# Interfaz Visual

## HUD

Elementos:

* **Objetivo actual:** Muestra lo que debe hacer el jugador y se actualiza conforme avanza por las distintas zonas.
* **Batería de la linterna:** Indica la carga disponible y advierte cuando está por agotarse.
* **Indicadores contextuales:** Muestran la tecla E y la acción disponible al observar un objeto interactivo.
* **Confirmación de checkpoint:** Aparece brevemente cuando se guarda el progreso.
* **Indicador de peligro:** Oscurece los bordes de la pantalla según la proximidad o persecución de la criatura mutante

## Jerarquía visual

1. **Peligro e interacción:** las señales de amenaza y los avisos de interacción deben reconocerse rápidamente para reaccionar o actuar.
2. **Objetivo actual:** debe permanecer visible y ser fácil de consultar para orientar el avance.
3. **Recursos y confirmaciones:** el nivel de batería y los avisos de checkpoint ocupan un lugar secundario. La alerta de batería baja destaca cuando requiere atención.
4. **Menús y configuración:** Las opciones seleccionadas se distinguen mediante bordes azules, facilitando su identificación durante la navegación.

## Estados

| Estado                  | Representación visual                                                                                        |
| ----------------------- | ------------------------------------------------------------------------------------------------------------- |
| Exploración            | Se muestran el objetivo actual y el indicador de batería.                                                    |
| Interacción disponible | Aparece la tecla E junto con la acción que puede realizarse.                                                 |
| Lectura                 | Se muestra el contenido de la nota o expediente de forma legible.                                             |
| Diálogo                | Se presentan el texto y las opciones de respuesta disponibles.                                                |
| Batería baja           | El indicador advierte que la carga está por agotarse.                                                        |
| Peligro                 | Los bordes de la pantalla se oscurecen según la cercanía o persecución de la criatura mutante. (pendiente) |
| Guardado                | Aparece brevemente la confirmación del checkpoint.                                                           |
| Pausa                   | Se muestra el menú de pausa y se detiene la partida.                                                         |
| Configuración          | Se muestran las categorías Audio, Video y Controles.                                                         |
| Confirmación           | Aparece una ventana para confirmar el inicio de una nueva partida y el reinicio del progreso guardado.        |
| Derrota                 | Aparece la pantalla de captura con la opción de reintentar.                                                  |
| Partida completada      | Se muestra la pantalla de finalización tras el desenlace.                                                    |

## Convenciones

**Tipografía:** Los expedientes utilizan Courier Prime, Special Elite y Maquina 374 Regular para simular textos mecanografiados; Caveat para anotaciones y Gotham para información complementaria. Las notas emplean Biro Script Plus y Gloria Hallelujah Regular. Los diálogos utilizarán fuentes de estilo manuscrito similar, priorizando la legibilidad.

**Iconografía:** Símbolos sencillos y reconocibles para la batería, la tecla E y el guardado. Mantener el mismo estilo y grosor de línea en todos los iconos.

**Tamaños mínimos:** Pendientes de definir mediante pruebas dentro del juego. Los objetivos, diálogos y documentos deben poder leerse sin acercarse a la pantalla.

**Contraste:** Textos blancos o gris claro sobre fondos oscuros en la interfaz. En notas y expedientes, texto oscuro sobre papel claro; las manchas y el desgaste no deben ocultar información necesaria.

**Animaciones:** Pendientes de definir. Las transiciones y avisos deben ser breves y permitir leer la información sin distraer de la exploración.

## Pantallas

### Menú principal

Presenta el título Dark Mutant y incluye las siguientes opciones:

- **Continuar:** Carga la partida guardada y muestra la fecha y hora del último progreso.
- **Jugar:** Permite comenzar una nueva partida.
- **Opciones:** Abre el menú de configuración.
- **Créditos:** Muestra la información del equipo de desarrollo.
- **Salir: C**ierra el videojuego.

### Confirmación de nueva partida

Aparece al seleccionar una nueva partida cuando existe progreso guardado. Advierte que se reiniciará la partida actual y permite elegir entre Cancelar e Iniciar.

### Configuración

Se divide en tres categorías:

| Categoría | Opciones disponibles                                                      |
| ---------- | ------------------------------------------------------------------------- |
| Audio      | Ajustar el volumen general y el ambiente mediante barras deslizantes.    |
| Video      | Seleccionar el modo de pantalla: ventana, sin bordes o pantalla completa. |
| Controles  | Ajustar la sensibilidad de la cámara e invertir el eje vertical.         |

### Pantalla de juego

Muestra el escenario en primera persona junto con el HUD, los objetivos, la batería y los indicadores de interacción.

### Menú de pausa

Permite detener temporalmente la partida, reanudarla, regresar al menú principal o salir del videojuego.

### Lectura de documentos

Presenta las notas, fotografías y expedientes encontrados durante la exploración, conservando su apariencia de documentos físicos.

### Pantalla de derrota

Aparece cuando Vadrik es capturado por la criatura mutante. Permite reintentar desde el último checkpoint, regresar al menú principal o salir.

### Pantalla de finalización

Se presenta después del desenlace de Dark Mutant y permite regresar al menú principal o salir del videojuego.

- **Navegación:**[[00 - Índice]] · ← [[03 - Entornos]] · [[05 - Audio y Música]] →
