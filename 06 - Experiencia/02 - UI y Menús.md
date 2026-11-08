# UI y Menús

## Descripción de la sección

Define la estructura funcional de las interfaces y menús.

## Mapa de navegación

```text
Menú principal
├── Nueva partida
├── Continuar
└── Salir

Durante la partida → Pausa
├── Reanudar
├── Volver al menú principal
└── Salir

Después de la derrota
├── Reintentar 
├── Volver al menú principal
└── Salir

Después de la victoria
├── Volver al menú principal
└── Salir
```



## Pantallas

### Menú principal

**Propósito: Propósito:** Permitir el acceso al juego. 

**Elementos:** Título del juego, botones Jugar y  Salir.

**Acciones disponibles:** Iniciar la partida, reanudar partida  o cerrar el juego.

### Diálogos

**Propósito:** Presentar conversaciones y opciones de respuesta.

**Elementos:** Texto del diálogo y respuestas disponibles.

**Acciones disponibles:** Avanzar el texto y seleccionar una respuesta.

### Pausa

**Propósito:** Detener temporalmente la partida.

**Elementos:** Botones Reanudar, Reiniciar y Volver al menú.

**Acciones disponibles:** Continuar jugando, reiniciar desde el último checkpoint o regresar al menú principal.

### Derrota

**Propósito:** Comunicar la captura y permitir otro intento.

**Elementos:** Mensaje de derrota y botones Reintentar y Volver al menú.

**Acciones disponibles:** Reintentar desde el último checkpoint o regresar al menú principal.

### Finalización / Victoria

**Propósito:** Confirmar que el jugador completó el recorrido y el desenlace.

**Elementos:** Mensaje de finalización y botones Volver al menú y Salir.

**Acciones disponibles:** Regresar al menú principal o cerrar el juego.


### Confirmaciones

Documenta acciones destructivas o irreversibles y cómo se confirman.

| Acción                             | Mensaje de confirmación                                                             | Opciones                  |
| ---------------------------------- | ----------------------------------------------------------------------------------- | ------------------------- |
| Reiniciar desde el checkpoint      | «¿Reiniciar desde el último checkpoint? Perderás el avance posterior al guardado».  | Reiniciar / Cancelar      |
| Volver al menú durante la partida  | «¿Volver al menú principal? El progreso posterior al último checkpoint se perderá». | Volver al menú / Cancelar |
| Cerrar el juego durante la partida | «¿Salir del juego? El progreso posterior al último checkpoint se perderá».          | Salir / Cancelar          |

> **Navegación:** [[00 - Índice]] · ← [[01 - UX y Flujo del Jugador]] · [[03 - Accesibilidad]] →
