# Personajes y Animación

## Descripción de la sección

Documenta cómo deben verse y comportarse visualmente los personajes.

## Requisitos por personaje

| Personaje | Modelo | Animaciones | VFX | Estado |
|---|---|---|---|---|
| Vadrik Dsang | Sin modelo visible: el juego es en primera persona y la cámara representa sus ojos, a 1.8 m de altura (1.1 m agachado). | Movimiento de cámara al caminar, correr y agacharse. | Haz de la linterna; viñeta de miedo en pantalla cuando la criatura está cerca. | Implementado |
| Jereth Dsang — niño humano | Modelo 3D estilizado de un niño (unos 1.3 m), con chaqueta gris verdosa con capucha, pantalón gris oscuro y tenis marrones. | Idle (de pie, quieto) para la alucinación de la fogata. | Aparición y desaparición con un fundido, para reforzar que es una alucinación. | Pendiente |
| Jereth Dsang — criatura mutante | Modelo 3D estilizado: cuerpo delgado y encorvado, extremidades largas, varios ojos asimétricos, dientes afilados y garras. Rig de Mixamo. | Idle, caminar, buscar, correr, ataque (captura) y jumpscare. | Ninguno; su presencia se comunica con sonido. | Pendiente |
| Dr. Cooper | Modelo 3D estilizado de un hombre mayor, canoso, con lentes y bata manchada de sangre. Rig de Mixamo. | Pose herida (sentado o recostado) y muerte. | Ninguno. | Pendiente |

## Animaciones

Todas las animaciones de personajes se obtienen de **Mixamo** y se aplican a modelos propios. Vadrik no tiene animaciones de cuerpo porque no se ve.

### Movimiento

| Personaje | Animación | Cuándo se usa |
|---|---|---|
| Criatura | Idle | Espera en un punto de patrulla (2 s) |
| Criatura | Caminar | Estado de patrulla e investigación |
| Criatura | Buscar (mirar alrededor) | Estado de búsqueda (6 s) e investigación (4 s) |
| Criatura | Correr | Estado de persecución |
| Jereth humano | Idle | Alucinación de la fogata |
| Vadrik (cámara) | Balanceo suave | Al caminar y correr; menor al estar agachado |

La velocidad de las animaciones de caminar y correr debe coincidir con la velocidad del NavMesh Agent de la criatura para que no parezca que se desliza.

### Interacción

Vadrik no tiene manos visibles, por lo que las interacciones se muestran con animaciones de los objetos:

| Objeto | Animación |
|---|---|
| Puertas | Giran sobre su bisagra hasta 95° |
| Palanca del generador | Baja al activarse |
| Fusible | Aparece colocado en la caja de fusibles |
| Escondite | La cámara se mueve a la posición interior |

### Combate

No aplica: el juego no tiene combate.

### Daño

No aplica: Vadrik no tiene barra de vida ni recibe daño gradual.

### Muerte / derrota

| Situación | Animación |
|---|---|
| Captura | La criatura reproduce la animación de ataque frente a la cámara y aparece la pantalla de captura |
| Muerte del Dr. Cooper | Tras la conversación, pasa de la pose herida a la animación de muerte |
| Jumpscare final | La criatura aparece detrás de Vadrik con la animación de ataque, seguida de un fundido a los créditos |

## Convenciones

| Elemento | Convención |
|---|---|
| Flujo de trabajo | Modelo en Blender en pose T, sin rig → exportar FBX → subir a Mixamo para el rig automático → descargar el personaje y sus animaciones → importar en Unity |
| Descarga de Mixamo | Personaje: FBX for Unity, *With Skin*. Animaciones: FBX for Unity, *Without Skin*, 30 fps; las de desplazamiento con *In Place* activado |
| Rig en Unity | Humanoid, para compartir animaciones entre la criatura y el Dr. Cooper |
| Controlador | Un Animator Controller por personaje; los estados de la criatura corresponden a los de `CreatureAI` (patrulla, investigación, persecución, búsqueda y captura) |
| Nombres de archivo | `Personaje_Criatura.fbx`, `Personaje_Jereth.fbx`, `Personaje_Cooper.fbx`; animaciones `Anim_Criatura_Caminar.fbx`, `Anim_Criatura_Correr.fbx`, etc. |
| Carpeta | `Assets/Art/Characters/<Personaje>/` (modelos, materiales, texturas y animaciones) |
| Escala | 1 unidad = 1 metro. Altura del niño unos 1.3 m y del Dr. Cooper unos 1.75 m. La criatura encorvada no debe superar 1.9 m, para pasar por las puertas |
| Geometría | Hasta 10,000 triángulos por personaje |
| Texturas | 1K o 2K, con el mismo estilo estilizado y desgastado del resto del juego (ver [[01 - Dirección de Arte]]) |

> **Navegación:** [[00 - Índice]] · ← [[01 - Dirección de Arte]] · [[03 - Entornos]] →