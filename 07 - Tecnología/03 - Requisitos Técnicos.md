# Requisitos Técnicos

## Descripción de la sección

Define las condiciones técnicas necesarias para ejecutar y desarrollar el videojuego.

## Requisitos mínimos

| Componente | Requisito mínimo |
|---|---|
| Sistema operativo | Windows 10 de 64 bits |
| CPU | Intel Core i5-4460 o AMD Ryzen 3 1200 |
| GPU | NVIDIA GeForce GTX 960 (2 GB) o AMD Radeon RX 460 (2 GB), compatible con DirectX 11 |
| RAM | 8 GB |
| Almacenamiento | 2 GB de espacio disponible |
| Resolución | 1280 × 720 píxeles (HD) |
| Rendimiento | 30 FPS con calidad gráfica baja |
| Conexión | No requiere conexión a Internet |

## Requisitos recomendados

| Componente | Requisito recomendado |
|---|---|
| Sistema operativo | Windows 10 u 11 de 64 bits |
| CPU | Intel Core i5-10400 o AMD Ryzen 5 3600 |
| GPU | NVIDIA GeForce GTX 1660 Super (6 GB) o AMD Radeon RX 5600 XT (6 GB) |
| RAM | 16 GB |
| Almacenamiento | 2 GB de espacio disponible en SSD |
| Resolución | 1920 × 1080 píxeles (Full HD) |
| Rendimiento | 60 FPS con calidad gráfica alta |
| Conexión | No requiere conexión a Internet |

## Requisitos de desarrollo

Equipo y software necesarios para abrir y modificar el proyecto.

| Elemento | Requisito |
|---|---|
| Equipo | Procesador Intel Core i5/i7 o AMD Ryzen 5/7, de 8 a 16 GB de RAM, SSD y tarjeta gráfica dedicada |
| Motor | Unity 6000.6.4f1 (misma versión para todo el equipo) |
| Modelado | Blender 4.2 LTS |
| Código | Visual Studio Code con la extensión de C# |
| Control de versiones | Git y Git LFS instalados antes de clonar el repositorio; sin Git LFS, los modelos, texturas y audios se descargan como archivos vacíos |
| Audio | FL Studio |

## Objetivos de rendimiento

**FPS objetivo:** 60 FPS a 1920 × 1080 píxeles en el equipo recomendado, y 30 FPS a 1280 × 720 píxeles en el equipo mínimo.

**Tiempo de carga objetivo:** máximo 15 segundos para iniciar la partida desde el menú y 5 segundos para reaparecer en un checkpoint.

**Memoria máxima:** 4 GB de RAM durante la partida, para que el juego funcione en equipos de 8 GB junto con el sistema operativo.

**Límites de geometría:** la escena `Mundo` ronda 1.1 millones de triángulos visibles. Para no superarlo, cada modelo tiene un límite (pinos altos hasta 3,300 triángulos, árboles secos hasta 1,800 y rocas cerca de 320), y los árboles usan LOD Group para dejar de dibujarse a unos 80 m de la cámara.

## Configuración de la compilación

| Elemento | Valor |
|---|---|
| Plataforma | Windows de 64 bits (x86_64) |
| Nombre del producto | Dark Mutant |
| Versión | 0.1.0 (se incrementa con cada entrega) |
| Escenas incluidas | `MainMenu` y `Mundo` |
| Modo de pantalla | Pantalla completa por defecto; se puede cambiar desde Configuración |
| Opciones gráficas para el jugador | Calidad, modo de pantalla y sincronización vertical (VSync) |

## Restricciones

* **Plataforma:** el videojuego solo estará disponible para PC con Windows de 64 bits.
* **Rendimiento:** el objetivo es 60 FPS a 1920 × 1080 píxeles; en equipos con menos capacidad, el jugador puede bajar la calidad gráfica desde Configuración.
* **Hardware:** se requiere una tarjeta gráfica compatible con DirectX 11; no se garantiza el funcionamiento con gráficos integrados antiguos.
* **Controles:** solo teclado y mouse, sin soporte para mandos ni reasignación de teclas.
* **Conectividad:** el videojuego funciona sin conexión a Internet y no incluye funciones en línea.
* **Jugabilidad:** la experiencia es individual, con progresión lineal y una duración estimada de 30 a 35 minutos.
* **Guardado:** el progreso se guarda automáticamente en checkpoints, con una sola partida guardada y sin ranuras adicionales.
* **Gráficos:** la calidad de los modelos, texturas, iluminación y efectos depende de los objetivos de rendimiento.
* **Compatibilidad:** no habrá versión para dispositivos móviles ni consolas.

> **Navegación:** [[00 - Índice]] · ← [[02 - Motor y Herramientas]] · [[04 - Datos y Persistencia]] →