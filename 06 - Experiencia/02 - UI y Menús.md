# UI y Menús

## Mapa de navegación

```text
Menú principal
├── Jugar
│   └── Confirmación de nueva partida
├── Continuar
├── Opciones
│   ├── Audio
│   ├── Video
│   └── Controles
├── Créditos
└── Salir

Durante la partida
├── Inventario
│   ├── Linterna
│   ├── Llaves
│   └── Fusibles
└── Menú de pausa
    ├── Reanudar
    ├── Reiniciar desde el checkpoint
    ├── Volver al menú principal
    └── Salir

Pantalla de derrota
├── Reintentar desde el último checkpoint
├── Volver al menú principal
└── Salir

Pantalla final
├── Volver al menú principal
└── Salir
```

## Pantallas

### Menú principal

**Propósito: Propósito:** Permitir el acceso a las funciones principales del videojuego.

**Elementos:** Título Dark Mutant y opciones Jugar, Continuar, Opciones, Créditos y Salir.

**Acciones disponibles:** Iniciar una nueva partida, continuar una partida guardada, acceder a la configuración, consultar los créditos o cerrar el jueg

### Configuración

**Propósito:** Permitir al jugador modificar los ajustes de audio, video y controles.

**Elementos:** Secciones Audio, Video y Controles, con sus respectivas opciones de ajuste.

**Acciones disponibles:**

- **Audio:** Ajustar el volumen general y los sonidos ambientales.
- **Video:** Seleccionar el modo de pantalla.
- **Controles:** Ajustar la sensibilidad del mouse e invertir el eje vertical.
- **Restablecer:** Recuperar los valores predeterminados.
- 

### Créditos

**Propósito:** Mostrar a los integrantes que participaron en el desarrollo de Dark Mutant.

**Elementos:** Nombres de los integrantes y sus funciones dentro del proyecto.

**Acciones disponibles:** Consultar los créditos y regresar al menú principal.

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

| Acción                                     | Mensaje de confirmación                                                                  | Opciones                   |
| ------------------------------------------- | ----------------------------------------------------------------------------------------- | -------------------------- |
| Iniciar nueva partida con progreso guardado | «Se reiniciará el progreso guardado actual. ¿Deseas continuar?»                       | Iniciar / Cancelar         |
| Reiniciar desde el checkpoint               | «¿Reiniciar desde el último checkpoint? Perderás el avance posterior al guardado».   | Reiniciar / Cancelar       |
| Volver al menú durante la partida          | «¿Volver al menú principal? El progreso posterior al último checkpoint se perderá». | Volver al menú / Cancelar |
| Cerrar el juego durante la partida          | «¿Salir del juego? El progreso posterior al último checkpoint se perderá».           | Salir / Cancelar           |
