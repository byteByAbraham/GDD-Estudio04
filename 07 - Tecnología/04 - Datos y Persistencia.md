# Datos y Persistencia

## Descripción de la sección

Define qué información necesita conservar el juego y cómo se estructura.

## Datos persistentes

* **Progreso:** Último checkpoint alcanzado y objetivo actual de la partida.
* **Configuración:** No se contempla el almacenamiento de configuraciones personalizadas.
* **Inventario:** No se incluye un sistema de inventario.
* **Estadísticas:** No se contempla el almacenamiento de estadísticas del jugador.
* **Desbloqueos:** Accesos habilitados y generadores activados durante el recorrido.
* **Otros:** Carga restante de la linterna y decisiones de diálogo registrada

## Modelo de datos

El modelo de datos de Dark Mutant se organiza alrededor del progreso del jugador y los elementos necesarios para continuar la partida. No se contempla el uso de una base de datos externa, ya que el videojuego funciona sin conexión a Internet.

## Formato

**Formato de guardado:**

**Ubicación:**

**Versionado de datos:**

abraham sabw

## Migraciones

¿Qué ocurre si cambia la estructura de los datos entre versiones?

No se contemplan migraciones de datos entre versiones, ya que el videojuego utilizará un sistema de guardado local con una única partida y no se prevén actualizaciones que requieran modificar la estructura de los datos guardados.

> **Navegación:** [[00 - Índice]] · ← [[03 - Requisitos Técnicos]] · [[05 - Seguridad y Riesgos Técnicos]] →
