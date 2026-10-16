# Reglas y Estados del Juego

## Descripción de la sección

Define las reglas globales y los estados que puede atravesar el videojuego.

## Estados principales

- Menú principal
- Carga
- Jugando
- Pausa
- Victoria
- Derrota
- Game Over
- Créditos

## Transiciones

| Estado origen  | Evento                         | Estado destino | Condición                               |
| -------------- | ------------------------------ | -------------- | --------------------------------------- |
| Menú principal | Selecciona una nueva partida   | Carga          | El jugador presiona botón de inicio     |
| Carga          | Finaliza la carga              | Jugador        | El mapa y la escena estan               |
| Jugando        | Presiona tecla ESC             | Pausa          | El jugador solicita congelar la partida |
| Pausa          | Selecciona renaudar            | Jugar          | El jugador cierra el menú de pausa      |
| Jugador        | La vida del jugador llega a  0 | Game over      | Se activa la pantalla de que perdió     |
| Jugador        | Completa objetivo final        | Victoria       | Se activa la escena final de resolución |
| Victoria       | Presiona continual             | Créditos       | Finalización de juego                   |

## Reglas globales

1. Gestión de Recursos en Tiempo Real: El tiempo de descarga de la linterna avanza únicamente mientras el juego esté en estado jugando 
2. Persistencia entre Escenas: Las baterías acumuladas e ítems del inventario se mantienen al cambiar de área
3. Condición de Muerte : Si el jugador muere derrota, no hay regeneración automática; debe reiniciar desde el último punto

## Casos especiales

Documenta excepciones importantes para evitar interpretaciones diferentes durante la implementación.

 1. Agotamiento de Batería durante Eventos: Si la batería se agota mientras el jugador está interactuando con un objeto o puzle, la linterna se apagará inmediatamente sin pausar el evento.
    
2.  Transición de Pausa: Entrar al estado de **Pausa** congela completamente el temporizador del consumo de la batería de la linterna

> **Navegación:** [[00 - Índice]] · ← [[06 - Economía y Recursos]] · [[01 - Premisa y Trama]] →
