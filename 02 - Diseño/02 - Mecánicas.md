# Mecánicas

## Mecánicas principales

### Mecánica 01- Movimiento y exploración en primera persona

**Propósito:** permitir que el jugador recorra el bosque, las cabañas y el laboratorio para reconocer caminos y localizar elementos necesarios para avanzar.

**Activación:** comienza cuando el jugador obtiene el control de Vadrik y utiliza los controles de movimiento y cámara.

**Reglas:**

- La cámara se controla en primera persona y determina hacia dónde observa e interactúa el jugador.
- El jugador puede caminar, correr y agacharse.
- Al intentar levantarse, se comprueba si existe un obstáculo sobre el personaje. Si no hay espacio, permanece agachado.
- El desplazamiento incorpora balanceo de cámara y movimiento al caminar.
- Durante las persecuciones se incorporan temblores de adrenalina.
- El movimiento produce sonidos que se relacionan con el sistema de percepción de la criatura mutante.
- El movimiento se deshabilita durante la pausa y los estados que impiden controlar a Vadrik.

**Entrada:**

| Tecla o control                        | Acción                         |
| -------------------------------------- | ------------------------------- |
| **W**                            | Avanzar                         |
| **S**                            | Retroceder                      |
| **A**                            | Desplazarse a la izquierda      |
| **D**                            | Desplazarse a la derecha        |
| **Mouse**                        | Orientar la cámara             |
| **Shift izquierdo + movimiento** | Correr                          |
| **Ctrl izquierdo**               | Agacharse o intentar levantarse |

**Estado inicial:** Vadrik se encuentra en una zona que el jugador todavía no ha explorado completamente.

**Estado final:** cambia su ubicación, orientación o postura según los controles y el espacio disponible.

**Recursos utilizados:** espacio transitable del escenario. No se especifica un sistema de resistencia para correr.

**Recompensa:** descubrir rutas y elementos necesarios para avanzar.

**Penalización:** el desplazamiento puede producir ruido o exponer al jugador.

**Interacciones con otras mecánicas:** interacción, linterna, sigilo, ruido y persecución.

**Casos límite:**

- Si hay un techo u obstáculo encima, no se permite abandonar la postura agachada.
- Los obstáculos sólidos impiden continuar el desplazamiento en esa dirección.
- Al abrir una interfaz que utiliza el cursor, el control de cámara debe coordinarse con dicha interfaz.
- El movimiento se deshabilita durante la pausa y los estados que impiden controlar a Vadrik.

### Mecánica 02 - Interactuar con objetos y recoger llaves

**Propósito:** permitir que el jugador utilice elementos del escenario y encuentre las llaves necesarias para acceder a las cabañas.

**Activación:** localizar una llave, apuntar hacia ella y presionar E; después, interactuar con su acceso correspondiente.

**Reglas:**

- Cada llave está asociada a un acceso determinado.
- Al recogerla, el sistema registra que se ha cumplido el requisito correspondiente.
- No existe una pantalla de inventario ni selección manual de llaves.
- Al interactuar con el acceso, se comprueba si su llave ya fue recogida.
- El estado del acceso se relaciona con los objetivos y la persistencia.

**Entrada:**

| Tecla o control | Acción                           |
| --------------- | --------------------------------- |
| Mouse           | Apuntar hacia el objeto           |
| E               | Ejecutar la interacción indicada |

**Estado inicial:** objeto disponible o acceso cerrado.

**Estado final:** objeto utilizado, llave registrada o acceso abierto si se cumple el requisito.

**Recursos utilizados:** llave específica y estado de progreso asociado.

**Recompensa:** entrar a una nueva cabaña y continuar la exploración.

**Penalización:** el acceso permanece cerrado mientras no se encuentre la llave correcta.

**Interacciones con otras mecánicas:** exploración, lectura, generadores, objetivos y checkpoints.

**Casos límite:**

- Interactuar sin la llave requerida no abre el acceso.
- Una misma llave no debe registrarse varias veces.
- Al restaurar una partida, el estado de la llave debe ser coherente con el acceso correspondiente.

### Mecánica 03 - Leer notas y expedientes del entorno

Propósito: presentar información narrativa y generar intriga mediante documentos, notas y fotos colocados en los escenarios.

Activación: apuntar hacia una nota o expediente y presionar E.

Reglas:

- El contenido se presenta mediante una interfaz de lectura.
- Los documentos se examinan directamente en el escenario.
- No se recogen ni se almacenan en un inventario.
- No existe un archivo para consultar notas descubiertas.
- Para volver a leer un documento, el jugador debe interactuar nuevamente con él en su ubicación.
- Las notas generan suspenso; los expedientes permiten conocer los experimentos y reconstruir lo ocurrido.

**Entrada**

| Tecla o control                | Acción        |
| ------------------------------ | -------------- |
| E                              | Abrir lectura  |
| Esc (propuesta, por confirmar) | Cerrar lectura |

Estado inicial: documento disponible en el escenario y lectura cerrada.

Estado final: contenido visualizado y regreso a la exploración al cerrar la lectura.

Recursos utilizados: notas y expedientes; no se consumen.

Recompensa: obtener información sobre el lugar, los experimentos y los personajes.

Penalización: no se especifica una penalización directa.

Interacciones con otras mecánicas: exploración, interacción y narrativa

### Mecánica 04 - Utilizar la linterna y administrar la batería

**Propósito**: iluminar el entorno y hacer que el jugador controle una carga limitada.

**Activación:** utilizar el control de encendido o interactuar con una pila.

**Reglas:**

- La linterna inicia con un 100 % de batería.
- Consume un 0.3 % por segundo mientras está encendida.
- Apagada no consume carga.
- Al llegar al 0 %, deja de iluminar, pero permanece una iluminación ambiental mínima para continuar.
- Hay cuatro pilas distribuidas por el mapa.
- Cada pila recupera un 40 % de carga sin superar el 100 %.
- Las pilas se utilizan inmediatamente; no se almacenan.

**Entrada:**

| Tecla o control | Acción                              |
| --------------- | ------------------------------------ |
| F               | Encender o apagar la linterna        |
| Mouse           | Orientar la luz junto con la cámara |
| E               | Recoger y utilizar una pila          |

**Estado inicial:** linterna encendida o apagada con una carga determinada.

**Estado final:** iluminación y carga actualizadas por consumo o recarga.

**Recompensa:** reconocer caminos, obstáculos y objetos.

**Penalización:** consumo de carga y exposición mediante la iluminación.

**Interacciones con otras mecánicas:** exploración, interacción, detección, HUD y guardado.

**Casos límite:**

- Con carga agotada no puede mantenerse encendida.
- La recarga sobrante se pierde y la pila se consume.
- Agotar la batería no provoca una derrota inmediata.

### Mecánica 05 - Sigilo y utilización de escondites

**Propósito:** evitar la detección mediante la postura, el movimiento y los elementos del entorno.

**Activación:** desplazarse por una zona peligrosa, agacharse o utilizar un escondite.

**Reglas:**

- La criatura mutante responde a señales visuales y sonoras.
- Los obstáculos pueden interrumpir la visión directa.
- Agacharse no vuelve invisible al jugador.
- Los sonidos permiten advertir la cercanía de la amenaza.

**Entrada:**

| Tecla o control | Acción                                         |
| --------------- | ---------------------------------------------- |
| W, A, S, D      | Desplazarse                                    |
| Ctrl izquierdo  | Agacharse o levantarse si hay espacio          |
| Mouse           | Observar la amenaza y las rutas                |
| E               | Utilizar un escondite cuando aparezca el aviso |

**Estado inicial:** jugador expuesto o próximo a la amenaza.

**Estado final:** jugador oculto, desplazándose sin detección o descubierto.

**Recursos utilizados:** obstáculos y escondites.

**Recompensa:** atravesar una zona sin iniciar una persecución.

**Penalización:** una exposición o un ruido detectable puede revelar al jugador.
### Mecánica 03 - Evitar a la criatura y utilizar escondites

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
- La lluvia es constante dificulta orientarse y escuchar a la criatura. Reduce el alcance de sus sentidos en exteriores, por lo que ofrece oportunidades para moverse sin ser detectado.
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
