# Interfaz Visual

## Descripción de la sección

Documenta la información que el juego muestra al jugador y las reglas visuales de la interfaz.

## HUD

Elementos:

- **Objetivo actual:** indica qué debe hacer el jugador y se actualiza conforme avanza.
- **Batería de la linterna:** Muestra la carga disponible y avisa cuando está por agotarse.
- **Indicadores contextuales:** Muestran la tecla E y la acción disponible al observar un objeto interactivo.
- **Confirmación de checkpoint**: Aparece brevemente cuando se guarda el progreso.
- **Indicador de peligro:** Oscurece los bordes de la pantalla según la proximidad o persecución de la criatura mutante. (pendiente)

## Jerarquía visual

¿Qué información debe verse primero, segundo y tercero?

1. **Peligro e interacción:** las señales de amenaza y los avisos de interacción deben reconocerse rápidamente para reaccionar o actuar.
2. **Objetivo actual:** debe permanecer visible y ser fácil de consultar para orientar el avance.
3. **Recursos y confirmaciones:** el nivel de batería y los avisos de checkpoint ocupan un lugar secundario. La alerta de batería baja destaca cuando requiere atención.

## Estados

Documenta estados normales, advertencias, daño, éxito, error y bloqueo.

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
| Derrota                 | Aparece la pantalla de captura con la opción de reintentar.                                                  |
| Partida completada      | Se muestra la pantalla de finalización tras el desenlace.                                                    |

## Convenciones

**Tipografía:** Los expedientes utilizan Courier Prime, Special Elite y Maquina 374 Regular para simular textos mecanografiados; Caveat para anotaciones y Gotham para información complementaria. Las notas emplean Biro Script Plus y Gloria Hallelujah Regular. Los diálogos utilizarán fuentes de estilo manuscrito similar, priorizando la legibilidad.

**Iconografía:** Símbolos sencillos y reconocibles para la batería, la tecla E y el guardado. Mantener el mismo estilo y grosor de línea en todos los iconos.

**Tamaños mínimos:** Pendientes de definir mediante pruebas dentro del juego. Los objetivos, diálogos y documentos deben poder leerse sin acercarse a la pantalla.

**Contraste:** Textos blancos o gris claro sobre fondos oscuros en la interfaz. En notas y expedientes, texto oscuro sobre papel claro; las manchas y el desgaste no deben ocultar información necesaria.

**Animaciones:** Pendientes de definir. Las transiciones y avisos deben ser breves y permitir leer la información sin distraer de la exploración.

## Pantallas

- Menú principal (niciar una partida, continuar el progreso guardado o salir)
- Pantalla de juego con HUD.
- Menú de pausa
- Lectura de notas y expedientes
- Diálogos y opciones de respuesta.
- Victoria
- Derrota
- Finalización de la partida.

> **Navegación:** [[00 - Índice]] · ← [[03 - Entornos]] · [[05 - Audio y Música]] →
