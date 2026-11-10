# Controles

## Descripción de la sección

Define la relación entre las acciones del jugador y las entradas físicas del dispositivo.

## Mapa de controles

Dark Mutant se juega únicamente con teclado y mouse. No hay soporte para control (mando) ni pantalla táctil.

**Exploración**

| Acción | Teclado | Mouse |
|---|---|---|
| Mover | W, A, S y D (mantener) | — |
| Mirar y orientar la linterna | — | Movimiento |
| Correr | Shift izquierdo (mantener, solo de pie) | — |
| Agacharse o ponerse de pie | C (pulsar para alternar) | — |
| Interactuar: leer, recoger, abrir, usar llave, colocar fusible, bajar palanca y usar el panel de código | E (pulsar) | — |
| Entrar o salir de un escondite | E (pulsar) | — |
| Encender o apagar la linterna | F (pulsar) | — |
| Abrir o cerrar el inventario | Tab (pulsar) | — |
| Pausa | Esc (pulsar) | — |
| Saltar | Sin asignación; el recorrido no requiere saltar | — |

**Inventario**

| Acción | Teclado | Mouse |
|---|---|---|
| Cambiar de pestaña (Inventario / Documentos) | Q y E | Clic en la pestaña |
| Moverse por la lista | W y S, o flechas | Clic en el elemento; rueda para desplazar |
| Examinar un objeto o leer un documento completo | F o Intro | Clic |
| Cerrar | Tab o Esc | Botón «Cerrar» |

**Panel de código, diálogos y menús**

| Acción | Teclado | Mouse |
|---|---|---|
| Ingresar un dígito en el panel de código | Teclas 0 a 9 (fila superior o teclado numérico) | Clic en el dígito |
| Confirmar o cerrar el panel de código | Intro / Esc | Botones del panel |
| Elegir una opción de diálogo o continuar | — | Clic izquierdo |
| Cerrar una lectura | Esc | Botón «Cerrar» |
| Seleccionar en menús | — | Clic izquierdo |
| Volver desde Configuración | Esc | Botón «Volver» |
| Reintentar tras una captura | — | Clic en «Reintentar» |

## Principios de control

- **Una tecla por función:** E siempre sirve para interactuar con lo que el jugador tiene enfrente, F siempre es la linterna y Tab siempre es el inventario.
- **Acciones críticas cerca de W A S D:** correr (Shift), agacharse (C), interactuar (E) y linterna (F) se alcanzan sin soltar el movimiento, lo cual es importante durante una persecución.
- **Sin combinaciones:** ninguna acción requiere pulsar dos teclas a la vez, salvo moverse y correr.
- **Retroalimentación inmediata:** cada acción tiene una respuesta visual o sonora (ver la tabla de abajo). No hay vibración, porque no hay soporte para control.

## Reasignación

El jugador no puede cambiar las teclas asignadas. Desde Configuración sí puede ajustar la sensibilidad del mouse e invertir el eje Y, además de las opciones de audio, video y accesibilidad.

## Entrada y retroalimentación

| Entrada / acción | Respuesta inmediata | Confirmación o límite |
|---|---|---|
| W, A, S y D | Movimiento según hacia dónde mira la cámara, con sonido de pasos según la postura | Las colisiones bloquean el paso; la diagonal no aumenta la velocidad |
| Movimiento del mouse | Cambia la mirada y la dirección de la linterna | En los menús mueve el cursor; en un escondite solo gira la cámara |
| Shift mantenido | Aumenta la velocidad mientras se mueve de pie | Pasos más ruidosos (12 m); no funciona agachado |
| C | Cambia la altura de la cámara y la postura | Pasos más silenciosos (2 m); si hay un techo encima, sigue agachado |
| F | Enciende o apaga la linterna con un sonido breve | Gasta batería encendida; con 0 % muestra «Sin batería»; no funciona en un escondite |
| E sobre un documento | Abre la pantalla de lectura y pausa el juego | Se agrega a Documentos; volver a leerlo no lo duplica |
| E sobre una llave o un fusible | Lo recoge y muestra su nombre | Se agrega al Inventario y desaparece del escenario |
| E sobre una pila | La usa al instante y recupera 40 % de batería | Máximo 100 %; si la batería está llena, el sobrante se pierde |
| E sobre una puerta | La abre si tiene la llave correcta | Sin la llave muestra «Está cerrada con llave» |
| E sobre una caseta de generador | Primero coloca el fusible; después baja la palanca y enciende el generador con luz y sonido | Sin fusible muestra «Falta un fusible»; el generador hace ruido a 8 m y no se puede apagar |
| E sobre el panel de código | Abre el teclado numérico y pausa el juego | Sin energía no responde; código incorrecto: «Código incorrecto»; código correcto: la puerta se desbloquea |
| E sobre un escondite | Coloca al jugador dentro y apaga la linterna | Muestra «[E] Salir»; corta la persecución |
| E desde un escondite | Devuelve al jugador al punto de salida | La linterna sigue apagada; no hay invulnerabilidad |
| Tab | Abre o cierra el inventario y cambia entre cursor y cámara | Pausa el juego; no se abre si hay otra pantalla abierta |
| Esc | Cierra la pantalla abierta o abre la pausa | Los menús siguen respondiendo con el juego detenido |
| Clic en una opción de diálogo | Muestra la respuesta del otro personaje | La elección no se puede cambiar y no altera el final |
| Captura | Se bloquean las entradas y aparece la pantalla de captura | Opciones «Reintentar» y «Menú principal» |
| Clic en «Reintentar» | Carga el último checkpoint | La criatura vuelve a su patrulla, la batería queda en al menos 30 % y el jugador no aparece bajo ataque inmediato |

## Aprendizaje de los controles

Los controles se enseñan dentro de la cabaña 1, que es una zona segura, mediante los avisos de interacción y el objetivo en pantalla, en este orden: mirar y caminar, encender la linterna en la oscuridad, leer un documento, recoger la llave y abrir la puerta. Agacharse, esconderse y recoger pilas se aprenden en el bosque y en la cabaña 2, con el aviso que aparece al apuntar cada objeto. La lista completa de controles se puede consultar en el menú de pausa.

> **Navegación:** [[00 - Índice]] · ← [[03 - Sistemas]] · [[05 - Progresión]] →