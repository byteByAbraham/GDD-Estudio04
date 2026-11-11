# Sistemas del Juego

## Descripción de la sección

Los sistemas son conjuntos de reglas y componentes que trabajan juntos: combate, inventario, IA, diálogo, progresión, economía, misiones, etc.

## Inventario de sistemas

| Sistema | Propósito | Dependencias | Estado |
|---|---|---|---|
| S01 - Jugador, cámara y entradas | Moverse, observar y aceptar solo las acciones permitidas en cada situación | Colisiones, S09 | Implementado |
| S02 - Interacción e inventario | Usar objetos, leer documentos y guardar el equipo | S01, S08 | Implementado (falta la linterna en el inventario) |
| S03 - Progresión, accesos y checkpoints | Controlar objetivos, puertas, generadores, panel de código y puntos de guardado | S02, S09 | En integración (faltan la palanca y conectar el panel) |
| S04 - Ambiente nocturno y lluvia | Mantener la noche, la lluvia constante, la oscuridad interior y el audio ambiental | S05, S08 | Implementado (falta que la lluvia empiece desde el inicio) |
| S05 - Criatura: percepción, estados y captura | Crear una amenaza justa y coherente con el sigilo, sin combate | NavMesh, S01, S04, S06 | Implementado |
| S06 - Linterna y batería | Iluminar con un costo de batería y de riesgo | S01, S02, S05 | Implementado |
| S07 - Narrativa y diálogos | Contar la historia con la introducción, los documentos, los diálogos y la escena final | S02, S03, S08 | Pendiente (el sistema de diálogos existe; faltan las escenas) |
| S08 - Interfaz y señales | Comunicar acciones, estado y peligro con texto, imagen y sonido | S01 a S07 | Implementado |
| S09 - Gestión de partida, guardado y ajustes | Pausar, reintentar desde el checkpoint, guardar y cargar | S01 a S08 | Implementado |

## Estados globales del juego

Todos los sistemas consultan el estado global (`GameStateManager`) para saber qué acciones están permitidas.

| Estado | Cuándo ocurre | Movimiento | Criatura | Tiempo |
|---|---|---|---|---|
| Jugando | Exploración normal | Sí | Activa | Corre |
| Pausa | Esc o pérdida del foco de la ventana | No | Detenida | Detenido |
| Lectura | Documento, inventario, panel de código o diálogo abierto | No | Detenida | Detenido |
| Capturado | La criatura atrapa al jugador | No | Detenida | Pantalla de captura |
| Victoria | Termina la escena final | No | Detenida | Créditos |

### S01 - Jugador, cámara y entradas

| Campo | Contenido |
|---|---|
| Objetivo | Permitir explorar en primera persona y limitar las acciones según la situación del jugador. |
| Entradas | Movimiento (W A S D), mouse, Shift, C, E, F, Tab y Esc, leídos con el Input System (`PlayerInputActions`). |
| Salidas | Posición, orientación, postura, ruido de pasos y solicitudes de interacción. |
| Estados posibles | De pie, agachado, corriendo, escondido, bloqueado (pausa, lectura o captura). |
| Datos que necesita | Velocidades, alturas, sensibilidad del mouse, invertir eje Y y estado global. |
| Datos que genera | Posición y rotación para el guardado; eventos de ruido para S05. |
| Riesgos | Atravesar paredes o quedar atorado; recibir entradas con una pantalla abierta. |

**Reglas y parámetros**

| Regla | Valor |
|---|---|
| Velocidad caminando / corriendo / agachado | 2.5 / 4.5 / 1.2 m/s |
| Diagonal | Misma velocidad máxima que en línea recta |
| Correr | Solo de pie; agacharse lo termina |
| Altura de pie / agachado | 1.8 m / 1.1 m; no se levanta si hay un techo encima |
| Gravedad | −20 m/s² (Character Controller) |
| Salto | No existe |
| En un escondite | Solo giro de cámara, E para salir y Esc para pausa |
| Perder el foco de la ventana | Pausa el juego |

### S02 - Interacción e inventario

| Campo | Contenido |
|---|---|
| Objetivo | Permitir usar los objetos del escenario y guardar el equipo y los documentos obtenidos. |
| Entradas | E sobre un objeto a 2 m o menos; Tab para el inventario. |
| Salidas | Objeto guardado, documento leído, puerta o mecanismo actualizado y mensaje en pantalla. |
| Estados posibles | Sin objetivo, objeto apuntado, pantalla de lectura abierta, inventario abierto. |
| Datos que necesita | Identificador único de cada objeto, su tipo y sus requisitos (llave, fusible o energía). |
| Datos que genera | Banderas `pickup:<id>`, listas de llaves y documentos. |
| Riesgos | Registrar un objeto dos veces; que un objeto obligatorio quede inaccesible. |

**Objetos interactivos**

| Objeto | Acción con E | Dónde se guarda |
|---|---|---|
| Linterna | Equipo inicial | Inventario |
| Pila | Recoger (se usa al instante, +40 %) | No se guarda |
| Llave | Recoger | Inventario |
| Fusible | Recoger | Inventario |
| Nota, archivo o imagen | Leer | Documentos |
| Puerta | Abrir o cerrar; pide su llave si está cerrada | — |
| Escondite (armario, cama o casillero) | Entrar o salir | — |
| Caseta de generador | Colocar fusible y bajar la palanca | — |
| Panel de código | Abrir el teclado numérico | — |

**Reglas**

| Regla | Detalle |
|---|---|
| Detección del objeto | Raycast desde el centro de la cámara, 2 m, sin obstáculos |
| Aviso | Muestra el nombre y la acción: leer, recoger, abrir, colocar, activar o esconderse |
| Requisito faltante | Mensaje como «Está cerrada con llave» o «Falta un fusible», sin completar la acción |
| Duplicados | Cada objeto se registra una sola vez |
| Inventario | Pestañas Inventario y Documentos; Q / E cambian de pestaña y F examina |

### S03 - Progresión, accesos y checkpoints

| Campo | Contenido |
|---|---|
| Objetivo | Guiar al jugador por la secuencia de objetivos y recordar lo que ya desbloqueó. |
| Entradas | Llaves y fusibles usados, palancas bajadas, código correcto, zonas alcanzadas y diálogos terminados. |
| Salidas | Objetivo en pantalla actualizado, puertas desbloqueadas, energía restablecida y checkpoint guardado. |
| Estados posibles | Objetivo en curso, objetivo completado, zona bloqueada, zona desbloqueada. |
| Datos que necesita | Orden de objetivos, llave que abre cada puerta y código del panel. |
| Datos que genera | Banderas `door.unlocked:<id>`, `door.open:<id>`, generadores encendidos, objetivo actual. |
| Riesgos | Que el jugador quede sin poder avanzar o retroceda en la progresión tras una captura. |

**Secuencia de progresión**

| Paso | Objetivo en pantalla | Requisito | Dónde se obtiene | Checkpoint |
|---|---|---|---|---|
| 1 | Encuentra la forma de salir | Llave de la cabaña 1 | Dentro de la cabaña 1 | Inicio de partida |
| 2 | Encuentra la llave y entra a la segunda cabaña | Llave de la cabaña 2 | Perdida en el bosque | Al entrar a la cabaña 2 |
| 3 | Busca la forma de entrar a la tercera cabaña | Llave de la cabaña 3 y primer fusible | Dentro de la cabaña 2 | — |
| 4 | Explora la tercera cabaña | Segundo fusible y código de la pizarra | Dentro de la cabaña 3 | Al entrar a la cabaña 3 |
| 5 | Restablece la energía del laboratorio | Dos fusibles colocados y dos palancas bajadas | Casetas de generadores | Al encender los dos generadores |
| 6 | Abre la puerta del laboratorio | Código de 4 dígitos | Pizarra de la cabaña 3 | Al entrar al laboratorio |
| 7 | Descubre la verdad | Hablar con el Dr. Cooper y leer el archivo de Jereth | Laboratorio y oficina del Dr. Cooper | — |

La alucinación de la fogata ocurre en el trayecto entre la cabaña 2 y la cabaña 3, y no bloquea la progresión.

**Reglas**

| Regla | Detalle |
|---|---|
| Fusibles | Cualquiera de los dos funciona en cualquier caseta |
| Generador | E coloca el fusible y E baja la palanca; hace ruido a 8 m |
| Energía | Con los dos generadores encendidos, se activa el panel de código |
| Panel de código | 4 dígitos, sin límite de intentos |
| No retroceder | Las puertas desbloqueadas, los generadores y los objetivos completados no se pierden |
| Checkpoint | Guarda posición, batería, objetivo, banderas, llaves y documentos |

### S04 - Ambiente nocturno y lluvia

| Campo | Contenido |
|---|---|
| Objetivo | Mantener una atmósfera oscura y lluviosa que limite la percepción del jugador y de la criatura. |
| Entradas | Posición del jugador (interior o exterior) y ajustes de audio. |
| Salidas | Lluvia visual, sonido de lluvia, modificador de ruido y de visión para S05. |
| Estados posibles | Exterior bajo la lluvia, interior a cubierto. |
| Datos que necesita | Zonas de refugio (`WeatherShelterZone`) en cada cabaña y en el laboratorio. |
| Datos que genera | Indicador «bajo la lluvia» para el ruido y la visión de la criatura. |
| Riesgos | Que la oscuridad impida orientarse; caída de FPS por las partículas de lluvia. |

**Reglas**

| Regla | Detalle |
|---|---|
| Noche | Permanente durante toda la partida (skybox nocturno y posprocesado `VP_Mundo`) |
| Lluvia | Constante desde el inicio |
| Interior de las cabañas | Sin luz; la linterna es la única fuente para ver los objetos |
| Dentro de un refugio | El sonido de la lluvia se atenúa y deja de reducir el ruido del jugador |
| Efecto en el ruido | Con lluvia, los pasos se oyen a 3 / 8 / 1 m (caminar / correr / agachado) en lugar de 5 / 12 / 2 m |
| Efecto en la visión de la criatura | Con lluvia, su alcance baja de 10 m a 7 m |

### S05 - Criatura: percepción, estados y captura

| Campo | Contenido |
|---|---|
| Objetivo | Crear la única amenaza del juego: peligrosa, pero justa y evitable con sigilo. |
| Entradas | Posición y postura del jugador, ruidos, haz de la linterna, escondites y zonas protegidas. |
| Salidas | Estado de la criatura, desplazamiento, sonidos de respiración y captura. |
| Estados posibles | Patrulla, investigación, persecución, búsqueda y captura. |
| Datos que necesita | Puntos de patrulla, NavMesh, zona protegida de la cabaña 1. |
| Datos que genera | Evento de captura para S09; estado actual para el audio de S08. |
| Riesgos | Detección injusta a través de paredes; quedarse atorada en el NavMesh. |

**Percepción**

| Sentido | Alcance | Detalle |
|---|---|---|
| Vista | Cono de 70°, 10 m (7 m con lluvia) | La confirma tras 0.8 s de pie o 1.2 s agachado; las paredes la bloquean |
| Linterna | 8 m | Detecta el haz encendido |
| Oído | Radio del ruido | Pasos (5 / 12 / 2 m) y generador (8 m) |

**Estados**

| Estado | Comportamiento | Cambia a |
|---|---|---|
| Patrulla | Recorre puntos fijos y espera 2 s en cada uno | Investigación (ruido) o Persecución (ve al jugador o su linterna) |
| Investigación | Va al origen del ruido y espera 4 s | Persecución o Búsqueda |
| Persecución | Sigue al jugador por el NavMesh | Captura (a 3 m durante 0.6 s) o Búsqueda (lo pierde 3 s o se esconde) |
| Búsqueda | Revisa un radio de 3 m durante 6 s | Patrulla o Persecución |
| Captura | Termina el intento | Reaparición en el último checkpoint |

**Reglas**

| Regla | Detalle |
|---|---|
| Patrulla | Cerca de la cabaña 2, la cabaña 3, el laboratorio y una zona junto a la cabaña 1 |
| Zona protegida | Nunca entra a la cabaña 1 |
| Escondites | Entrar cancela la detección y la captura en curso; no revisa escondites |
| Diálogos y lectura | No puede capturar al jugador mientras hay una pantalla abierta |
| Aviso | Respiración distinta en patrulla, investigación y persecución |

### S06 - Linterna y batería

| Campo | Contenido |
|---|---|
| Objetivo | Dar visión en la oscuridad con un costo de batería y de riesgo. |
| Entradas | F, pilas recogidas y estado del escondite. |
| Salidas | Haz encendido o apagado, porcentaje de batería y señal de luz para S05. |
| Estados posibles | Encendida, apagada, sin batería, bloqueada (en un escondite). |
| Datos que necesita | Consumo, recarga y mínimo al reaparecer. |
| Datos que genera | Porcentaje de batería para el HUD y el guardado. |
| Riesgos | Que el jugador se quede sin luz sin poder avanzar. |

**Parámetros**

| Parámetro | Valor |
|---|---|
| Batería inicial | 100 % |
| Consumo encendida | 0.3 % por segundo (unos 5.5 min de luz continua) |
| Recarga por pila | +40 %, hasta 100 % |
| Pilas en el mapa | 4 |
| Batería mínima al reaparecer | 30 % |
| Sin batería | Mensaje «Sin batería» y luz ambiental mínima |
| En un escondite | Se apaga y no puede encenderse |
| Detección por la criatura | Haz encendido hasta 8 m |

### S07 - Narrativa y diálogos

| Campo | Contenido |
|---|---|
| Objetivo | Contar el pasado de Vadrik, Jereth y el Dr. Cooper durante la partida y cerrar la historia con la revelación final. |
| Entradas | Documentos leídos, llegada a la fogata, llegada al laboratorio y opciones elegidas. |
| Salidas | Pantallas de lectura, diálogos, escena final y créditos. |
| Estados posibles | Introducción, exploración, diálogo, escena final. |
| Datos que necesita | Textos de documentos, nodos de diálogo (quién habla, texto y opciones) y banderas. |
| Datos que genera | Banderas de diálogos terminados para que no se repitan. |
| Riesgos | Que el jugador no entienda el final si no leyó documentos; diálogos demasiado largos. |

**Momentos narrativos**

| Momento | Dónde | Qué ocurre | Tipo |
|---|---|---|---|
| Introducción | Inicio de la partida | Explica cómo Vadrik, desesperado por la enfermedad de Jereth, llegó con el Dr. Cooper | Texto en pantalla |
| Documentos | Bosque, cabañas y laboratorio | Notas, archivos e imágenes revelan quién es en realidad el Dr. Cooper y sus experimentos | Lectura opcional |
| Alucinación | Fogata, entre las cabañas 2 y 3 | Vadrik cree ver a Jereth y habla con él; es una alucinación, no una comunicación real | Diálogo por opciones |
| Dr. Cooper | Laboratorio | Cooper, herido, le dice que Jereth está encerrado; antes de morir confiesa que nunca hubo cura | Diálogo por opciones |
| Revelación | Oficina del Dr. Cooper | Vadrik lee el archivo de Jereth y descubre que la criatura es su hijo | Lectura |
| Final | Oficina del Dr. Cooper | La criatura aparece detrás de Vadrik (jumpscare) | Escena y créditos |

**Reglas**

| Regla | Detalle |
|---|---|
| Opciones | De 2 a 3 por respuesta; cambian la réplica, no la historia ni el final |
| Repetición | Cada diálogo ocurre una sola vez |
| Documentos | Opcionales, pero el archivo de Jereth es obligatorio para terminar |

### S08 - Interfaz y señales

| Campo | Contenido |
|---|---|
| Objetivo | Comunicar con claridad qué puede hacer el jugador, qué tiene y cuándo está en peligro. |
| Entradas | Eventos de S01 a S07. |
| Salidas | Elementos del HUD, mensajes, pantallas y sonidos. |
| Datos que necesita | Textos, íconos, tamaño de texto, subtítulos y volúmenes. |
| Riesgos | Saturar la pantalla; señales que delaten demasiado la ubicación de los objetos. |

**Señales**

| Señal | Tipo | Cuándo |
|---|---|---|
| Objetivo actual | Texto en el HUD | Siempre visible; cambia al completar un paso |
| Batería | Barra en el HUD | Siempre visible; aviso cuando está baja |
| Aviso de interacción | Texto al centro | Al apuntar un objeto a 2 m o menos |
| Mensajes | Texto temporal | Requisito faltante, checkpoint guardado, código correcto o incorrecto |
| Respiración de la criatura | Sonido | Según su estado y distancia |
| Efecto de miedo | Viñeta en pantalla | Cuando la criatura está cerca o persigue |
| Subtítulos | Texto | Diálogos y sonidos importantes (se pueden desactivar) |

### S09 - Gestión de partida, guardado y ajustes

| Campo | Contenido |
|---|---|
| Objetivo | Permitir pausar, reintentar, guardar, continuar y configurar el juego. |
| Entradas | Esc, botones de los menús, checkpoints y captura. |
| Salidas | Cambios de estado global, partida guardada o cargada y ajustes aplicados. |
| Datos que necesita | Último checkpoint, archivo de guardado y preferencias. |
| Datos que genera | `darkmutant_save.json` (con respaldo `.bak`) y preferencias en PlayerPrefs. |
| Riesgos | Guardado dañado; reaparecer en un lugar inseguro. |

**Reglas**

| Regla | Detalle |
|---|---|
| Guardado automático | En cada checkpoint |
| Guardado manual | Desde el menú de pausa, en la posición actual |
| Captura | Reaparece en el último checkpoint con al menos 30 % de batería |
| Nueva partida | Borra la partida guardada; conserva los ajustes |
| Continuar | Carga la partida guardada desde el menú principal |
| Ajustes | Volumen general, de ambiente y de voces; sensibilidad; invertir eje Y; subtítulos; tamaño de texto; efectos reducidos; modo de pantalla; calidad; VSync |
| Detalle técnico | Ver [[04 - Datos y Persistencia]] |

## Relaciones entre sistemas

| Origen | Destino | Información intercambiada |
|---|---|---|
| S01 - Jugador | S02 - Interacción | Dirección de la cámara y solicitud de E |
| S01 - Jugador | S05 - Criatura | Posición, postura y ruido de pasos |
| S01 - Jugador | S06 - Linterna | Pulsación de F y estado del escondite |
| S02 - Interacción | S03 - Progresión | Llaves, fusibles y documentos obtenidos |
| S03 - Progresión | S07 - Narrativa | Llegada a la fogata y al laboratorio |
| S04 - Ambiente | S05 - Criatura | Modificadores de visión y ruido por la lluvia |
| S06 - Linterna | S05 - Criatura | Haz encendido |
| S05 - Criatura | S09 - Partida | Captura confirmada |
| S03 - Progresión | S09 - Partida | Checkpoint alcanzado y progreso a guardar |
| S01 a S07 | S08 - Interfaz | Estados y eventos para mensajes, HUD y sonidos |
| S09 - Partida | S01 a S08 | Pausa, restauración del checkpoint y  |

> **Navegación:** [[00 - Índice]] · ← [[02 - Mecánicas]] · [[04 - Controles]] →