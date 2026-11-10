# Motor y Herramientas

## Descripción de la sección

Documenta las herramientas utilizadas para crear el videojuego y por qué fueron seleccionadas.

## Motor

**Motor:** Unity 6.6

**Versión:** 6000.6.4f1

**Renderizado:** Universal Render Pipeline (URP) 17.6.0, con espacio de color lineal. La ambientación nocturna usa un skybox de noche y un volumen de posprocesado (`VP_Mundo`) con mapeo de tonos ACES, ajuste de exposición, viñeta, bloom y grano de película; la cámara aplica antialiasing SMAA.

**Física:** motor de física 3D integrado de Unity (PhysX). El jugador usa el componente Character Controller con gravedad propia de −20 m/s²; los escenarios usan mallas de colisión simplificadas; la interacción y la visión de la criatura usan raycasts, y la criatura se desplaza sobre una malla de navegación (NavMesh).

**Sistema de entrada:** Unity Input System 1.20.0, con el mapa de acciones `PlayerInputActions` dividido en dos grupos: `Movement` (mover, mirar, correr, agacharse, interactuar y linterna) y `Session` (pausa y archivo de notas).

**¿Por qué Unity?** Ofrece un entorno 3D completo con iluminación, física, navegación e interfaz integrados; se programa en C#, lenguaje que el equipo ya conoce; tiene documentación extensa y es gratuito para proyectos académicos.

## Lenguajes

| Lenguaje | Uso |
|---|---|
| C# | Lógica del juego en Unity: movimiento del jugador, interacción, linterna, inteligencia artificial de la criatura, progresión, guardado e interfaz. |
| Python | Scripts para Blender que generan los modelos 3D (cabañas, laboratorio y vegetación), crean sus colisiones, asignan materiales y exportan los archivos FBX. |

## Herramientas

| Área                 | Herramienta           | Uso                                                                                                                      |
| -------------------- | --------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Motor                | Unity 6.6             | Construcción de escenas, iluminación, física, navegación, interfaz y compilación del ejecutable.                         |
| Editor de código     | Visual Studio Code    | Escritura y depuración de los scripts en C#.                                                                             |
| Modelado 3D          | Blender 4.2 LTS       | Modelado de cabañas, laboratorio, vegetación, rocas y objetos, generados mediante scripts de Python y exportados en FBX. |
| Modelado en Unity    | ProBuilder            | Geometría básica y bloqueos de prueba dentro de Unity.                                                                   |
| Texturas             | Poly Haven            | Texturas de terreno con licencia CC0 (dominio público), en resolución 1K.                                                |
| Audio                | FL Studio             | Creación y edición de música ambiental y efectos de sonido, exportados en WAV.                                           |
| Diseño de interfaz   | Figma                 | Diseño y prototipado de menús, HUD y pantallas antes de llevarlos a Unity.                                               |
| Material gráfico     | Canva                 | Presentaciones, imágenes promocionales y material de apoyo.                                                              |
| Control de versiones | Git, Git LFS y GitHub | Historial de cambios, ramas por función, solicitudes de cambio (pull requests) y almacenamiento de archivos pesados.     |
| Gestión de tareas    | GitHub Projects       | Tablero de tareas con estados Pendiente, En progreso y Completado.                                                       |
| Documentación        | Obsidian              | Elaboración y organización del GDD en archivos Markdown enlazados.                                                       |
| Publicación          | Itch.io               | Distribución del ejecutable para Windows.                                                                                |


## Dependencias

Paquetes de Unity instalados mediante el Package Manager. El proyecto no usa plugins ni servicios externos de pago.

| Paquete | Versión | Uso en el proyecto |
|---|---|---|
| Universal Render Pipeline | 17.6.0 | Renderizado, iluminación y posprocesado. |
| Input System | 1.20.0 | Lectura de teclado y mouse mediante acciones. |
| AI Navigation | 2.0.14 | Malla de navegación (NavMesh Surface) y desplazamiento de la criatura (NavMesh Agent). |
| ProBuilder | 6.1.4 | Geometría básica dentro de Unity. |
| uGUI y TextMesh Pro | 2.6.0 | Interfaz: HUD, menús, archivo de notas y textos. |
| Test Framework | 1.8.0 | Pruebas automatizadas del código. |
| Timeline | 6.6.0 | Instalado por la plantilla; no se utiliza actualmente. |
| Visual Scripting | 1.9.12 | Instalado por la plantilla; no se utiliza (toda la lógica está en C#). |

## Convenciones del proyecto

**Estructura de carpetas**

| Carpeta | Contenido |
|---|---|
| `Assets/Scenes` | Escenas `MainMenu` y `Mundo`; `Testing/` para la escena de pruebas. |
| `Assets/Scripts` | Código en C#, dividido en `Player`, `Creature`, `Interaction`, `Core`, `UI` y `Audio`. |
| `Assets/Art/Environment` | `Models` (FBX), `Materials`, `Textures`, `Terrain` y `PostProceso`. |
| `Assets/Prefabs` | `Environment` (`Cabanas`, `Laboratorio`, `Vegetacion`) y `Gameplay` (objetos interactivos). |
| `Assets/Audio` | `Ambient` (lluvia y ambiente). |
| `Assets/UI` | Imágenes de la interfaz: fondos, íconos y marcos. |
| `Testing/` (dentro de cada carpeta) | Recursos de prueba que no forman parte de la versión final. |

**Nomenclatura**

- Archivos y objetos en `Pascal_Case` con guion bajo y sin acentos ni ñ: `Cabana_Jugable.fbx`, `Pino_Alto_1.prefab`, `Roca_Mediana_2.prefab`.
- Variantes numeradas al final: `Pino_Alto_1` a `Pino_Alto_4`.
- Prefijos por tipo: `TD_` datos de terreno, `TL_` capas de terreno, `VP_` volumen de posprocesado, `LIM_` paredes de límite, `MK_` marcadores de posición, `COL_` mallas de colisión, `Bg_` fondos de interfaz e `Icon_` íconos.
- Cada modelo se exporta en archivos separados según su uso: `_Jugable` (lo que se ve), `_Colisiones` (lo que bloquea al jugador), `_Estatica` y `_Props`.

**Control de versiones**

- Ramas: `main` (versiones entregadas), `develop` (integración) y `feature/<tarea>` para cada función, por ejemplo `feature/entorno-mundo`.
- Los cambios entran a `develop` mediante pull request revisado por el dueño del repositorio.
- Mensajes de commit con el formato `tipo(área): descripción`, por ejemplo `feat(progression): conecta objetivos de la segunda cabana`.
- Una escena tiene un solo responsable a la vez; el equipo se avisa antes de editar `Mundo` para evitar conflictos.
- Git LFS almacena los archivos pesados: modelos (`.fbx`, `.blend`), imágenes, audio, video, fuentes, los datos del terreno y el NavMesh.
- Siempre se sube el archivo `.meta` de cada archivo o carpeta nueva.

**Formato de assets**

- Escala: 1 unidad = 1 metro en Blender y en Unity.
- Modelos en FBX, con el origen en la base del objeto (o en la bisagra, en las puertas). Al importar: Bake Axis Conversion activado, sin rig ni animación, y Generate Colliders solo en el FBX de colisiones.
- Texturas en PNG o JPG a 1K; audio en WAV.
- Límites de triángulos: pinos altos hasta 3,300, árboles secos hasta 1,800 y rocas cerca de 320.

**Convenciones de código**

- Todos los scripts usan el espacio de nombres `DarkMutant`.
- Clases y métodos en `PascalCase` (`PlayerMotor`, `TryToggle`); variables privadas en `camelCase`.
- Los valores ajustables se exponen en el Inspector con `[SerializeField] private` en lugar de hacerlos públicos o escribirlos fijos en el código.
- Los sistemas se comunican mediante eventos de C# (`event Action`) para reducir dependencias.
- Comentarios de documentación con `/// <summary>` en español.

> **Navegación:** [[00 - Índice]] · ← [[01 - Arquitectura Técnica]] · [[03 - Requisitos Técnicos]] →