# Controles

## Descripción de la sección

Define la relación entre las acciones del jugador y las entradas físicas del dispositivo.

## Mapa de controles

| Acción | Teclado | Mouse | Control | Táctil |
|---|---|---|---|---|
| Mover | W, A, S y D - mantener | - | No previsto | No previsto |
| Mirar / orientar el haz | - | Movimiento | No previsto | No previsto |
| Interactuar: recoger, leer, abrir o usar objeto clave | **[E]** - pulsar | - | No previsto | No previsto |
| Entrar / salir del escondite | **[E]** - pulsar, acción contextual | - | No previsto | No previsto |
| Ataque principal: golpe defensivo con linterna | - | Clic izquierdo - pulsar | No previsto | No previsto |
| Ataque secundario: luz intensa defensiva | - | Clic derecho - mantener | No previsto | No previsto |
| Encender / apagar iluminación normal | **[F]** - pulsar | - | No previsto | No previsto |
| Correr | Shift izquierdo - mantener mientras se mueve de pie | - | No previsto | No previsto |
| Agacharse / ponerse de pie | Ctrl izquierdo - pulsar para alternar | - | No previsto | No previsto |
| Abrir / cerrar diario e inventario | Tab - pulsar | - | No previsto | No previsto |
| Seleccionar entrada del diario u opción de interfaz | - | Clic izquierdo - pulsar | No previsto | No previsto |
| Desplazar texto o lista | - | Rueda | No previsto | No previsto |
| Saltar | Sin asignación, el recorrido no requiere salto | - | No previsto | No previsto |
| Menú / pausa | Esc - pulsar durante exploración | Clic izquierdo para elegir opciones | No previsto | No previsto |
| Cerrar lectura, diario o panel contextual | Esc - pulsar, Tab también cierra el diario | Botón "Cerrar" - clic izquierdo | No previsto | No previsto |
| Volver desde opciones | Esc - pulsar | Botón "Volver" - clic izquierdo | No previsto | No previsto |
| Reintentar tras captura | - | Clic izquierdo en "Reintentar" | No previsto | No previsto |

## Principios de control

- Los controles deben ser consistentes.
- Las acciones críticas deben ser fáciles de identificar.
- Debe existir retroalimentación visual, sonora o háptica cuando corresponda.
- Evitar combinaciones innecesariamente complejas.

## Reasignación

El jugador no podrá hacer cambios en las asignaciones de teclas o botones de mouse a los controles contemplados. La sensibilidad de cámara y las opciones de presentación podrán ajustarse sin modificar esas asignaciones.

## Entrada y retroalimentación

| Entrada / acción | Respuesta inmediata | Confirmación o límite |
|---|---|---|
| W, A, S y D | Movimiento relativo a cámara y pasos acordes a postura | Las colisiones bloquean el paso, la diagonal no aumenta velocidad |
| Movimiento del mouse | Cambia mirada y orientación de la linterna | En interfaz mueve el cursor, en escondite respeta los límites de giro |
| **[E]** sobre documento | Abre lectura, registra la entrada y pausa el mundo | Aviso breve de entrada añadida, releer no duplica registros |
| **[E]** sobre objeto clave | Recoge el objeto y actualiza inventario | Nombre del objeto y confirmación sonora, el objeto deja de estar disponible en el mundo |
| **[E]** sobre puerta o mecanismo | Ejecuta la interacción disponible si cumple sus requisitos | Si falta un requisito, lo comunica, no utiliza objetos incorrectos |
| **[E]** sobre escondite | Lleva a la posición de ocultamiento y apaga la linterna | Muestra "[E] - Salir", no borra una persecución si la criatura vio la entrada |
| **[E]** desde escondite | Devuelve al punto de salida y postura anterior | La linterna permanece apagada, no concede invulnerabilidad |
| Shift mantenido | Aumenta velocidad mientras se mueve de pie | Pasos más notorios, no corre al agacharse, golpear o usar luz intensa |
| Ctrl pulsado | Cambia altura y postura | Pasos más suaves, si falta altura para levantarse, conserva postura e indica el obstáculo |
| **[F]** pulsado | Alterna iluminación normal con un sonido breve | No consume reserva ni aplica interrupción a la criatura |
| Clic derecho mantenido | Enciende luz intensa, reduce movimiento a caminar y muestra la reserva | Si el haz alcanza la parte superior del cuerpo o la cabeza sin obstáculos, comunica exposición, 1.2 segundos continuos permiten interrumpirla si no está resistiendo |
| Soltar clic derecho | Termina luz intensa y elimina exposición acumulada | Restaura iluminación previa, la reserva se recupera después de 3 segundos sin uso |
| Reserva agotada | Cesa el haz intenso y aparece un aviso breve | Luz normal encendida, es necesario soltar y volver a pulsar después de recuperar reserva |
| Clic izquierdo pulsado | Inicia el golpe con animación y sonido | Impacto a los 0.2 segundos, si alcanza un objetivo válido, provoca reacción de golpe, recuperación total de 1.5 segundos |
| Defensa contra criatura en resistencia | El haz o golpe se presenta normalmente | Gesto de protección indica que no hubo nueva interrupción, el golpe no se repite por mantener pulsado |
| Tab pulsado | Abre o cierra diario/inventario y cambia entre cursor y cámara | La consulta pausa la simulación, no abre otro panel si ya hay una pantalla contextual |
| Esc pulsado | Cierra el panel abierto o cambia pausa | La interfaz continúa respondiendo con la simulación detenida |
| Captura confirmada | Se bloquean entradas del mundo y aparece la secuencia breve de captura | Después se ofrecen "Reintentar" y "Menú principal" |
| Clic en "Reintentar" | Reinicia la partida según las reglas de reinicio que se definan | Jugador, criatura, entorno e investigación deben corresponder al mismo estado de partida |

Las interacciones de los acertijos utilizarán los controles del mundo o de interfaz que correspondan a su diseño. Sus acciones específicas se documentarán cuando se definan los acertijos, no se asigna aquí una combinación, objeto o mecanismo concreto.

La introducción propone enseñar, en este orden: mirar y caminar dentro de la cabaña, encender/apagar la luz, recoger y consultar una pista, agacharse y usar un escondite, y defenderse. Los mensajes desaparecen después de utilizar la acción y quedan disponibles desde pausa para consulta.

> **Navegación:** [[00 - Índice]] · ← [[03 - Sistemas]] · [[05 - Progresión]] →
