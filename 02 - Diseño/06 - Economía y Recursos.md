# Economía y Recursos

## Descripción de la sección

Documenta cualquier recurso cuantificable: dinero, vida, energía, munición, experiencia, materiales, tiempo, puntos, etc.

Dark Mutant no tiene dinero, puntos, experiencia, munición ni tienda. Su economía se basa en un recurso que se gasta (la **batería**) y en objetos de progreso que se encuentran una sola vez (**llaves, fusibles y documentos**).

## Recursos

| Recurso | Obtención | Uso | Límite | Pérdida |
|---|---|---|---|---|
| Batería de la linterna | Comienza al 100 % y se recarga con pilas | Mantener encendida la linterna | 100 % | 0.3 % por segundo mientras la linterna está encendida |
| Pila | 4 repartidas por el mapa; se recogen con **E** | Recupera 40 % de batería, sin superar el 100 % | 4 en toda la partida; no se guardan | Se usa al recogerla; si la batería está llena, el sobrante se pierde |
| Linterna | Equipo inicial de Vadrik; aparece en el inventario | Iluminar el bosque y el interior oscuro de las cabañas | 1 | No se pierde; deja de iluminar sin batería |
| Llaves | 3: la de la cabaña 1 (en su interior), la de la cabaña 2 (perdida en el bosque) y la de la cabaña 3 (dentro de la cabaña 2) | Abrir la puerta de su cabaña | 1 por cabaña | No se pierden; se conservan en el inventario |
| Fusibles | 2: uno en la cabaña 2 y otro en la cabaña 3 | Colocarlos en las casetas de generadores | 2 | Se quedan en la caseta al colocarlos |
| Código de la puerta | Escrito en una pizarra de la cabaña 3 | Abrir el panel de la puerta del laboratorio | 1 código de 4 dígitos | No se pierde; el jugador puede volver a verlo |
| Documentos (notas, archivos e imágenes) | Repartidos en el bosque, las cabañas y el laboratorio; se leen con **E** | Contar la historia y revelar quién es en realidad el Dr. Cooper | Cantidad fija | No se consumen; se guardan en la pestaña Documentos |

## Fuentes y sumideros

| Recurso | Fuente (de dónde sale) | Sumidero (en qué se gasta) |
|---|---|---|
| Batería | 100 % inicial, 4 pilas (+40 % cada una) y mínimo de 30 % al reaparecer en un checkpoint | Linterna encendida (0.3 % por segundo); sobrante de una pila con batería llena |
| Llaves | Exploración del bosque y de las cabañas | Ninguno; abren su puerta y se conservan |
| Fusibles | Cabañas 2 y 3 | Casetas de generadores |
| Documentos | Exploración | Ninguno |

## Reglas

#### Vida y salud

* **Vulnerabilidad:** Vadrik no tiene barra de salud; si la criatura lo atrapa, el intento termina.
* **Recuperación:** no existen botiquines, curación ni regeneración.
* **Reaparición:** tras una captura, el jugador vuelve al último checkpoint.
* **Sin mejoras:** el personaje no se vuelve más fuerte ni más rápido durante la partida.

#### Batería y pilas

* **Límite:** la batería nunca supera el 100 %; el sobrante de una pila se pierde.
* **Sin acumulación:** las pilas se usan al recogerlas y no se guardan en el inventario.
* **Consumo:** la linterna gasta 0.3 % por segundo encendida; apagada no gasta.
* **Agotamiento:** al llegar a 0 %, la linterna deja de iluminar y queda una luz ambiental mínima para poder continuar.
* **Sin regeneración:** las pilas no reaparecen; la única recuperación extra es el mínimo de 30 % al reaparecer tras una captura.

#### Llaves y cabañas

* **Correspondencia:** cada llave abre únicamente la puerta de su cabaña.
* **Permanencia:** una puerta desbloqueada sigue abierta durante toda la partida.
* **Checkpoints:** entrar a las cabañas 2 y 3 guarda el progreso.

#### Laboratorio

* **Fusibles:** cualquiera de los dos fusibles funciona en cualquiera de las dos casetas.
* **Activación:** en cada caseta, E coloca el fusible y E baja la palanca; el generador se enciende con luz y sonido, y hace ruido a 8 m.
* **Energía:** con los dos generadores encendidos se activa el panel de código y se guarda un checkpoint.
* **Permanencia:** un generador encendido no se apaga, ni siquiera tras una captura.
* **Panel de código:** acepta 4 dígitos, no tiene límite de intentos y un código incorrecto no tiene penalización.
* **Revelación:** el archivo de Jereth, en la oficina del Dr. Cooper, es el único documento obligatorio para terminar el juego.

## Balance

**Cálculo de la batería**

| Concepto | Valor |
|---|---|
| Batería total disponible en la partida | 100 % inicial + 4 pilas × 40 % = 260 % |
| Duración de 100 % de batería | 100 ÷ 0.3 ≈ 333 s ≈ 5.5 min |
| Luz total disponible | 260 ÷ 0.3 ≈ 867 s ≈ 14.4 min |
| Duración estimada de la partida | 30 a 35 min |
| Tiempo que el jugador debe pasar sin linterna | Más de la mitad de la partida |

Con este balance, el jugador no puede llevar la linterna encendida todo el tiempo: debe encenderla para buscar objetos en el interior oscuro de las cabañas y apagarla en los trayectos o cuando la criatura está cerca. El mínimo de 30 % al reaparecer evita que una partida quede sin salida por falta de luz.

**¿Qué comportamiento queremos incentivar?**

Que el jugador observe antes de actuar, decida cuándo vale la pena gastar batería, preste atención a los documentos (como el código de la pizarra) y busque refugio en lugar de correr sin rumbo.

**¿Qué comportamiento queremos evitar?**

Que avance corriendo sin observar, deje la linterna encendida todo el tiempo, interactúe al azar o repita intentos sin aprender de las capturas. Por eso correr hace más ruido, la luz delata al jugador y las pilas son limitadas.

> **Navegación:** [[00 - Índice]] · ← [[05 - Progresión]] · [[07 - Reglas y Estados del Juego]] →