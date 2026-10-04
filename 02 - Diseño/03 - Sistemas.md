# Sistemas del Juego

## Descripción de la sección

Los sistemas son conjuntos de reglas y componentes que trabajan juntos: combate, inventario, IA, diálogo, progresión, economía, misiones, etc.

## Inventario de sistemas

| Sistema | Propósito | Dependencias | Estado |
|---|---|---|---|
| S01 - Jugador, cámara y entradas | Moverse, observar y aceptar solo acciones compatibles | Colisiones del escenario, estados de partida, configuración de entradas | Propuesto|
| S02 - Interacción, inventario y diario | Registrar pistas y utilizar objetos clave | S01, identificadores de contenido, S07 | Propuesto|
| S03 - Acertijos y progreso | Gestionar objetivos y condiciones de avance de la investigación | S02, eventos de objetivos, S04, S08 | Propuesto|
| S04 - Fases nocturnas y lluvia | Modificar el ambiente según el progreso | S03, iluminación y clima, S05, S07 | Propuesto|
| S05 - Criatura, percepción y captura | Crear amenazas coherentes con sigilo y defensa | Navegación del escenario, S01, S04, eventos de S06 | Propuesto|
| S06 - Linterna y defensa | Iluminar, aplicar luz intensa y golpear | S01, visibilidad y colisiones, S05, S07 | Propuesto|
| S07 - Interfaz, audio y señales narrativas | Comunicar acciones y sostener la tensión | Estados publicados por S01 a S06, contenido narrativo | Propuesto|
| S08 - Gestión de partida y ajustes | Pausar, reintentar y gestionar el guardado que se defina | Estado estable de S01 a S07, archivos locales | Propuesto|

### S01 - Jugador, cámara y entradas

**Objetivo:**  

Permitir explorar en primera persona y controlar qué acciones están disponibles según la situación del jugador.

**Entradas:**  

Dirección de movimiento, movimiento del mouse, carrera, postura, interacción, controles de linterna, apertura de paneles y pausa.

**Procesamiento / reglas:**

- El movimiento se calcula respecto a la orientación horizontal de la cámara. Velocidades iniciales: caminar 2.5 m/s, correr 4.5 m/s y agachado 1.2 m/s.

- La dirección diagonal se normaliza y las colisiones impiden atravesar geometría. El recorrido se construye sin exigir saltos.

- La cámara permite moverse de manera horizontal y vertical, la sensibilidad se ajusta desde opciones.

- Las acciones de desplazamiento y postura se combinan con la exploración, la carrera requiere estar de pie.

- La luz intensa obliga a caminar. El golpe cancela carrera y luz intensa y bloquea **[E]**, **[F]**, **[Ctrl]** y **[Tab]** durante su recuperación. El movimiento a velocidad de caminar y la cámara siguen disponibles durante el golpe.

- Dentro de un escondite solo se admite cámara limitada, **[E]** para salir y **[Esc]** para pausa.

- Una pantalla contextual desactiva entradas del mundo y libera el cursor. La captura desactiva todas las acciones salvo las opciones de reinicio o menú al terminar su presentación.

- **[Esc]** puede pausar durante una acción, al volver se conserva su tiempo restante, pero no se reanuda automáticamente la luz intensa.

- Perder el foco de la ventana pausa la simulación y libera las entradas mantenidas para evitar desplazamientos involuntarios.

**Salidas:**  

Posición, orientación, postura, velocidad, señales de pasos y solicitudes de acciones válidas.

**Estados posibles:**  

Exploración de pie, exploración agachado, carrera, luz intensa, golpe, escondido, pantalla contextual, pausa y capturado. Postura y posición se mantienen como datos separados de la acción activa.

**Dependencias:**  

Colisiones y posiciones transitables, estados globales de S08, controles y opciones de S07.

**Interacciones:**  

S02 recibe interacción, S05 recibe posición y ruido, S06 recibe defensa, S07 representa mensajes y ajustes, S08 bloquea acciones al pausar o restaurar.

**Datos que necesita:**  

Velocidades, alturas de postura, sensibilidad, límites de cámara, asignaciones fijas de entradas y posiciones de entrada/salida de escondites.

**Datos que genera:**  

Transformación del jugador, postura, acción activa y eventos de movimiento.

**Riesgos:**  

Entradas simultáneas que activen dos acciones incompatibles, colisiones defectuosas, cámara que atraviese paredes, obstáculos que impidan completar el recorrido.

**Criterios de aceptación:**

- Desplazarse en diagonal no supera la velocidad configurada.

- Mantener carrera mientras se usa luz intensa produce movimiento a velocidad de caminar.

- Una pared bloquea el desplazamiento y ponerse de pie bajo un techo bajo conserva la postura agachada.

- Abrir un panel o pausar detiene movimiento, criatura y temporizadores del mundo.

- Salir de un escondite utiliza su punto de salida y recupera la postura de entrada.

- Perder el foco y volver a la ventana no produce movimiento ni defensa sin entrada del usuario.

### S02 - Interacción, inventario y diario

**Objetivo:**  

Permitir encontrar y conservar pistas, manipular puertas y utilizar objetos necesarios para la investigación.

**Entradas:**  

Objeto señalado por la cámara, solicitud **[E]**, selección en el diario y eventos de restauración.

**Procesamiento / reglas:**

- Se selecciona el primer interactivo alcanzado por el centro de la cámara a un máximo de 2 metros, respetando obstáculos.

- Cada interactivo contiene un identificador, tipo, mensaje contextual, requisitos y resultado. Los requisitos se comprueban al pulsar **[E]**, no solo al mostrar el mensaje.

- La linterna está disponible desde el inicio, separada de los objetos de investigación.

- No se duplica un objeto ya recogido. Los objetos clave no se pueden descartar, su capacidad basta para el contenido del episodio.

- Los documentos pueden releerse. Su contenido debe ser legible a 1920 × 1080.

- Abrir lectura, diario o panel de acertijo solicita una pantalla contextual a S08, que pausa el mundo. Solo hay una pantalla contextual abierta.

**Salidas:**  

Objetos registrados, documentos disponibles, acciones de puerta, eventos de pista obtenida y mensajes de requisito incumplido.

**Estados posibles:**  

Sin objetivo, objetivo interactivo válido, requisito pendiente, lectura, diario, objeto recogido, objeto instalado.

**Dependencias:**  

S01 para seleccionar y activar, catálogo local de elementos, S07 para presentación, S08 para pausa y restauración.

**Interacciones:**  

S03 recibe objetos y eventos de progreso. S07 muestra información. S08 utiliza los registros de objetos e interactivos para reiniciar o recuperar el estado de partida según el método que se defina.

**Datos que necesita:**  

Identificadores únicos, nombres, tipos, textos, imágenes, requisitos, posiciones y estado inicial de cada elemento.

**Datos que genera:**  

Conjuntos de elementos recogidos, documentos conocidos, piezas instaladas y puertas abiertas.

**Riesgos:**  

Duplicación de objetos, ausencia de un objeto obligatorio, pistas ilegibles, información registrada que no corresponda al mundo restaurado.

**Criterios de aceptación:**

- E no alcanza elementos tras una pared ni fuera de los 2 metros.

- Recoger dos veces el mismo identificador no duplica el inventario ni el diario.

- Cada requisito incumplido produce un mensaje comprensible.

- Al restaurar la partida, la presencia de objetos y documentos coincide con el estado recuperado.

### S03 - Acertijos y progreso

**Objetivo:**

Gestionar los objetivos y las condiciones de avance de la investigación, incluidos los acertijos que se diseñen para el juego.

**Entradas:**

Interacciones completadas, información descubierta, objetos utilizados cuando corresponda, resultados de acertijos, eventos narrativos y estado recuperado de partida.

**Procesamiento / reglas:**

- Cada objetivo y acertijo tendrá requisitos, acciones válidas y resultados definidos cuando se desarrolle su contenido.
- El sistema comprueba esos requisitos antes de marcar un objetivo o acertijo como completado.
- Completar una interacción puede actualizar el objetivo, habilitar un elemento o permitir acceso a una zona, según el diseño de cada caso.
- El contenido de pistas, nombres de objetos, soluciones y ubicaciones no se establece en esta ficha.
- Si un acertijo se resuelve directamente en el escenario, utiliza las entradas de exploración correspondientes. Si emplea un panel contextual, utiliza las entradas de interfaz y pausa la simulación.
- Una acción incorrecta no marca el acertijo como resuelto. Su retroalimentación y posibles consecuencias se definirán para cada acertijo.
- Los eventos de progreso se registran para impedir que una interacción repetida duplique recompensas o vuelva a ejecutar una transición ya realizada.
- Se propone vincular el paso de noche a noche con lluvia a un evento de avance de la investigación. El evento concreto y su ubicación quedan pendientes de definición.
- Esperar o permanecer escondido no completa un objetivo de investigación por sí solo.

**Salidas:**

Objetivos actualizados, interacciones o acertijos completados, cambios habilitados en el entorno y eventos de avance para otros sistemas.

**Estados posibles:**

Objetivo pendiente, objetivo en progreso, requisito cumplido, interacción o acertijo resuelto y objetivo completado.

**Dependencias:**

S02 para información, objetos e interacciones; S04 para la transición de clima; S07 para comunicar objetivos; S08 para reiniciar o recuperar el estado de partida.

**Interacciones:**

Recibe resultados de S02, comunica avances a S07 y solicita a S04 el cambio de fase cuando se cumpla el evento definido. S08 aplica el estado de progreso correspondiente al reiniciar o continuar.

**Datos que necesita:**

Definición de objetivos, requisitos, acciones válidas, condiciones de resolución, consecuencias, mensajes y eventos asociados. Los identificadores definitivos se asignarán al crear el contenido.

**Datos que genera:**

Estado de objetivos, requisitos cumplidos, interacciones completadas, acertijos resueltos y eventos de progreso ejecutados.

**Riesgos:**

Requisitos imposibles de cumplir, falta de información para resolver un acertijo, eventos duplicados y diferencias entre el progreso registrado y el estado del entorno.

**Criterios de aceptación:**

- Un objetivo solo se completa al cumplir sus requisitos definidos.
- La información necesaria para resolver un acertijo está disponible dentro del juego.
- Una acción incorrecta no registra una resolución válida.
- Repetir una interacción completada no duplica sus efectos.
- El mensaje del objetivo coincide con el progreso actual.
- El cambio a lluvia responde al evento de investigación configurado, sin depender de un acertijo o una ubicación todavía no definidos.

### S04 - Fases nocturnas y lluvia

**Objetivo:**  

Cambiar las condiciones de percepción y el ambiente del recorrido sin añadir un ciclo horario completo.

**Entradas:**  

Evento de avance de la investigación definido en S03, fase actual o recuperada, pausa, configuración de efectos y volumen.

**Procesamiento / reglas:**

- Fases: noche sin lluvia y noche con lluvia. La primera permite aprender la ruta y reconocer señales, la segunda dificulta orientación y escucha.

- El efecto visual y sonoro aumenta gradualmente. La criatura conserva posición y estado, no se teletransporta ni se reinicia por el clima.

- La lluvia reduce la visibilidad del bosque y enmascara sonidos. S05 aplica menores alcances de visión y oído en exteriores, dentro de edificios conserva los valores de la fase sin lluvia.

- Se identifica si emisor y receptor están en exteriores para aplicar la reducción sonora. Si alguno está en un interior, se utilizan los valores sin reducción.

- Los interiores mantienen el sonido de lluvia atenuado.

- La lluvia no modifica acertijos, reserva de linterna, velocidad del jugador ni transitabilidad del escenario.

- La fase no se revierte durante el episodio. Si se recupera una partida en fase de lluvia, se aplica el clima de ese estado sin repetir un evento de transición ya completado.

- Se limita la densidad y distancia de partículas. La opción de efectos reducidos conserva la información del clima y disminuye partículas y destellos.

**Salidas:**  

Fase actual, valores de ambiente, intensidad de lluvia y modificadores de percepción exterior.

**Estados posibles:**  

Noche sin lluvia, transición visual a lluvia, noche con lluvia estable. La transición visual pertenece a la fase de lluvia a efectos de progreso y guardado.

**Dependencias:**  

S03 para el evento, iluminación, audio y regiones interiores/exteriores, S08 para restauración.

**Interacciones:**  

S05 utiliza los modificadores de percepción, S07 reproduce ambiente y señales, S08 restablece la fase correspondiente al estado de partida y pausa el avance de los efectos.

**Datos que necesita:**  

Perfiles de iluminación y sonido, intensidad máxima de lluvia, duración de transición, regiones del escenario, calidad de efectos.

**Datos que genera:**  

Fase y valores de ambiente activos.

**Riesgos:**  

Pérdida de rendimiento por partículas, interiores mojados visualmente, sonidos esenciales completamente ocultos, recorrido demasiado oscuro.

**Criterios de aceptación:**

- La lluvia comienza una sola vez cuando se cumple el evento de investigación definido.

- La transición es gradual, utiliza la duración configurada y se detiene al pausar.

- La criatura conserva posición y persecución al cambiar el clima, salvo que pierda contacto por las reglas de percepción.

- El perfil exterior reduce los sentidos de S05 y el interior mantiene sus valores base.

- Se mide el objetivo de 60 FPS en el equipo de referencia que acuerde el equipo, se ajusta la densidad de lluvia si el objetivo no se alcanza.

### S05 - Criatura, percepción y captura

**Objetivo:**  

Producir una amenaza que patrulle, reaccione a señales y permita escapar mediante reglas comprensibles.

**Entradas:**  

Posición visible del jugador, ruidos, haz de linterna, escondite observado, interrupciones de S06, fase del clima, regiones protegidas.

**Procesamiento / reglas:**

- La criatura utiliza rutas transitables y puntos de patrulla definidos. El primer encuentro se sitúa fuera del refugio inicial.

- Solo persigue una posición confirmada visualmente. Los ruidos producen investigación de su punto de origen, sin revelar una ubicación posterior.

- La luz de la linterna puede atraer su atención cuando perciba el haz; esa señal permite investigar su origen y no revela automáticamente la posición posterior del jugador.

- La cobertura sólida bloquea visión y ataques. La exposición visual vuelve a cero al romperse la línea de visión.

- Radios iniciales de ruido exterior sin lluvia/con lluvia: caminar 5/3 metros, correr 12/8, agachado 2/1 y golpe 10/6. Un golpe fallido también produce ruido. La visión continúa requiriendo un recorrido despejado.

- Los avisos se limitan a uno por segundo para evitar reiniciar continuamente la misma reacción.

- Velocidades propuestas: patrulla 1.5 m/s y persecución 4 m/s. El jugador puede crear distancia corriendo, a cambio de producir ruido.

- Al perder visión durante 2 segundos, se dirige a la última posición confirmada. Al alcanzarla, busca durante 8 segundos y luego retoma patrulla si no recibe nuevas señales.

- A 1.2 metros del jugador y con línea de ataque despejada inicia una preparación visible de 0.6 segundos. La captura se aplica al terminar únicamente si sigue en alcance y no fue interrumpida.

- Una interrupción cancela la preparación de ataque. La criatura conserva la última información observada y vuelve a actuar al terminar el efecto, necesita contacto visible para actualizar la posición del jugador.

- La resistencia de 5 segundos comienza al terminar cualquier interrupción. Durante ella no puede recibir otra interrupción de luz o golpe.

- La cabaña inicial funciona como espacio protegido y bloquea navegación y ataques de la criatura. Si el jugador entra, esta investiga la última posición exterior y luego sigue las reglas de búsqueda.

**Salidas:**  

Desplazamiento, orientación, animación, señales de presencia, persecución y captura.

**Estados posibles:**  

Patrulla, investigar señal, persecución, búsqueda, comprobar escondite, preparar ataque, interrumpida, capturar. La resistencia es un temporizador independiente, no una nueva persecución.

**Dependencias:**  

Rutas y colisiones del escenario, S01 para posición y postura, S04 para percepción, S06 para interrupciones, S08 para pausa y reinicio.

**Interacciones:**  

S07 reproduce pasos, reacciones y aviso de ataque. S08 recibe captura y ofrece reinicio. S06 consulta visibilidad, alcance y resistencia.

**Datos que necesita:**  

Puntos de patrulla, posiciones investigadas, visión, tiempos y radios de ruido, entradas de escondite, regiones protegidas, velocidad, posición inicial definida para el estado de partida que se restablezca.

**Datos que genera:**  

Estado actual, última posición conocida, progreso de confirmación visual y temporizadores de búsqueda, interrupción y resistencia.

**Riesgos:**  

Percepción a través de paredes, persecución sin información observable, atascos de navegación, ataques sin aviso, interrupciones infinitas por alternar luz y golpe.

**Criterios de aceptación:**

- No detecta visualmente ni captura al jugador detrás de una pared sólida.

- Agacharse en campo visual no garantiza invisibilidad.

- Perder contacto antes de esconderse no informa mágicamente la nueva ubicación.

- La criatura no entra ni ataca dentro de los espacios protegidos.

- Un golpe o una exposición válida cancelan la preparación de captura si la criatura no está resistiendo.

- Alternar luz y golpe durante resistencia no permite encadenar interrupciones.

- En pausa no avanzan movimiento, percepción ni ataque.

### S06 - Linterna y defensa

**Objetivo:**  

Concentrar iluminación y defensa en una herramienta que siempre esté disponible, con límites sobre su capacidad de detener a la criatura.

**Entradas:**  

**[F]**, **[clic derecho]** mantenido, **[clic izquierdo]** pulsado, dirección de cámara, estado del jugador, visibilidad y resistencia de la criatura.

**Procesamiento / reglas:**

| Parámetro propuesto | Valor inicial |
|---|---|
| Reserva máxima / inicial | 100 unidades |
| Consumo de luz intensa | 25 unidades por segundo |
| Espera para recuperar reserva | 3 segundos desde el último uso de luz intensa |
| Recuperación | 20 unidades por segundo, hasta 100 |
| Alcance de defensa luminosa | 8 metros |
| Cono de defensa luminosa | 15° de apertura total, centrado en la cámara |
| Exposición continua necesaria | 1.2 segundos |
| Interrupción por luz | 2 segundos |
| Alcance de golpe | 1.5 metros |
| Preparación del golpe | 0.2 segundos |
| Recuperación del golpe | 1.5 segundos desde su inicio |
| Interrupción por golpe | 1 segundo |
| Retroceso máximo | 0.5 metros, limitado por geometría |
| Resistencia compartida | 5 segundos después de terminar la interrupción |

- La luz normal no consume reserva y no interrumpe. La reserva solo limita la acción de luz intensa.

- La luz intensa exige exposición sobre la parte superior del cuerpo o la cabeza, sin obstáculos. Romper el contacto, agotar la reserva o encontrar resistencia elimina la exposición acumulada.

- Si se inicia con **[F]** apagada, se ilumina durante el uso y se restaura el estado anterior al soltar. Agotar la reserva deja encendida la luz normal para conservar visibilidad.

- Agotar la reserva exige una nueva pulsación de botón derecho, recuperar reserva no reactiva el haz por mantenerlo pulsado.

- La recuperación continúa al explorar, golpear o esconderse, siempre que hayan transcurrido 3 segundos sin luz intensa. En pausa o captura no avanza.

- Un golpe se aplica una sola vez al objetivo frontal más cercano dentro del alcance y sin obstáculos, al terminar su preparación. Pulsaciones durante recuperación se descartan y no se acumulan.

- El golpe cancela la luz intensa y no consume reserva. La criatura recibe interrupción solo si no está resistiendo.

- El retroceso se limita al espacio libre. La interrupción sigue aplicándose aunque no sea posible desplazarla.

- Una defensa válida se resuelve antes de una captura coincidente. Fuera de esas condiciones, la captura continúa según S05.

- Esconderse apaga la iluminación y bloquea defensa. Pausar corta la exposición de luz intensa, conserva la reserva y congela los tiempos restantes del golpe.

**Salidas:**  

Haz normal o intenso, reserva, evento de golpe, solicitud de interrupción y retroalimentación de impacto o resistencia.

**Estados posibles:**  

Luz normal apagada/encendida, luz intensa, reserva agotada, golpe en preparación/recuperación, defensa bloqueada por estado del jugador.

**Dependencias:**  

S01 para entradas compatibles, geometría y dirección de cámara, S05 para aplicar efectos, S07 para representación.

**Interacciones:**  

S05 recibe avisos de luz, ruido y defensa. S07 muestra la reserva y las reacciones. S08 establece el estado de la herramienta de acuerdo con las reglas de reinicio o recuperación de partida que se definan.

**Datos que necesita:**  

Parámetros de la tabla, estado anterior de iluminación, objetivo visible, estado de resistencia y bloqueo de entradas.

**Datos que genera:**  

Reserva restante, tiempo de recuperación, exposición acumulada y tiempos de golpe.

**Riesgos:**  

Luz que atraviese obstáculos, golpe que impacte varias veces, recuperación que se active dentro de pausa, balance que vuelva inútil la herramienta o elimine el miedo.

**Criterios de aceptación:**

- Sin usar defensa, la iluminación normal sigue disponible durante toda la partida.

- Cuatro segundos continuos de luz intensa agotan 100 unidades desde reserva completa.

- Tras 3 segundos sin luz intensa, la reserva recupera 20 unidades por segundo sin superar 100.

- Una exposición válida de 1.2 segundos provoca una interrupción de 2 segundos, interrumpir el haz antes impide ese resultado.

- Cada golpe tiene un único impacto y no se repite por mantener el botón pulsado.

- Luz y golpe respetan los mismos 5 segundos de resistencia.

- Una defensa no afecta a la criatura detrás de una pared.

- Agotar la reserva no deja al jugador sin iluminación normal ni reactiva defensa sin nueva pulsación.

### S07 - Interfaz, audio y señales narrativas

**Objetivo:**  

Comunicar acciones, progreso y amenazas mientras mantiene la incertidumbre sobre la voz del hijo.

**Entradas:**  

Objetivo actual, interactivo seleccionado, reserva de linterna, estados observables de la criatura, eventos narrativos, clima, configuración.

**Procesamiento / reglas:**

- La interfaz de exploración muestra un punto central discreto, mensaje contextual cuando corresponde, objetivo breve y reserva defensiva al usar luz intensa o mientras se recupera.

- La interfaz no muestra la posición de una criatura fuera de la vista ni un indicador que confirme si una voz pertenece al hijo o a la criatura.

- Pasos, sonidos de persecución, gesto de resistencia y preparación de ataque comunican amenazas próximas. La captura siempre tiene la preparación definida por S05.

- Los documentos y paneles usan texto legible, contraste suficiente y navegación con mouse. Los cambios importantes incluyen texto o símbolo y no dependen solo del color.

- Opciones iniciales: sensibilidad, invertir eje vertical, volumen general/ambiente/voces, subtítulos, tamaño de texto y efectos reducidos. Las asignaciones de teclas y botones son fijas, según Controles.

**Salidas:**  

Mensajes, paneles, objetivo, indicador de reserva, subtítulos, sonidos y opciones aplicadas.

**Estados posibles:**  

Exploración, interacción disponible, lectura/diario/acertijo, pausa, captura, cierre del episodio, opciones.

**Dependencias:**  

Estados de S01 a S06, contenido local aprobado por narrativa y arte, administración de pantallas de S08.

**Interacciones:**  

Muestra requisitos de S02, progreso de S03, ambiente de S04 y señales de S05/S06. Envía ajustes a S01, S04 y S08.

**Datos que necesita:**  

Textos, iconos, subtítulos, sonidos, identificadores de eventos, condiciones de activación y opciones del usuario.

**Datos que genera:**  

Eventos narrativos reproducidos, selección de panel y ajustes modificados.

**Riesgos:**  

Textos difíciles de leer, demasiados indicadores que anticipen el peligro, voces repetidas, sonidos esenciales tapados por lluvia, eventos que revelen prematuramente el misterio.

**Criterios de aceptación:**

- El mensaje contextual coincide con la acción que **[E]** puede ejecutar.

- Documentos, objetivos y paneles se leen a la resolución objetivo sin recortes.

- La lluvia permite oír la preparación de ataque cuando la criatura está a distancia de captura.

- Un evento narrativo no se repite continuamente al cruzar su zona, si se recupera una partida, se respetan los eventos registrados en su estado.

- Cambiar sensibilidad o volumen aplica el resultado sin reiniciar la partida.

### S08 - Gestión de partida y ajustes

**Objetivo:**

Administrar los menús, la pausa, el reinicio tras captura y la persistencia local de los ajustes. Gestionar el guardado de progreso según el método que defina el equipo.

**Entradas:**

Nueva partida, pausa, captura, solicitud de reintento, retorno al menú, cambios de ajustes y solicitud de guardar o continuar cuando esas funciones estén habilitadas.

**Procesamiento / reglas:**

- El método de guardado y reinicio de progreso está pendiente de definición. Esta ficha no establece ubicaciones, cantidad de guardados ni eventos concretos que los generen.
- Nueva partida utiliza los estados iniciales establecidos para jugador, entorno, investigación y criatura.
- Pausa, lectura, diario y paneles contextuales congelan la simulación, los tiempos de IA, defensa y clima. La interfaz continúa respondiendo.
- Tras una captura se ofrecen «Reintentar» y «Menú principal». Reintentar utiliza el estado de partida establecido por las reglas de reinicio que se definan.
- Al reiniciar o recuperar una partida, jugador, objetos, documentos, mecanismos, clima y progreso deben corresponder al mismo estado, sin datos parciales de una partida anterior.
- El jugador no vuelve al mundo dentro de una pared ni bajo un ataque inevitable causado por una posición de reinicio inválida.
- Los ajustes de sensibilidad, audio y presentación se almacenan localmente y por separado del progreso. Las asignaciones de controles permanecen fijas.
- Si se incorpora guardado de progreso, su formato debe conservar los datos necesarios para recuperar un estado coherente y manejar errores de archivo.
- «Continuar» solo estará disponible cuando exista una función de guardado y un estado válido recuperable. La interfaz debe comunicar qué progreso se conserva al salir, de acuerdo con el método elegido.
- Todas las funciones previstas se ejecutan sin conexión a Internet.

**Salidas:**

Estado global de partida, pausa o reinicio; ajustes persistentes; datos de progreso recuperables cuando se implemente su guardado; mensajes de menú o error.

**Estados posibles:**

Menú principal, jugando, pantalla contextual, pausa, capturado, reiniciando y recuperando partida cuando exista un guardado válido.

**Dependencias:**

Estados de S01 a S07, configuración inicial del juego, acceso a archivos locales para ajustes y método de guardado de progreso cuando se defina.

**Interacciones:**

Congela o restablece los otros sistemas. S07 presenta menús y mensajes. S03 proporciona el progreso y recibe el estado correspondiente al reinicio o recuperación.

**Datos que necesita:**

Estados iniciales del juego, reglas de pausa y reinicio, ajustes del usuario y datos de progreso requeridos por el método de guardado que se elija.

**Datos que genera:**

Estado global de partida, ajustes locales y datos persistentes de progreso cuando esa función esté habilitada.

**Riesgos:**

Reinicio con estados contradictorios, ubicación inválida del jugador, entradas mantenidas que se reanuden automáticamente y archivos de ajustes o progreso inválidos.

**Criterios de aceptación:**

- Pausar detiene la simulación y permite utilizar el menú.
- Tras una captura, «Reintentar» y «Menú principal» producen sus acciones correspondientes.
- Reiniciar establece de forma coherente el estado del jugador, criatura, entorno e investigación.
- Cerrar una pantalla no activa por accidente un golpe o una interacción.
- Los ajustes persisten después de cerrar y abrir el juego, sin permitir reasignar controles.
- Si se implementa guardado de progreso, se puede guardar y continuar sin conexión; un archivo inválido muestra un mensaje y no bloquea el menú.

## Relaciones entre sistemas

| Origen | Destino | Información intercambiada |
|---|---|---|
| S01 - Jugador | S02 - Interacción | Dirección de cámara, distancia y solicitud **[E]** |
| S01 - Jugador | S05 - Criatura | Posición visible, postura y avisos de pasos |
| S01 - Jugador | S06 - Linterna | Dirección, entradas de defensa y estado que permite actuar |
| S02 - Interacción | S03 - Progreso | Información descubierta, objetos utilizados e interacciones completadas |
| S03 - Progreso | S04 - Clima | Evento de avance de investigación definido para activar lluvia |
| S04 - Clima | S05 - Criatura | Fase y modificadores de percepción en exteriores |
| S06 - Linterna | S05 - Criatura | Avisos del haz, ruido de golpe e interrupciones válidas |
| S05 - Criatura | S08 - Partida | Captura confirmada |
| S03 - Progreso | S08 - Partida | Estado de objetivos e interacciones para reinicio o recuperación |
| S01 a S06 | S07 - Interfaz/audio | Estados y eventos necesarios para mensajes, sonidos y subtítulos |
| S08 - Partida | S01 a S07 | Pausa, restauración, progreso y ajustes persistentes |

> **Navegación:** [[00 - Índice]] · ← [[02 - Mecánicas]] · [[04 - Controles]] →
