# Mecánicas

## Descripción de la sección

Una mecánica es una regla o interacción mediante la cual el jugador puede actuar dentro del sistema del juego.

Documenta cada mecánica con suficiente detalle para que otro integrante pueda implementarla.

## Resumen de mecánicas

| Tipo | Mecánica | Entrada principal |
|---|---|---|
| Principal | 01 - Explorar e investigar el entorno | E, Tab |
| Principal | 02 - Evitar a la criatura y utilizar escondites | C, E, W A S D |
| Principal | 03 - Linterna y batería | F, E |
| Principal | 04 - Restablecer la energía del laboratorio | E |
| Principal | 05 - Panel de código | E, teclas 0 a 9, clic |
| Secundaria | 01 - Desplazamiento y carrera | W A S D, Shift |
| Secundaria | 02 - Agacharse | C |
| Secundaria | 03 - Inventario | Tab, Q / E, W / S, F |
| Secundaria | 04 - Diálogos por opciones | Clic izquierdo |

## Mecánicas principales

### Mecánica 01 - Explorar e investigar el entorno

**Propósito:**

Permitir que el jugador descubra lo ocurrido con Jereth y quién es en realidad el Dr. Cooper mediante la observación, la lectura de documentos y el uso de objetos. La investigación es lo que obliga al jugador a salir de la seguridad de la cabaña 1.

**Activación:**

Acercarse a un objeto interactivo, apuntarlo con el centro de la cámara y pulsar **E**.

**Reglas:**

- Solo son interactivos: linterna, pilas, llaves, fusibles, notas, archivos, imágenes, puertas, escondites, palancas de los generadores y panel de código. El resto del escenario es decorativo.
- El objeto debe estar a 2 m o menos y sin una pared u obstáculo entre la cámara y el objeto.
- Al apuntar, un mensaje indica la acción disponible: leer, recoger, abrir, colocar, activar o esconderse.
- Las notas, archivos e imágenes se muestran en una pantalla de lectura y se guardan en la pestaña Documentos del inventario. Las llaves y los fusibles se guardan en la pestaña Inventario. Cada objeto tiene un identificador único y solo se registra una vez.
- Las cabañas no tienen luz; para encontrar los objetos de su interior se necesita la linterna.
- Si falta un requisito (una llave, un fusible o la energía), un mensaje lo indica, por ejemplo «Está cerrada con llave», sin marcar la acción como completada.
- La pantalla de lectura pausa el juego.

**Entrada:**

- **[E]** para interactuar.
- **[Esc]** para cerrar una pantalla de lectura.
- **[Tab]** para abrir el inventario.

**Estado inicial:** jugador explorando, con un objeto interactivo al alcance que aún no se ha usado.

**Estado final:** documento leído y registrado, objeto guardado o puerta abierta. Si se completa un paso de la progresión, el objetivo en pantalla se actualiza.

**Recursos utilizados:** objetos interactivos, inventario, pantalla de lectura y banderas de progreso.

**Recompensa:** información sobre el pasado, acceso a nuevas zonas y avance de la historia.

**Penalización:** explorar fuera de las cabañas expone al jugador a la criatura.

**Interacciones con otras mecánicas:** el desplazamiento permite llegar a los objetos, la linterna permite verlos en la oscuridad y el sigilo permite investigar zonas peligrosas.

**Casos límite:**

- Volver a leer un documento no lo duplica ni repite eventos de progreso.
- Si dos objetos están juntos, se selecciona el que toca primero el centro de la cámara; su nombre aparece en pantalla.
- Un objeto obligatorio (llave o fusible) nunca puede quedar fuera del recorrido accesible.
- Al reaparecer en un checkpoint, los objetos, documentos, llaves y puertas coinciden con el estado guardado.

### Mecánica 02 - Evitar a la criatura y utilizar escondites

**Propósito:**

Construir tensión a partir de la vulnerabilidad de Vadrik, que no puede pelear, y convertir la observación del entorno en una herramienta para sobrevivir.

**Activación:**

Salir del campo de visión de la criatura, agacharse para hacer menos ruido o entrar a un escondite (armario, cama o casillero) con **E**.

**Reglas:**

- La criatura detecta al jugador por la vista (cono de 70° hasta 10 m, o 7 m con lluvia), por el ruido y por el haz de la linterna encendida (hasta 8 m).
- Agacharse reduce el ruido de los pasos y hace que la criatura tarde más en confirmar que lo ve (1.2 s en lugar de 0.8 s), pero no vuelve invisible al jugador.
- Las paredes y los objetos sólidos bloquean la visión de la criatura. La lluvia reduce el alcance de su vista y de su oído, pero no garantiza seguridad.
- Correr y encender un generador producen ruido que puede atraer a la criatura.
- Para esconderse, el jugador debe estar a 2 m o menos de un escondite libre y pulsar E.
- Al entrar, el jugador queda en una posición fija, la linterna se apaga y no puede moverse ni encenderla; solo puede girar la cámara.
- Entrar a un escondite cancela la detección y cualquier captura en curso. Si la criatura lo estaba persiguiendo, busca durante 6 s alrededor del último lugar donde lo vio y después vuelve a patrullar.
- La cabaña 1 es una zona protegida: la criatura no puede entrar.
- La criatura se anuncia con su respiración, que cambia cuando patrulla, investiga o persigue, para que el jugador pueda reaccionar antes de ser visto.

**Entrada:** **[W, A, S, D]** para moverse, **[C]** para agacharse, **[E]** para entrar o salir del escondite y **[Mouse]** para observar.

**Estado inicial:** jugador expuesto o perseguido; criatura patrullando, investigando o persiguiendo.

**Estado final:** jugador fuera de la vista de la criatura o dentro de un escondite; la criatura busca y después regresa a su patrulla.

**Recursos utilizados:** coberturas, escondites, rutas de escape, percepción de la criatura y ruido del jugador.

**Recompensa:** evitar la captura y continuar la investigación.

**Penalización:** si la criatura lo ve, lo persigue; si lo oye, investiga el lugar del ruido; si lo alcanza a 3 m o menos durante 0.6 s, lo captura.

**Interacciones con otras mecánicas:** correr crea distancia pero hace ruido; la linterna ayuda a ver pero puede delatar; los escondites rompen la persecución.

**Casos límite:**

- Un escondite bloqueado o sin salida libre no es válido; cada escondite debe tener una salida utilizable.
- No se puede entrar a un escondite durante una captura o con una pantalla abierta.
- Al salir, el jugador aparece en un punto que no atraviesa paredes y no es invulnerable.
- Al salir, la linterna sigue apagada hasta que el jugador pulse F.

### Mecánica 03 - Linterna y batería

**Propósito:** dar al jugador una herramienta para ver que tiene un costo, de modo que cada decisión de iluminar sea un riesgo.

**Activación:** pulsar **[F]** para encender o apagar la linterna; recoger pilas con **[E]**.

**Reglas:**

- La linterna forma parte del equipo de Vadrik desde el inicio y aparece en el inventario.
- La batería empieza al 100 % y gasta 0.3 % por segundo encendida (unos 5.5 minutos de luz continua). Apagada no gasta.
- Cada pila se usa al recogerla y recupera 40 %, hasta un máximo de 100 %. Las pilas no se guardan en el inventario.
- Al llegar a 0 %, la linterna se apaga, aparece el mensaje «Sin batería» y queda una luz ambiental mínima para que el jugador no se quede sin salida.
- La criatura detecta el haz encendido hasta 8 m y va a investigar.
- Hay 4 pilas en el mapa, y siempre hay al menos una alcanzable antes del siguiente objetivo.

**Entrada:** **[F]**, **[E]** y movimiento del mouse para orientar el haz.

**Estado inicial:** linterna encendida o apagada, con un porcentaje de batería.

**Estado final:** haz encendido o apagado, orientado hacia donde mira el jugador, y batería actualizada.

**Recursos utilizados:** linterna, batería, pilas e iluminación de la escena.

**Recompensa:** ver caminos, objetos y amenazas en la oscuridad.

**Penalización:** gastar batería y revelar la posición.

**Interacciones con otras mecánicas:** es necesaria para investigar el interior oscuro de las cabañas; se apaga al esconderse.

**Casos límite:** pausar, leer o abrir el inventario no gasta batería. Al reaparecer en un checkpoint, la batería tiene al menos 30 %. La lluvia no afecta a la linterna.

### Mecánica 04 - Restablecer la energía del laboratorio

**Propósito:** convertir el exterior del laboratorio en la zona de mayor tensión: el jugador debe permanecer expuesto y hacer ruido para poder avanzar.

**Activación:** acercarse a una de las dos casetas de generadores con un fusible en el inventario, pulsar **E** para colocar el fusible y pulsar **E** de nuevo para bajar la palanca.

**Reglas:**

- Hay dos fusibles: uno en la cabaña 2 y otro en la cabaña 3.
- Cada caseta tiene una abertura para un fusible y una palanca. Cualquiera de los dos fusibles sirve en cualquier caseta.
- Sin fusible, la caseta muestra el mensaje «Falta un fusible».
- Al bajar la palanca, el generador se enciende, hace ruido a 8 m (puede atraer a la criatura) y se enciende su luz indicadora.
- Cuando los dos generadores están encendidos, se restablece la energía y se enciende el panel de código de la puerta del laboratorio.

**Entrada:** **[E]**.

**Estado inicial:** generador apagado, sin fusible.

**Estado final:** fusible colocado y generador encendido; con los dos encendidos, el laboratorio tiene energía.

**Recursos utilizados:** fusibles, casetas de generadores, palancas y banderas de progreso.

**Recompensa:** el panel de código de la puerta del laboratorio se activa.

**Penalización:** el ruido del generador puede atraer a la criatura.

**Interacciones con otras mecánicas:** depende de la exploración (encontrar los fusibles) y del sigilo (sobrevivir al ruido).

**Casos límite:** un fusible colocado no puede retirarse. Un generador encendido no se apaga. Al reaparecer en un checkpoint, los generadores encendidos siguen encendidos.

### Mecánica 05 - Panel de código

**Propósito:** cerrar la investigación pidiendo al jugador que use una información que encontró antes: el número escrito en la pizarra de la cabaña 3.

**Activación:** con la energía restablecida, apuntar al panel de la puerta del laboratorio y pulsar **E**.

**Reglas:**

- El código tiene 4 dígitos y está escrito en una pizarra de la cabaña 3.
- Sin energía, el panel no responde.
- El jugador ingresa los dígitos con las teclas numéricas o con clic en los botones del panel, y los confirma.
- Si el código es correcto, aparece el mensaje «Código correcto», la puerta se desbloquea y el objetivo cambia.
- Si es incorrecto, aparece «Código incorrecto» y los dígitos se borran. No hay límite de intentos.
- Si se confirma con menos de 4 dígitos, aparece «Necesitas 4 dígitos».
- El panel abierto pausa el juego.

**Entrada:** **[E]** para abrir, **[0 a 9]** o **[Clic izquierdo]** para ingresar dígitos y **[Esc]** para cerrar.

**Estado inicial:** puerta del laboratorio cerrada y panel encendido.

**Estado final:** puerta desbloqueada.

**Recursos utilizados:** panel de código, pizarra de la cabaña 3 y puerta del laboratorio.

**Recompensa:** acceso al laboratorio y a la escena final.

**Penalización:** ninguna jugable; un código incorrecto solo hace perder tiempo.

**Interacciones con otras mecánicas:** depende de la investigación (haber visto la pizarra) y de la energía restablecida.

**Casos límite:** cerrar el panel sin acertar no desbloquea la puerta. Una vez desbloqueada, la puerta sigue abierta al reaparecer en un checkpoint.

## Mecánicas secundarias

Las siguientes mecánicas complementan el núcleo y utilizan la misma ficha para facilitar su implementación.

### Mecánica secundaria 01 - Desplazamiento y carrera

**Propósito:** recorrer el mapa, alcanzar objetos y escapar de una persecución.

**Activación:** pulsar **W, A, S, D** y mantener **Shift izquierdo** para correr mientras el jugador está de pie.

**Reglas:**

- Velocidades: caminar 2.5 m/s, correr 4.5 m/s y agachado 1.2 m/s.
- El movimiento en diagonal tiene la misma velocidad máxima que en línea recta.
- Solo se puede correr de pie; agacharse termina la carrera.
- No hay barra de resistencia: el costo de correr es el ruido (12 m, u 8 m con lluvia).
- No existe una acción de salto; todo el recorrido se puede transitar sin saltar.

**Entrada:** **[W, A, S, D]**, **[Shift izquierdo]** mantenido y **[Mouse]** para orientar la cámara.

**Estado inicial:** jugador detenido o en movimiento.

**Estado final:** posición y orientación actualizadas dentro del área transitable.

**Recursos utilizados:** Character Controller, cámara, colisiones y ruido de pasos.

**Recompensa:** llegar a los objetivos y alejarse de la criatura.

**Penalización:** correr produce un ruido que la criatura oye desde más lejos.

**Interacciones con otras mecánicas:** investigación, sigilo y acceso a escondites.

**Casos límite:** no hay movimiento en pausa, captura, escondite o con una pantalla abierta. Soltar las teclas o perder el foco de la ventana detiene el movimiento. La velocidad no depende de los FPS.

### Mecánica secundaria 02 - Agacharse

**Propósito:** reducir el ruido al desplazarse y aprovechar coberturas bajas.

**Activación:** pulsar **C** para alternar entre de pie y agachado.

**Reglas:** baja la cámara (altura de 1.8 m a 1.1 m) y la velocidad a 1.2 m/s; reduce el ruido de los pasos de 5 m a 2 m (de 3 m a 1 m con lluvia); no permite correr y no elimina la detección visual. El jugador solo puede levantarse si hay espacio sobre él.

**Entrada:** **[C]**.

**Estado inicial:** jugador de pie o agachado.

**Estado final:** postura cambiada, o la misma si un obstáculo impide levantarse.

**Recursos utilizados:** altura del jugador, cámara, colisiones y ruido de pasos.

**Recompensa:** menor probabilidad de atraer a la criatura por el ruido y más tiempo antes de que confirme que lo ve.

**Penalización:** menor velocidad.

**Interacciones con otras mecánicas:** sigilo, desplazamiento y escondites.

**Casos límite:** la postura no cambia durante una captura, en un escondite o con una pantalla abierta.

### Mecánica secundaria 03 - Inventario

**Propósito:** guardar el equipo y los objetos de progreso, y permitir releer los documentos encontrados, sin indicar al jugador qué hacer a continuación.

**Activación:** pulsar **[Tab]**.

**Reglas:**

- El inventario tiene dos pestañas: **Inventario** (linterna, llaves y fusibles) y **Documentos** (notas, archivos e imágenes).
- Al seleccionar un elemento se muestra su imagen y descripción; con **F** o **Intro** se examina (acercar un objeto o leer el documento completo).
- No muestra objetivos ni pistas sobre dónde ir.
- Las llaves y los fusibles se usan automáticamente al pulsar **E** sobre su puerta o caseta, sin arrastrarlos.
- Abrir el inventario pausa el juego y libera el cursor.

**Entrada:** **[Tab]** para abrir o cerrar, **[Q / E]** para cambiar de pestaña, **[W / S]** o flechas para moverse por la lista, **[F / Intro]** para examinar, **[Clic izquierdo]** para seleccionar y **[Esc]** para cerrar.

**Estado inicial:** exploración, con los objetos y documentos obtenidos hasta ese momento.

**Estado final:** información consultada y regreso a la exploración sin cambiar la posición del jugador.

**Recursos utilizados:** inventario, lista de llaves, fusibles y documentos.

**Recompensa:** relacionar la información de los documentos y recordar qué objetos se tienen.

**Penalización:** no aplica una penalización jugable directa.

**Interacciones con otras mecánicas:** investigación, apertura de puertas y restablecimiento de la energía.

**Casos límite:** una pestaña vacía muestra un mensaje claro. No se abre durante una captura, en un escondite o con otra pantalla abierta. Al reaparecer en un checkpoint, el inventario conserva lo obtenido hasta ese punto.

### Mecánica secundaria 04 - Diálogos por opciones

**Propósito:** dar voz a Vadrik en los dos momentos clave de la historia y permitir que el jugador elija cómo reacciona, sin cambiar el desenlace.

**Activación:** se inicia automáticamente al llegar a la fogata o al encontrar al Dr. Cooper herido en el laboratorio.

**Reglas:**

- Solo hay dos diálogos: la alucinación de Jereth en la fogata y la conversación con el Dr. Cooper en el laboratorio.
- Cada línea muestra quién habla y su texto; cuando Vadrik debe responder, aparecen de dos a tres opciones.
- Las opciones cambian la respuesta inmediata del otro personaje, pero no el rumbo ni el final de la historia.
- Durante el diálogo el jugador no puede moverse.
- Cada diálogo ocurre una sola vez.

**Entrada:** **[Clic izquierdo]** para elegir una opción o continuar.

**Estado inicial:** jugador llega al punto del diálogo.

**Estado final:** diálogo terminado, bandera de progreso registrada y control devuelto al jugador (o inicio de la escena final, en el caso del Dr. Cooper).

**Recursos utilizados:** sistema de diálogos, pantalla de diálogo y banderas de progreso.

**Recompensa:** información sobre la historia y conexión emocional con Vadrik.

**Penalización:** no aplica.

**Interacciones con otras mecánicas:** progresión y narrativa.

**Casos límite:** la criatura no puede capturar al jugador durante un diálogo. Si el jugador reaparece en un checkpoint después de un diálogo, este no se repite.

> **Navegación:** [[00 - Índice]] · ← [[01 - Jugabilidad]] · [[03 - Sistemas]] →