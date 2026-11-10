# Audio y Música

## Descripción de la sección

Define la identidad sonora y cómo el audio comunica información al jugador.

## Música

**Estilo:** música ambiental oscura y lenta, solo en el menú principal. Durante la partida no hay música: la tensión la construyen la lluvia, el ambiente del bosque y los sonidos de la criatura.

**Instrumentación:** sintetizadores graves sostenidos (drones), piano lento y texturas atmosféricas, compuestos y producidos en FL Studio.

**Temas principales:** un solo tema para el menú principal, en bucle, que anticipa la soledad y el misterio del bosque.

**Música dinámica:** no. La respuesta dinámica al peligro está en el audio de la criatura, cuya respiración cambia según si patrulla, investiga o persigue.

## Efectos de sonido

| Evento                                   | Sonido                                                                                                     | Propósito                                                      | Estado                         |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- | ------------------------------ |
| Lluvia constante                         | Bucle de lluvia sobre el bosque (`rain_forest_loop.wav`), atenuado dentro de las cabañas y del laboratorio | Reforzar la noche, el aislamiento y la tensión                 | Implementado                   |
| Pasos de Vadrik                          | 3 variaciones de paso con tono aleatorio (0.94 a 1.06); más suaves agachado                                | Comunicar el movimiento y el ruido producido                   | Implementado                   |
| Criatura en patrulla                     | Respiración lenta                                                                                          | Avisar que está cerca, aunque no haya detectado al jugador     | Implementado (audio de prueba) |
| Criatura investigando o buscando         | Respiración agitada                                                                                        | Indicar que oyó algo                                           | Implementado (audio de prueba) |
| Criatura persiguiendo                    | Respiración intensa y alerta al iniciar la persecución                                                     | Advertir que el jugador fue descubierto                        | Implementado (audio de prueba) |
| Pasos de la criatura                     | Paso pesado cada 0.55 s                                                                                    | Indicar su dirección y cercanía                                | Implementado (audio de prueba) |
| Encender o apagar la linterna            | Clic del interruptor                                                                                       | Confirmar el cambio de estado                                  | Pendiente                      |
| Recoger una pila, una llave o un fusible | Sonido breve de objeto                                                                                     | Confirmar que se obtuvo                                        | Pendiente                      |
| Leer un documento                        | Papel al desplegarse                                                                                       | Acompañar la pantalla de lectura                               | Pendiente                      |
| Abrir una puerta / puerta cerrada        | Rechinido de bisagra / cerradura trabada                                                                   | Confirmar la apertura o indicar que falta la llave             | Pendiente                      |
| Colocar un fusible y bajar la palanca    | Encaje metálico y palanca pesada                                                                           | Confirmar cada paso del generador                              | Pendiente                      |
| Generador encendido                      | Arranque y motor en marcha                                                                                 | Indicar que está activo y explicar por qué atrae a la criatura | Pendiente                      |
| Panel de código                          | Pitido por dígito; tono de error o de aceptación                                                           | Confirmar cada dígito y el resultado                           | Pendiente                      |
| Checkpoint                               | Aviso breve y discreto                                                                                     | Confirmar el guardado                                          | Pendiente                      |
| Captura                                  | Golpe sonoro con el grito de la criatura                                                                   | Reforzar el momento de la derrota                              | Pendiente                      |
| Jumpscare final                          | Golpe sonoro fuerte con el grito de la criatura                                                            | Cerrar la historia de forma impactante                         | Pendiente                      |
| Menús                                    | Clic suave al seleccionar                                                                                  | Confirmar la selección                                         | Pendiente                      |

## Audio espacial

| Fuente | Tipo | Detalle |
|---|---|---|
| Criatura (respiración y pasos) | 3D | Se oye con claridad a 1.5 m y deja de oírse a 24 m; permite saber de qué lado viene |
| Generadores | 3D | El motor se oye desde las casetas |
| Puertas | 3D | El sonido sale de la puerta |
| Lluvia y ambiente | 2D | Rodean al jugador; se atenúan dentro de refugios |
| Pasos de Vadrik, linterna, objetos e interfaz | 2D | Se oyen siempre al mismo volumen |

## Voz

**Narración:** no hay narración hablada; la introducción y los documentos se presentan con texto.

**Diálogos hablados:** no hay. Los diálogos de la fogata y del Dr. Cooper se muestran como texto con opciones.

**Vocalizaciones:** la criatura no habla; se comunica con respiraciones, gruñidos y gritos. Su volumen se controla con la opción «Voces» de la configuración.

**Idiomas:** español.

## Mezcla

| Prioridad | Grupo | Volumen relativo | Comportamiento |
|---|---|---|---|
| 1 | Captura y jumpscare | El más alto | Se escuchan por encima de todo |
| 2 | Criatura | Voz 55 %, pasos 45 % | Deben distinguirse sobre la lluvia en todo momento |
| 3 | Interacciones y UI | Medio | Confirmaciones breves que no tapan a la criatura |
| 4 | Pasos de Vadrik | 38 % (agachado 42 % de ese valor) | Más suaves al agacharse, como en el ruido de la jugabilidad |
| 5 | Lluvia y ambiente | Fondo constante | Se atenúa dentro de cabañas y laboratorio |
| — | Música del menú | Medio | Solo en el menú principal |

El jugador ajusta tres volúmenes desde la configuración: **general** (100 % por defecto), **ambiente** (80 %) y **voces** (100 %).

> **Navegación:** [[00 - Índice]] · ← [[04 - Interfaz Visual]] · [[01 - UX y Flujo del Jugador]] →