# Mecánicas

## Descripción de la sección

Una mecánica es una regla o interacción mediante la cual el jugador puede actuar dentro del sistema del juego.

Documenta cada mecánica con suficiente detalle para que otro integrante pueda implementarla.

## Mecánicas principales

### Mecánica 01 - Explorar e investigar el entorno

**Propósito:**  

Permitir que el jugador descubra información sobre el experimento mediante la observación, la lectura y el uso de objetos. La investigación proporciona razones para abandonar la seguridad del refugio.

**Activación:**  

Acercarse a un elemento interactivo, apuntar al mismo con el centro de la cámara y pulsar la entrada de interacción. Si la interacción corresponde a un acertijo, utilizar las acciones que se definan para ese elemento.

**Reglas:**  

- Solo se puede interactuar con un elemento a la vez y sin una pared u obstáculo entre la cámara y el elemento interactivo.

- El mensaje contextual indica la acción disponible a realizar: leer, recoger, abrir, examinar o utilizar.

- Los documentos se registran en el diario, los objetos de acceso se guardan en el inventario. Cada elemento tiene un identificador único y solo se incorpora una vez.

- La resolución de un acertijo actualiza el progreso de acuerdo con sus requisitos. Su contenido, solución y consecuencias se definirán cuando se diseñe cada acertijo.

- Si una interacción no cumple sus requisitos, se informa al jugador sin marcarla como completada.

- Las pantallas de lectura y diario pausan la simulación. Los acertijos que utilicen un panel contextual seguirán la misma regla; las interacciones realizadas directamente en el escenario no pausan por sí solas.

**Entrada:**  

- **[E]** para interactuar, clic izquierdo para seleccionar opciones y botones de interfaz

- **[Esc]** para cerrar una pantalla contextual 

- **[Tab]** para consultar el diario e inventario.

**Estado inicial:**  

Jugador en exploración con un elemento interactivo disponible. La información aún no se ha registrado o la interacción permanece pendiente.

**Estado final:**  

Información registrada, objeto incorporado o mecanismo actualizado. Si se completa un requisito de investigación, también se actualiza el objetivo correspondiente.

**Recursos utilizados:**  

Elementos interactivos, inventario de objetos clave, diario, interfaz contextual cuando corresponda y estados de progreso. No se utilizan monedas, fabricación ni objetos consumibles de investigación.

**Recompensa:**  

Información sobre el experimento, acceso a elementos o zonas y avance de la investigación, según los objetivos que se definan.

**Penalización:**  

No cumplir los requisitos de una interacción impide completar esa acción. Las consecuencias de fallar un acertijo se definirán para cada caso. La exploración fuera de los espacios protegidos expone al jugador a la criatura.

**Interacciones con otras mecánicas:**

El desplazamiento permite alcanzar las pistas; la iluminación facilita verlas; el sigilo y la defensa permiten investigar zonas amenazadas. El progreso puede activar la transición a lluvia mediante el evento que se defina para la investigación.

**Casos límite:**  

- Releer una pista no duplica registros ni vuelve a ejecutar eventos de progreso.

- Si dos objetos están próximos, se selecciona el primero alcanzado por el centro de la cámara; su nombre aparece en pantalla.

- Un objeto obligatorio no puede descartarse ni quedar fuera del recorrido accesible.

- Cerrar una interfaz no marca una interacción o acertijo como resuelto si sus requisitos no se han cumplido.

- Tras un reinicio, objetos, documentos, mecanismos y puertas deben coincidir con el estado de partida que se restablezca. El método de reinicio y guardado está pendiente de definición.

### Mecánica 02 - Evitar a la criatura y utilizar escondites

**Propósito:**  

Construir tensión mediante la vulnerabilidad del padre y permitir que la observación del entorno sea una herramienta de supervivencia.

**Activación:**  

Alejarse del campo visual de la criatura, reducir el ruido al agacharse y utilizar un escondite señalado como interactivo.

**Reglas:**

- La detección depende de visibilidad, distancia y ruido. Agacharse reduce el ruido y retrasa la confirmación visual, no vuelve invisible al jugador.

- Una pared o cobertura sólida bloquea la visión. La oscuridad y la lluvia reducen la visibilidad, pero no garantizan seguridad.

- Correr y golpear generan señales que pueden atraer a la criatura.

- Para esconderse, el jugador debe estar a 2 metros o menos de un escondite libre y pulsar E.

- Entrar en un escondite coloca al jugador en una posición definida, apaga la linterna y desactiva el movimiento, los golpes y la luz intensa. La cámara conserva un giro limitado.

- Al salir, la linterna permanece apagada hasta que el jugador la encienda con F.

- La cabaña inicial funciona como espacio protegido. La criatura no puede entrar ni atacar a través de sus paredes.

- La lluvia dificulta orientarse y escuchar a la criatura. También reduce el alcance de sus sentidos en exteriores, por lo que ofrece oportunidades para moverse sin ser detectado.

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

La carrera permite crear distancia, aunque produce ruido. La linterna facilita ver, pero puede revelar una posición. La defensa ofrece una oportunidad de romper contacto y esconderse.

**Casos límite:**

- Un escondite no es válido si está bloqueado o su posición de salida no es utilizable, el nivel debe garantizar al menos una salida libre.

- No se puede entrar durante el golpe, la captura o una pantalla de lectura.

- Salir no concede invulnerabilidad. Se coloca al jugador en un punto de salida que no atraviese paredes.

- Si se solicita ponerse de pie bajo un obstáculo, el jugador continúa agachado hasta disponer de espacio.

### Mecánica 03 - Defenderse con la luz y el golpe de la linterna

**Propósito:**  

Ofrecer una defensa limitada que permita escapar y refuerce el conflicto de enfrentarse al cuerpo del hijo.

**Activación:**  

Mantener la luz intensa sobre la criatura o ejecutar un golpe cuando se encuentre a corta distancia.

**Reglas:**

- La iluminación normal ayuda a explorar. La luz intensa es una acción defensiva distinta que utiliza una reserva recargable.

- Mantener el botón derecho activa la luz intensa y obliga a caminar. Alcanza hasta 8 metros y requiere apuntar a la parte superior del cuerpo o a la cabeza de la criatura, sin obstáculos entre ambos.

- Mantener la exposición durante 1.2 segundos continuos interrumpe a la criatura durante 2 segundos. Si se pierde el objetivo o se interrumpe el haz, la exposición acumulada vuelve a cero.

- La reserva inicia en 100 unidades, consume 25 unidades por segundo de luz intensa y recupera 20 por segundo después de 3 segundos sin usarla. El golpe y la luz normal no consumen esa reserva.

- Al agotarse la reserva, termina la luz intensa y vuelve la iluminación normal. Es necesario soltar y volver a pulsar el clic derecho después de recuperar reserva.

- Pulsar el clic izquierdo ejecuta un golpe frontal con la linterna, con alcance de 1.5 metros. Tiene 0.2 segundos de preparación, un solo instante de impacto y 1.5 segundos de recuperación desde el inicio.

- Un golpe válido hace retroceder a la criatura hasta 0.5 metros, si hay espacio, y la interrumpe durante 1 segundo. Un golpe solo puede afectar una vez al mismo objetivo.

- Después de cualquier interrupción, la criatura tiene 5 segundos de resistencia a nuevas interrupciones, contados desde que termina el efecto. Esta resistencia se comparte entre golpe y luz intensa.

- Durante esa resistencia no se acumula exposición de luz y los golpes no vuelven a interrumpir. Un gesto de protección de la criatura y una reacción visual breve comunican la resistencia.

- La defensa permite huir, no reduce una barra de salud de la criatura ni permite derrotarla mediante ataques repetidos.

- El golpe interrumpe la luz intensa si se inicia durante su uso. No puede golpearse ni usar la luz intensa desde un escondite o una pantalla contextual.

**Entrada:**  

**[Clic derecho]** del mouse mantenido para luz intensa, **[Clic izquierdo]** pulsado para un golpe. **[F]** controla la iluminación normal.

**Estado inicial:**  

Jugador activo con la linterna disponible. La criatura puede encontrarse patrullando, investigando o persiguiendo.

**Estado final:**  

Criatura interrumpida si se cumplen las condiciones, o defensa fallida si no existe objetivo válido, falta reserva o la criatura está resistiendo. El jugador dispone de una oportunidad para alejarse.

**Recursos utilizados:**  

Linterna, reserva de luz intensa, exposición continua, distancia, visibilidad y tiempos de recuperación.

**Recompensa:**  

Crear un breve momento para romper la persecución y llegar a cobertura.

**Penalización:**  

Fallar consume tiempo y, en el caso de la luz intensa, reserva. Intentar golpear exige acercarse a la criatura y aumenta el riesgo de captura.

**Interacciones con otras mecánicas:**  

La defensa se combina con carrera, cobertura y escondites. La reserva se conserva para las amenazas mientras la luz normal permite investigar.

**Casos límite:**

- Una pared bloquea tanto el golpe como la luz intensa, aunque el modelo de la criatura sea parcialmente visible.

- Una criatura interrumpida cancela su preparación de ataque. Si el jugador acierta una acción defensiva válida al mismo tiempo que la criatura ataca, se prioriza la acción del jugador.

- Durante los 5 segundos de resistencia de la criatura, apuntar el haz no almacena tiempo para interrumpir inmediatamente al terminarla.

- Mantener el botón izquierdo no genera golpes automáticos, cada golpe requiere una pulsación nueva después de la recuperación.

- La linterna está disponible desde el inicio y no puede soltarse ni perderse.

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

- La carrera se limita al estado de pie, termina al agacharse, usar luz intensa o iniciar un golpe.

- La carrera no utiliza una barra de resistencia en el alcance inicial. Su costo es el ruido y la dificultad para observar pistas.

- Las colisiones delimitan el recorrido. El nivel permite transitar sin una acción de salto.

**Entrada:**  

**[W, A, S y D]**. **[Shift izquierdo]** mantenido, **[Mouse]** para orientar la cámara.

**Estado inicial:** Jugador activo, detenido o desplazándose.

**Estado final:** Posición y orientación actualizadas dentro del espacio transitable.

**Recursos utilizados:** Control del jugador, cámara, colisiones y señales de pasos.

**Recompensa:** Alcanzar destinos y crear distancia respecto a la criatura.

**Penalización:** Correr genera pasos que pueden atraer la criatura desde más lejos.

**Interacciones con otras mecánicas:** Investigación, sigilo, defensa y acceso a escondites.

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

No cambia la postura durante captura, escondite, golpe o pantalla contextual. Si se entra agachado a un escondite, se recupera esa postura al salir.

### Mecánica secundaria 03 - Encender y orientar la iluminación normal

**Propósito:** Facilitar la navegación y lectura del entorno durante las dos fases nocturnas.

**Activación:** Encender la linterna y orientar el haz con la cámara.

**Reglas:**

- **[F]** alterna encendida y apagada. La iluminación normal no consume la reserva defensiva y no interrumpe a la criatura.

- Pulsar luz intensa con la iluminación apagada enciende temporalmente el haz. Al soltarla se restaura el estado normal anterior, salvo el agotamiento de reserva, que deja la luz normal encendida.

- **[F]** no altera el estado mientras se usa luz intensa o se ejecuta un golpe, debe pulsarse después de terminar la acción.

- La lluvia reduce la claridad del entorno, pero no modifica la reserva ni avería la linterna.

**Entrada:** **[F]** y movimiento del **[Mouse]**.

**Estado inicial:** Iluminación normal encendida o apagada.

**Estado final:** Haz visible o apagado, orientado hacia donde observa el jugador.

**Recursos utilizados:** Linterna, iluminación y visibilidad de los objetos.

**Recompensa:** Reconocer caminos, pistas y amenazas.

**Penalización:** Dirigir el haz hacia la criatura puede atraerla.

**Interacciones con otras mecánicas:** Investigación, sigilo y defensa con luz intensa.

**Casos límite:**  

Entrar en un escondite apaga la luz y salir no la enciende automáticamente. Durante una pantalla contextual o captura no se acepta **[F]**. Tras reanudar una pausa, la luz intensa requiere una nueva pulsación.

### Mecánica secundaria 04 - Consultar el diario y los objetos clave

**Propósito:** Permitir recordar la información encontrada y consultar el objetivo actual.

**Activación:** Abrir el panel y seleccionar una entrada o un objeto.

**Reglas:**

- El diario muestra únicamente información descubierta, el objetivo actual y los objetos clave obtenidos.

- Los documentos conservan su texto e imagen después de recogerse. Las voces no se etiquetan como auténticas o falsas.

- El inventario inicial es una lista de objetos clave: su capacidad basta para todos los elementos del episodio y no exige ordenar casillas ni descartar objetos.

- Las llaves o piezas se utilizan mediante **[E]** sobre su mecanismo, no requieren arrastrar elementos desde el inventario.

- El panel pausa la simulación y libera el cursor. Cerrarlo devuelve el control de la cámara.

**Entrada:** **[Tab]** para abrir o cerrar, **[Clic izquierdo]** para seleccionar, **[Esc]** para cerrar.

**Estado inicial:** Exploración con las entradas descubiertas hasta ese momento.

**Estado final:** Información consultada y retorno a exploración sin modificar la posición del jugador.

**Recursos utilizados:** Diario, inventario, objetivos y pantallas de interfaz.

**Recompensa:** Comprender pistas y orientar el siguiente paso de investigación.

**Penalización:** No aplica una penalización jugable directa.

**Interacciones con otras mecánicas:** Investigación y resolución del acertijo.

**Casos límite:**  

Un diario vacío muestra un mensaje claro. No se abre durante captura, golpe o escondite. Si ya hay un panel de lectura o acertijo, **[Tab]** no abre un segundo panel. Al restaurar una partida, el diario debe coincidir con la información incluida en el estado recuperado.

> **Navegación:** [[00 - Índice]] · ← [[01 - Jugabilidad]] · [[03 - Sistemas]] →
