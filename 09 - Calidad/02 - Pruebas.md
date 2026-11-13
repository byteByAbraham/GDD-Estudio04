# Pruebas

## Tipos de prueba

### Pruebas funcionales

Se comprobó que el movimiento en primera persona, el sigilo, la linterna, el inventario, las interacciones y el comportamiento de la criatura mutante funcionen según lo establecido en el GDD. También se verificó la apertura de puertas, la activación de generadores, el panel numérico y los checkpoints.

### Pruebas de integración

Se comprobó que los sistemas funcionen correctamente entre sí. Por ejemplo, que las llaves recolectadas puedan utilizarse para abrir puertas, que los fusibles del inventario permitan activar los generadores y que el código encontrado en la tercera cabaña desbloquee el acceso al laboratorio

### Pruebas de usabilidad

Se comprobó que el jugador comprenda los objetivos mostrados en pantalla, identifique los objetos interactivos, utilice el inventario y pueda avanzar mediante la exploración y las pistas. También permiten evaluar si las señales de peligro de la criatura mutante son comprensible

### Pruebas de rendimiento

Se comprobó que el videojuego mantenga un rendimiento estable en PC, tomando como referencia los 60 FPS establecidos. Se revisará el consumo de memoria, los tiempos de carga y la estabilidad durante la exploración del bosque, las persecuciones y el acceso al laboratorio.

## Caso de prueba

### CP01 — Inicio de partida

**Objetivo:** Comprobar que el menú principal permita iniciar una nueva partida y presentar el storyboard introductorio del videojuego.

**Precondiciones:** Ejecutar Dark Mutant desde el menú principal.

**Pasos:**

1. Seleccionar la opción «Nueva partida».
2. Comprobar que se presente el storyboard introductorio.
3. Esperar a que termine la introducción.
4. Verificar que Vadrik aparezca dentro de la primera cabaña.

**Resultado esperado:** El storyboard introductorio se presenta correctamente y el jugador comienza dentro de la primera cabaña con el control del personaje habilitado.

**Resultado obtenido:** El storyboard se presentó correctamente y, al finalizar, Vadrik apareció dentro de la primera cabaña con los controles habilitados.

**Estado:** Correcto.

### CP02 — Movimiento y controles

**Objetivo:** Verificar el funcionamiento del movimiento en primera persona.

**Precondiciones:** Haber iniciado la partida y tener el control de Vadrik.

**Pasos:**

1. Utilizar W, A, S y D para desplazarse.
2. Mover el mouse para controlar la cámara.
3. Mantener Shift izquierdo para correr.
4. Presionar la tecla C para agacharse.
5. Intentar desplazarse contra paredes y objetos sólidos.

**Resultado esperado:** Vadrik responde correctamente a los controles y no atraviesa los obstáculos del escenario.

**Resultado obtenido:** El personaje respondió a las teclas de movimiento, pudo correr y agacharse, y la cámara siguió los movimientos del mouse. No atravesó paredes ni obstáculos.

**Estado:** Correcto.

### CP03 — Linterna y batería

**Objetivo:** Comprobar el funcionamiento de la linterna y su consumo de batería.

**Precondiciones:** El jugador debe tener la linterna disponible.

**Pasos:**

1. Encender la linterna.
2. Mantenerla encendida para observar el consumo de batería.
3. Apagarla y comprobar que deje de consumir energía.
4. Recoger una pila disponible en el escenario.
5. Verificar que se recargue la batería.

**Resultado esperado:** La linterna ilumina el entorno, consume batería mientras está encendida y recupera energía al recoger pilas.

**Resultado obtenido:** La linterna iluminó correctamente, la batería disminuyó durante su uso y dejó de consumirse al apagarla. Al recoger una pila, el nivel de batería aumentó.

**Estado:** Correcto.

### CP04 — Exploración del bosque y criatura mutante

**Objetivo:** Verificar el comportamiento de la criatura mutante y las mecánicas de sigilo.

**Precondiciones:** Haber salido de la primera cabaña y encontrarse en el bosque.

**Pasos:**

1. Recorrer los caminos del bosque.
2. Observar el patrullaje de la criatura mutante.
3. Acercarse a su zona de detección.
4. Comprobar que inicie la persecución al detectar al jugador.
5. Correr y utilizar un escondite para evitar la captura.
6. Observar su comportamiento cuando pierde de vista al jugador.

**Resultado esperado:** La criatura mutante patrulla, detecta y persigue al jugador, y pasa a buscarlo cuando pierde su rastro. El jugador puede evitar la captura mediante el sigilo y los escondites.

**Resultado obtenido:** La criatura mutante realizó su patrullaje, detectó al jugador e inició la persecución. Al esconderse, el jugador evitó la captura y la criatura mutante comenzó a buscarlo.

**Estado:** Correcto.

### CP05 — Captura y reintento

**Objetivo:** Comprobar que la captura del jugador active la derrota y permita recuperar el progreso.

**Precondiciones:** Tener un checkpoint registrado y encontrarse en una zona donde aparezca la criatura mutante.

**Pasos:**

1. Permitir que la criatura mutante detecte a Vadrik.
2. No escapar de la persecución.
3. Esperar a que ocurra la captura.
4. Comprobar que aparezca la pantalla de derrota.
5. Seleccionar «Reintentar».

**Resultado esperado:** El jugador regresa al último checkpoint con el progreso correspondiente a ese punto de guardado.

**Resultado obtenido:** La captura activó la pantalla de derrota y, al seleccionar «Reintentar», el jugador regresó al último checkpoint con el progreso guardado.

**Estado:** Correcto.

### CP06 — Guardado y continuación

**Objetivo:** Verificar que el sistema de checkpoints permita continuar una partida después de salir del juego.

**Precondiciones:** Haber alcanzado al menos un checkpoint.

Pasos:

1. Avanzar hasta un punto de control.
2. Comprobar que el progreso se guarde.
3. Regresar al menú principal.
4. Seleccionar «Continuar».
5. Revisar la ubicación, el inventario, la batería y los objetivos.

**Resultado esperado:** La partida se recupera desde el último checkpoint con los objetos, la batería y los objetivos correspondientes al progreso guardado.

**Resultado obtenido:** La opción «Continuar» cargó el último checkpoint y restauró correctamente la ubicación, los objetos recolectados, la batería y los objetivos registrados.

**Estado:** Correcto.
