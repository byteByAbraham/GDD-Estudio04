# Controles

## Descripción de la sección

Define la relación entre las acciones del jugador y las entradas físicas del dispositivo.

## Mapa de controles

| Acción                                                                                            | Teclado                                             | Mouse                               | Control     | Táctil      |
| ------------------------------------------------------------------------------------------------- | --------------------------------------------------- | ----------------------------------- | ----------- | ----------- |
| Mover                                                                                             | W, A, S y D - mantener                              | -                                   | No previsto | No previsto |
| Mirar / orientar el haz                                                                           | -                                                   | Movimiento                          | No previsto | No previsto |
| Interactuar: leer, recoger llaves, baterías, abrir, usar llave, encender generador, usar candado. | **[E]** - pulsar                                    | -                                   | No previsto | No previsto |
| Entrar / salir del escondite                                                                      | **[E]** - pulsar, acción contextual                 | -                                   | No previsto | No previsto |
| Encender / apagar linterna                                                                        | **[F]** - pulsar                                    | -                                   | No previsto | No previsto |
| Correr                                                                                            | Shift izquierdo - mantener mientras se mueve de pie | -                                   | No previsto | No previsto |
| Agacharse / ponerse de pie                                                                        | Ctrl izquierdo - pulsar para alternar               | -                                   | No previsto | No previsto |
| Abrir / cerrar archivo de notas                                                                   | Tab - pulsar                                        | -                                   | No previsto | No previsto |
| Elegir opción de diálogo                                                                          | Teclas **[1]** y [2]                                | Clic izquierdo                      | No previsto | No previsto |
| Seleccionar en interfaz                                                                           | -                                                   | Clic izquierdo - pulsar             | No previsto | No previsto |
| Desplazar texto o lista                                                                           | -                                                   | Rueda                               | No previsto | No previsto |
| Saltar                                                                                            | Sin asignación, el recorrido no requiere salto      | -                                   | No previsto | No previsto |
| Menú / pausa                                                                                      | Esc - pulsar durante exploración                    | Clic izquierdo para elegir opciones | No previsto | No previsto |
| Cerrar lectura o panel                                                                            | Esc - pulsar, Tab también cierra el archivo         | Botón "Cerrar" - clic izquierdo     | No previsto | No previsto |
| Volver desde opciones                                                                             | Esc - pulsar                                        | Botón "Volver" - clic izquierdo     | No previsto | No previsto |
| Reintentar tras captura                                                                           | -                                                   | Clic izquierdo en "Reintentar"      | No previsto | No previsto |

## Principios de control

- Los controles deben ser consistentes.
- Las acciones críticas deben ser fáciles de identificar.
- Debe existir retroalimentación visual, sonora o háptica cuando corresponda.
- Evitar combinaciones innecesariamente complejas.

## Reasignación

El jugador no podrá hacer cambios en las asignaciones de teclas o botones de mouse a los controles contemplados. La sensibilidad de cámara y las opciones de presentación podrán ajustarse sin modificar esas asignaciones.

## Entrada y retroalimentación

| Entrada / acción                 | Respuesta inmediata                                                                    | Confirmación o límite                                                                                                                                    |
| -------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| W, A, S y D                      | Movimiento relativo a cámara y pasos acordes a postura                                 | Las colisiones bloquean el paso, la diagonal no aumenta velocidad                                                                                        |
| Movimiento del mouse             | Cambia mirada y orientación de la linterna                                             | En interfaz mueve el cursor, en escondite respeta los límites de giro                                                                                    |
| **[E]** sobre documento          | Abre lectura, registra la entrada y pausa el mundo                                     | Aviso breve de entrada añadida, releer no duplica registros                                                                                              |
| **[E]** sobre objeto clave       | Recoge el objeto y agrega la llave a la lista de llaves                                | Nombre del objeto y confirmación sonora, el objeto deja de estar disponible en el mundo                                                                  |
| **[E]** sobre puerta o mecanismo | Ejecuta la interacción disponible si cumple sus requisitos                             | Si falta un requisito, lo comunica, no utiliza objetos incorrectos                                                                                       |
| **[E]** sobre escondite          | Lleva a la posición de ocultamiento y apaga la linterna                                | Muestra "[E] - Salir", no borra una persecución si la criatura vio la entrada                                                                            |
| **[E]** desde escondite          | Devuelve al punto de salida y postura anterior                                         | La linterna permanece apagada, no concede invulnerabilidad                                                                                               |
| Shift mantenido                  | Aumenta velocidad mientras se mueve de pie                                             | Pasos más notorios, no corre al agacharse                                                                                                                |
| Ctrl pulsado                     | Cambia altura y postura                                                                | Pasos más suaves, si falta altura para levantarse, conserva postura e indica el obstáculo                                                                |
| **[F]** pulsado                  | Alterna iluminación normal con un sonido breve                                         | Consume batería mientras está encendida                                                                                                                  |
| Tab pulsado                      | Abre o cierra archivo de notas, imágenes y grabaciones, y cambia entre cursor y cámara | La consulta pausa la simulación, no abre otro panel si ya hay una pantalla contextual                                                                    |
| Esc pulsado                      | Cierra el panel abierto o cambia pausa                                                 | La interfaz continúa respondiendo con la simulación detenida                                                                                             |
| Captura confirmada               | Se bloquean entradas del mundo y aparece la secuencia breve de captura                 | Después se ofrecen "Reintentar" y "Menú principal"                                                                                                       |
| Clic en "Reintentar"             | Carga el último checkpoint                                                             | La criatura reaparece en su patrulla inicial, la batería queda en un mínimo del 30% y el jugador no aparece dentro de una pared ni bajo ataque inmediato |
| [E] sobre batería                | La recoge, recarga 40% y suena un aviso breve.                                         | Aviso sonoro breve. Si la batería ya está al 100%, no se desperdicia ni se pierde, se recoge y se completa hasta el 100%                                 |
| [E] sobre generador              | Lo enciende, emite ruido y avisa con luz y sonido.                                     | No se puede apagar. La criatura investiga el origen del ruido                                                                                            |
| [1] / [2] o clic en diálogo      | Elige la opción y continúa el texto.                                                   | Solo hay 2 opciones, y la elección no se puede cambiar una vez hecha                                                                                     |
| **[E]** sobre candado            | Abre un panel para ingresar el código con clic en los dígitos y pausa el mundo         | Un código incorrecto no abre y muestra un aviso breve. **[Esc]** cierra el panel sin resolver                                                            |

Las interacciones de los acertijos usan **[E]** en el mundo (llaves, baterías, generadores y puertas) y un panel contextual con el mouse para el candado de código. Los detalles de cada puzle están en [[03 - Sistemas]], sistema S03.

La introducción propone enseñar, en este orden: mirar y caminar, linterna, leer una pista, agacharse y esconderse, recoger batería. Los mensajes desaparecen después de utilizar la acción y quedan disponibles desde pausa para consulta.

> **Navegación:** [[00 - Índice]] · ← [[03 - Sistemas]] · [[05 - Progresión]] →
