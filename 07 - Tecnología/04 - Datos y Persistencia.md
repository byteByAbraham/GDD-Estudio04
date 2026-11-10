# Datos y Persistencia

## Descripción de la sección

Define qué información necesita conservar el juego y cómo se estructura.

## Datos persistentes

* **Progreso:** escena, posición y orientación del jugador en el último punto guardado, objetivo actual en pantalla y banderas de progreso (objetos recogidos, puertas desbloqueadas y abiertas, generadores encendidos y objetivos completados).
* **Configuración:** volumen general, volumen de ambiente, volumen de voces, sensibilidad del mouse, invertir eje Y, subtítulos, tamaño de texto, efectos reducidos, modo de pantalla, calidad gráfica y sincronización vertical (VSync).
* **Inventario:** llaves y notas obtenidas, con su título y contenido, para consultarlas en el archivo de notas y llaves.
* **Estadísticas:** no se guardan estadísticas del jugador (tiempo de juego, capturas u otras).
* **Desbloqueos:** puertas abiertas y generadores encendidos, registrados como banderas de progreso.
* **Otros:** carga de la batería de la linterna y fecha y hora del guardado, que se muestra en el menú principal al continuar.

## Modelo de datos

El juego no usa una base de datos ni servicios en línea: toda la información se guarda en archivos locales del equipo del jugador. Los datos se dividen en dos grupos independientes: la **partida guardada** y la **configuración**. Así, borrar la partida al iniciar una nueva no reinicia las opciones del jugador.

Durante la partida, el progreso vive en memoria en la clase `GameProgress`. Cuando el jugador llega a un checkpoint o guarda desde el menú de pausa, `CheckpointManager` toma una copia del progreso y `SaveSystem` la escribe en disco.

**Partida guardada (`SaveData`)**

| Campo | Tipo | Contenido |
|---|---|---|
| `version` | Entero | Versión de la estructura del guardado (actualmente 1). |
| `scene` | Texto | Escena donde se guardó (`Mundo`). |
| `savedAtUtc` | Texto | Fecha y hora del guardado en formato ISO 8601 (UTC). |
| `px`, `py`, `pz` | Decimal | Posición del jugador en metros. |
| `yaw` | Decimal | Hacia dónde mira el jugador, en grados. |
| `battery` | Decimal | Batería de la linterna, de 0 a 100 %. |
| `objective` | Texto | Objetivo mostrado en pantalla. |
| `flags` | Lista de texto | Banderas de progreso, por ejemplo `pickup:<id>`, `door.unlocked:<id>` y `door.open:<id>`. |
| `notes` | Lista de entradas | Notas obtenidas (identificador, título y contenido). |
| `keys` | Lista de entradas | Llaves obtenidas (identificador, título y descripción). |

**Configuración (`GameSettings`)**

Cada opción se guarda con el prefijo `dm.settings.`, por ejemplo `dm.settings.master` o `dm.settings.subtitles`. Si no existe un valor guardado, se usa el valor por defecto: volumen general 100 %, ambiente 80 %, voces 100 %, sensibilidad 1.0, subtítulos activados, texto normal, modo de pantalla sin bordes y VSync desactivado.

## Cuándo se guarda

| Momento | Qué se guarda | Cómo |
|---|---|---|
| Al pasar por un checkpoint | La partida completa, con la posición del checkpoint | Automático |
| Desde el menú de pausa (Guardar) | La partida completa, con la posición actual del jugador | Manual |
| Al cambiar una opción en Configuración | Las opciones del jugador | Automático |
| Al elegir Nueva partida | Se borra la partida guardada (la configuración se conserva) | Automático |

## Formato

**Formato de guardado:** la partida se guarda en un archivo de texto JSON legible, generado con `JsonUtility` de Unity (`darkmutant_save.json`). La configuración se guarda con `PlayerPrefs`, el sistema de preferencias de Unity.

**Ubicación:**

* Partida: carpeta `Application.persistentDataPath`, que en Windows corresponde a `C:\Users\<usuario>\AppData\LocalLow\<Compañía>\<Producto>\`.
* Configuración: registro de Windows, en `HKEY_CURRENT_USER\Software\<Compañía>\<Producto>`.

`<Compañía>` y `<Producto>` son los nombres definidos en *Project Settings → Player*.

**Versionado de datos:** cada archivo de guardado incluye el campo `version`. Al cargar, el juego comprueba que coincida con la versión actual (`CurrentVersion = 1`); si no coincide, la partida no se carga.

**Protección contra errores:**

* El juego primero escribe un archivo temporal (`.tmp`) y luego reemplaza el guardado anterior, para no dejar un archivo a medias si el juego se cierra mientras guarda.
* Antes de reemplazar el guardado, conserva una copia de respaldo (`.bak`). Si el archivo principal está dañado, carga el respaldo.
* Al cargar, valida que los datos tengan sentido: versión correcta, escena válida y posición y batería con valores numéricos reales. La batería se limita al rango de 0 a 100 %.
* Si el guardado falla, se conserva el último guardado válido y en pantalla aparece el mensaje «No se pudo guardar la partida».

## Migraciones

¿Qué ocurre si cambia la estructura de los datos entre versiones?

No se programan migraciones automáticas: como el juego tiene una sola partida corta, de 30 a 35 minutos, no se justifica convertir guardados antiguos. Si en una versión futura cambia la estructura del guardado, se incrementa `CurrentVersion`, y los guardados con la versión anterior se rechazan de forma segura: el juego no los carga y el jugador inicia una nueva partida. La configuración no se ve afectada, porque se guarda por separado.

> **Navegación:** [[00 - Índice]] · ← [[03 - Requisitos Técnicos]] · [[05 - Seguridad y Riesgos Técnicos]] →