# Audio y Música

## Descripción de la sección

Define la identidad sonora y cómo el audio comunica información al jugador.

## Música

**Estilo:** Música ambiental oscura y lenta en el menú principal. Durante la partida, se utiliza música tenue y de baja intensidad, combinada con los sonidos del bosque, la lluvia intermitente y la criatura mutante para mantener la tensión sin opacar los efectos ambientales.

**Instrumentación:** sintetizadores graves sostenidos (drones), piano lento y texturas atmosféricas, compuestos y producidos en FL Studio.

**Temas principales:** un solo tema para el menú principal, en bucle, que anticipa la soledad y el misterio del bosque.

**Música dinámica:** no. La respuesta dinámica al peligro está en el audio de la criatura, cuya respiración cambia según si patrulla, investiga o persigue.

## Efectos de sonido

| Evento                                   | Sonido                                                                                                     | Propósito                                                      | Estado        |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- | ------------- |
| Lluvia intermitente                      | Bucle de lluvia sobre el bosque (`rain_forest_loop.wav`), atenuado dentro de las cabañas y del laboratorio | Reforzar la noche, el aislamiento y la tensión                 | Implementado  |
| Pasos de Vadrik                          | 3 variaciones de paso con tono aleatorio (0.94 a 1.06); más suaves agachado                                | Comunicar el movimiento y el ruido producido                   | Implementado  |
| Criatura en patrulla                     | Respiración lenta                                                                                          | Avisar que está cerca, aunque no haya detectado al jugador     | Implementado  |
| Criatura investigando o buscando         | Respiración agitada                                                                                        | Indicar que oyó algo                                           | Implementado  |
| Criatura persiguiendo                    | Respiración intensa y alerta al iniciar la persecución                                                     | Advertir que el jugador fue descubierto                        | Implementado  |
| Pasos de la criatura                     | Paso pesado cada 0.55 s                                                                                    | Indicar su dirección y cercanía                                | Implementado  |
| Encender o apagar la linterna            | Clic del interruptor                                                                                       | Confirmar el cambio de estado                                  | Implementado  |
| Recoger una pila, una llave o un fusible | Sonido breve de objeto                                                                                     | Confirmar que se obtuvo                                        | Implementado  |
| Abrir una puerta / puerta cerrada        | Rechinido de bisagra / cerradura trabada                                                                   | Confirmar la apertura o indicar que falta la llave             | Implementado  |
| Colocar un fusible y bajar la palanca    | Encaje metálico y palanca pesada                                                                           | Confirmar cada paso del generador                              | Implementado  |
| Generador encendido                      | Arranque y motor en marcha                                                                                 | Indicar que está activo y explicar por qué atrae a la criatura | Implementado  |
| Panel de código                          | Pitido por dígito; tono de error o de aceptación                                                           | Confirmar cada dígito y el resultado                           | Implementado  |
| Checkpoint                               | Aviso breve y discreto                                                                                     | Confirmar el guardado                                          | Implemmentado |
| Captura                                  | Golpe sonoro con el grito de la criatura                                                                   | Reforzar el momento de la derrota                              | Implementado  |
| Jumpscare final                          | Golpe sonoro fuerte con el grito de la criatura                                                            | Cerrar la historia de forma impactante                         | Implementado  |


## Audio espacial

| Fuente | Tipo | Detalle |
|---|---|---|
| Criatura (respiración y pasos) | 3D | Se oye con claridad a 1.5 m y deja de oírse a 24 m; permite saber de qué lado viene |
| Generadores | 3D | El motor se oye desde las casetas |
| Puertas | 3D | El sonido sale de la puerta |
| Lluvia y ambiente | 2D | Rodean al jugador; se atenúan dentro de refugios |
| Pasos de Vadrik, linterna, objetos e interfaz | 2D | Se oyen siempre al mismo volumen |

## Voz

**Narración:** No hay narrador. La introducción se presenta mediante un storyboard ilustrado con texto, mientras que los elementos narrativos se consultan durante la exploración.

**Diálogos hablados:** no hay. Los diálogos de la fogata y del Dr. Cooper se muestran como texto con opciones.

**Vocalizaciones:** la criatura no habla; se comunica con respiraciones, gruñidos y gritos. Su volumen se controla con la opción «Voces» de la configuración.

**Idiomas:** español.

## Mezcla

| Prioridad | Grupo                     | Volumen relativo                  | Comportamiento                                                                                         |
| --------- | ------------------------- | --------------------------------- | ------------------------------------------------------------------------------------------------------ |
| 1         | Captura y jumpscare       | El más alto                       | Se escuchan por encima de todo                                                                         |
| 2         | Criatura                  | Voz 55 %, pasos 45 %              | Deben distinguirse sobre la lluvia en todo momento                                                     |
| 3         | Interacciones y UI        | Medio                             | Confirmaciones breves que no tapan a la criatura                                                       |
| 4         | Pasos de Vadrik           | 38 % (agachado 42 % de ese valor) | Más suaves al agacharse, como en el ruido de la jugabilidad                                            |
| 5         | Lluvia y ambiente         | Fondo constante                   | La lluvia aparece de forma intermitente y su sonido se atenúa dentro de las cabañas y del laboratorio. |
| 6         | Música durante la partida | Bajo                              | Acompaña la exploración y se mezcla suavemente con los sonidos ambientales sin ocultar las amenazas.   |
| —         | Música del menú           | Medio                             | Solo en el menú principal                                                                              |

El jugador ajusta tres volúmenes desde la configuración: **general** (100 % por defecto), **ambiente** (80 %) y **voces** (100 %).

