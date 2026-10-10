# Mecánicas

## Descripción de la sección

Una mecánica es una regla o interacción mediante la cual el jugador puede actuar dentro del sistema del juego.

Documenta cada mecánica con suficiente detalle para que otro integrante pueda implementarla.

## Mecánicas principales

### Mecánica 01 - Explorar e investigar el entorno

**Propósito:**  

Permitir que el jugador descubra información sobre el experimento mediante la observación, la lectura y el uso de objetos. La investigación proporciona razones para abandonar la seguridad de las cabañas.

**Activación:**  

Acercarse a un elemento interactivo, apuntar al mismo con el centro de la cámara y pulsar la entrada de interacción. Si la interacción corresponde a un acertijo, utilizar las acciones que se definan para ese elemento.

**Reglas:**  

- Solo se puede interactuar con un elemento a la vez y sin una pared u obstáculo entre la cámara y el elemento interactivo.

- El mensaje contextual indica la acción disponible a realizar: leer, recoger, abrir, examinar o utilizar.

- Los documentos, imágenes y dibujos se registran en el archivo de notas. Las llaves se guardan en una lista breve de llaves. Cada elemento tiene un identificador único y solo se incorpora una vez.

- Resolver un puzle abre el acceso a la siguiente zona y guarda un checkpoint. La pista, la solución y la ubicación de cada puzle están en [[03 - Sistemas]], sistema S03.

- Si una interacción no cumple sus requisitos, se informa al jugador sin marcarla como completada.

- Las pantallas de lectura y archivo pausan la simulación. Los acertijos que utilicen un panel contextual seguirán la misma regla; las interacciones realizadas directamente en el escenario no pausan por sí solas.

**Entrada:**  

- **[E]** para interactuar, clic izquierdo para seleccionar opciones y botones de interfaz

- **[Esc]** para cerrar una pantalla contextual 

- **[Tab]** para consultar el archivo de notas.

**Estado inicial:**  

Jugador en exploración con un elemento interactivo disponible. La información aún no se ha registrado o la interacción permanece pendiente.

**Estado final:**  

Información registrada, objeto incorporado o mecanismo actualizado. Si se completa un requisito de investigación, también se actualiza el objetivo correspondiente.

**Recursos utilizados:**  

Elementos interactivos, lista de llaves, archivo de notas, interfaz contextual cuando corresponda y estados de progreso. No se utilizan monedas, fabricación ni objetos consumibles de investigación

**Recompensa:**  

Información sobre el experimento, acceso a la siguiente zona y avance de la historia.

**Penalización:**  

No cumplir los requisitos de una interacción impide completar esa acción. Las consecuencias de fallar un acertijo se definirán para cada caso. La exploración fuera de las cabañas expone al jugador a la criatura.

**Interacciones con otras mecánicas:**

El desplazamiento permite alcanzar las pistas, la linterna facilita verlas, el sigilo permite investigar zonas con riesgo.

**Casos límite:**  

- Releer una pista no duplica registros ni vuelve a ejecutar eventos de progreso.

- Si dos objetos están próximos, se selecciona el primero alcanzado por el centro de la cámara; su nombre aparece en pantalla.

- Un objeto obligatorio no puede descartarse ni quedar fuera del recorrido accesible.

- Cerrar una interfaz no marca una interacción o acertijo como resuelto si sus requisitos no se han cumplido.

- Tras reaparecer en un checkpoint, objetos, notas, llaves y puertas coinciden con el estado guardado al resolver el último puzle.

### Mecánica 02 - Evitar a la criatura y utilizar escondites

**Propósito:**  

Construir tensión mediante la vulnerabilidad del padre y permitir que la observación del entorno sea una herramienta de supervivencia.

**Activación:**  

Alejarse del campo visual de la criatura, reducir el ruido al agacharse y utilizar un escondite señalado como interactivo.

**Reglas:**

- La detección depende de visibilidad, distancia y ruido. Agacharse reduce el ruido y retrasa la confirmación visual, no vuelve invisible al jugador.

- Una pared o cobertura sólida bloquea la visión. La oscuridad y la lluvia reducen la visibilidad, pero no garantizan seguridad.

- Correr y encender un generador generan señales que pueden atraer a la criatura.

- Para esconderse, el jugador debe estar a 2 metros o menos de un escondite libre y pulsar E.

- Entrar en un escondite coloca al jugador en una posición definida, apaga la linterna y desactiva el movimiento. La cámara conserva un giro limitado.

- Al salir, la linterna permanece apagada hasta que el jugador la encienda con F.

- La cabaña inicial funciona como espacio protegido. La criatura no puede entrar ni atacar a través de sus paredes.

- La lluvia es constante y dificulta orientarse y escuchar a la criatura. Reduce el alcance de sus sentidos en exteriores, por lo que ofrece oportunidades para moverse sin ser detectado.
- La criatura emite un tarareo apagado cuando está cerca, que funciona como aviso de proximidad. El ruido de un generador encendido también la atrae.

**Entrada:**  

**[W, A, S y D]** para moverse, **[Ctrl]** izquierdo para alternar agachado, **[E]** para entrar o salir del escondite, **[Mouse]** para observar.

**Estado inicial:**  

Jugador expuesto, desplazándose o perseguido. Criatura patrullando, investigando o persiguiendo.

**Estado final:**  

Jugador fuera de la vista o dentro de un escondite. La criatura pasa a buscar si pierde el contacto, o continúa hacia el escondite si observó la entrada.

**Recursos utilizados:**  

Coberturas, puntos de escondite, rutas de escape, percepción de la criatura y sonidos del jugador.

**Recompensa:**  

Evitar la captura y obtener una oportunidad para continuar la investigación.

**Penalización:**  

Ser visto puede provocar persecución; ser escuchado puede atraer a la criatura a investigar el origen del ruido. Ser encontrado permite que la criatura se acerque y ataque.

**Interacciones con otras mecánicas:**  

La carrera permite crear distancia, aunque produce ruido. La linterna facilita ver, pero puede revelar una posición. Los escondites permiten romper el contacto.

**Casos límite:**

- Un escondite no es válido si está bloqueado o su posición de salida no es utilizable, el nivel debe garantizar al menos una salida libre.

- No se puede entrar a un escondite durante la captura o una pantalla de lectura.

- Salir no concede invulnerabilidad. Se coloca al jugador en un punto de salida que no atraviese paredes.

- Si se solicita ponerse de pie bajo un obstáculo, el jugador continúa agachado hasta disponer de espacio.

### Mecánica 03 - Linterna y batería

**Propósito:** Dar al jugador una herramienta de visión con un costo, de modo que cada decisión de iluminar sea un riesgo.

**Activación:** Pulsar **[F]** para alternar la linterna. Recoger baterías con **[E]**.

**Reglas:**

- La linterna inicia al 100% y consume 0.3% por segundo mientras está encendida. Apagada no consume.

- Cada batería recogida recarga 40%, hasta un máximo de 100%.

- Al llegar a 0%, la linterna se apaga y queda una luz ambiental mínima para no dejar la partida sin salida.

- La criatura puede notar el haz si lo percibe, y eso la atrae a investigar el origen.

- Entrar a un escondite apaga la linterna, y al salir se enciende con **[F]**.

- Hay 4 baterías en el mapa y siempre una alcanzable antes del siguiente puzle.

**Entrada:** **[F]**, **[E]** y movimiento del mouse.

**Estado inicial:** Linterna encendida o apagada, con un porcentaje de batería.

**Estado final:** Haz visible o apagado, orientado hacia donde observa el jugador.

**Recursos utilizados:** Linterna, iluminación y visibilidad de los objetos.

**Recompensa:** Reconocer caminos, pistas y amenazas.

**Penalización:** Gastar batería y revelar posición.

**Interacciones con otras mecánicas:** Investigación, sigilo y exploración. La linterna facilita ver pistas, pero puede revelar la posición al jugador.

**Casos límite:**  

Pausar o abrir el archivo no consume batería. Al reaparecer en un checkpoint, la batería tiene un mínimo del 30%. La lluvia no afecta a la linterna. 


## Mecánicas secundarias

Las siguientes mecánicas complementan el núcleo y utilizan la misma ficha para facilitar su implementación.

### Mecánica secundaria 01 - Desplazamiento y carrera

**Propósito:**  

Recorrer el mapa, alcanzar pistas y escapar de una persecución.

**Activación:**  

Pulsar las **teclas de dirección** y mantener **[Shift izquierdo]** para correr mientras el jugador está de pie.

**Reglas:**

- Velocidades iniciales: caminar 2.5 m/s, correr 4.5 m/s y agachado 1.2 m/s.

- El movimiento diagonal tiene la misma velocidad máxima que el movimiento en línea recta.

- La carrera se limita al estado de pie y termina al agacharse.

- La carrera no utiliza una barra de resistencia en el alcance inicial. Su costo es el ruido y la dificultad para observar pistas.

- Las colisiones delimitan el recorrido. El nivel permite transitar sin una acción de salto.

**Entrada:**  

**[W, A, S y D]**. **[Shift izquierdo]** mantenido, **[Mouse]** para orientar la cámara.

**Estado inicial:** Jugador activo, detenido o desplazándose.

**Estado final:** Posición y orientación actualizadas dentro del espacio transitable.

**Recursos utilizados:** Control del jugador, cámara, colisiones y señales de pasos.

**Recompensa:** Alcanzar destinos y crear distancia respecto a la criatura.

**Penalización:** Correr genera pasos que pueden atraer la criatura desde más lejos.

**Interacciones con otras mecánicas:** Investigación, sigilo y acceso a escondites.

**Casos límite:**  

En pausa, captura, escondite o pantalla contextual no hay desplazamiento. Soltar las teclas o perder el foco de la ventana detiene el movimiento. No se modifica la velocidad por la tasa de fotogramas.

### Mecánica secundaria 02 - Agacharse

**Propósito:** Reducir el ruido al desplazarse y aprovechar coberturas bajas.

**Activación:** Alternar entre de pie y agachado.

**Reglas:**  

Reduce la altura de la cámara y la velocidad a 1.2 m/s. No permite correr y no elimina la detección visual. Solo puede recuperarse la postura de pie si existe espacio sobre el jugador.

**Entrada:** Ctrl izquierdo pulsado.

**Estado inicial:** Jugador de pie o agachado.

**Estado final:** Postura alternada, o conservada si el espacio impide levantarse.

**Recursos utilizados:** Altura del jugador, cámara, colisiones y ruido de pasos.

**Recompensa:** Menor probabilidad de atraer a la criatura por sonido.

**Penalización:** Menor velocidad de desplazamiento.

**Interacciones con otras mecánicas:** Sigilo, desplazamiento, uso de cobertura y linterna.

**Casos límite:**  

No cambia la postura durante captura, escondite o pantalla contextual. Si se entra agachado a un escondite, se recupera esa postura al salir.

### Mecánica secundaria 03 - Consultar el archivo de notas

**Propósito:** Permitir recordar la información encontrada, sin indicar al jugador qué hacer a continuación.

**Activación:** Pulsar **[Tab]** y seleccionar una entrada.

**Reglas:**

- El archivo muestra únicamente notas, imágenes y mensajes, y las llaves obtenidas. No muestra objetivos.

- Los documentos conservan su texto e imagen después de recogerse. Las voces no se etiquetan como auténticas o falsas.

- Las llaves se usan con **[E]** sobre su puerta, sin arrastrar elementos.

- El panel pausa la simulación y libera el cursor. Cerrarlo devuelve el control de la cámara.

**Entrada:** **[Tab]** para abrir o cerrar, **[Clic izquierdo]** para seleccionar, **[Esc]** para cerrar.

**Estado inicial:** Exploración con las entradas descubiertas hasta ese momento.

**Estado final:** Información consultada y retorno a exploración sin modificar la posición del jugador.

**Recursos utilizados:** Archivo de notas, lista de llaves y pantallas de interfaz.

**Recompensa:** Comprender las pistas y relacionarlas entre sí.

**Penalización:** No aplica una penalización jugable directa.

**Interacciones con otras mecánicas:** Investigación y resolución de puzles.

**Casos límite:**  

Un archivo vacío muestra un mensaje claro. No se abre durante captura o escondite. Si ya hay un panel de lectura o de candado abierto, **[Tab]** no abre un segundo panel. Al reaparecer en un checkpoint, el archivo conserva lo descubierto hasta ese punto.

> **Navegación:** [[00 - Índice]] · ← [[01 - Jugabilidad]] · [[03 - Sistemas]] →
