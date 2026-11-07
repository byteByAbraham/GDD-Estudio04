# Reglas y Estados del Juego

## Descripción de la sección

Define las reglas globales y los estados que puede atravesar el videojuego.

## Estados principales

| **Estado** | **Descripción**                                                                                          |
| ---------------- | --------------------------------------------------------------------------------------------------------------- |
| Menú principal  | Pantalla desde la que se puede iniciar una partida, continuar una guardada, o salir del juego.                  |
| Carga            | Prepara el escenario y los datos necesarios para iniciar la partida o regresar al último checkpoint.           |
| Jugando          | El jugador controla a Vadrik, explora, interactúa con objetos y cumple objetivos mientras evita los peligros.  |
| Pausa            | Detiene temporalmente la partida y permite reanudarla o volver al menú principal.                              |
| Victoria         | Se alcanza al completar la secuencia final del laboratorio y descubrir la verdad sobre Jereth.                  |
| Derrota          | Se activa cuando la criatura mutante atrapa a Vadrik y se reproduce la secuencia de muerte.                     |
| Game Over        | Pantalla posterior a la derrota que permite reintentar desde el último checkpoint o volver al menú principal. |
| Créditos        | Presenta a los integrantes del equipo y los recursos utilizados al finalizar el juego.                          |

## Transiciones

| Estado origen  | Evento                                    | Estado destino | Condición                                         |
| -------------- | ----------------------------------------- | -------------- | ------------------------------------------------- |
| Menú principal | Seleccionar «Nueva partida» o «Continuar» | Carga          | Para continuar, debe existir una partida guardada |
| Carga          | Terminar de cargar el escenario           | Jugando        | El escenario y el personaje están listos          |
| Jugando        | Presiona el botón de pausa **[ESC]**      | Pausa          | El jugador solicita congelar la partida           |
| Pausa          | Selecciona renaudar                       | Jugar          | La partida está pausada                           |
| Pausa          | Selecciona volver al menú                 | Menú principal | El jugador confirma que desea salir de la sesión  |
| Jugando        | Ser atrapado por la criatura mutante      | Derrota        | Vadrik muere                                      |
| Derrota        | Finalizar la secuencia de muerte          | Game Over      | Se muestran las opciones para reintentar o salir  |
| Game Over      | Seleccionar Reintentar                    | Carga          | Se recupera el último checkpoint                  |
| Game Over      | Seleccionar Volver al menú                | Menú principal | El jugador decide abandonar la partida            |
| Jugando        | Completa objetivo final                   | Victoria       | Se descubre la verdad sobre Jereth                |
| Victoria       | Seleccionar Volver al menú                | Créditos       | La historia ha concluido                          |
| Créditos       | Volver                                    | Menú principal | Finaliza la presentación de créditos              |

## Reglas globales

1. La progresión sigue un orden lineal, desde la primera cabaña hasta el interior del laboratorio.
2. Cada llave permite abrir únicamente su acceso correspondiente.
3. Entrar a una cabaña activa un checkpoint y guarda el progreso.
4. Ser atrapado por la criatura mutante provoca la derrota y permite reiniciar desde el último checkpoint.
5. Vadrik no puede combatir ni utilizar armas; debe evitar el peligro, esconderse o huir.
6. La batería de la linterna se consume únicamente mientras está encendida y se recupera mediante las pilas disponibles.
7. La entrada al laboratorio se habilita después de activar los dos generadores del exterior.
8. Los objetivos se actualizan conforme se completan las acciones necesarias para avanzar.
9. Las respuestas elegidas en los diálogos no cambian el rumbo ni el final de la historia.
10. Los accesos abiertos permanecen disponibles durante el recorrido.

## Casos especiales

Documenta excepciones importantes para evitar interpretaciones diferentes durante la implementación.

1. Si se recoge una pila con la batería casi llena, la carga llega hasta el 100 % y el sobrante se pierde; la pila se consume.
2. Si la batería llega al 0 %, la linterna se apaga, pero permanece una iluminación ambiental mínima para continuar.
3. Si el jugador muere antes de alcanzar otro checkpoint, reaparece en el último registrado con al menos un 30 % de batería.
4. Si el jugador pausa durante una persecución, la amenaza se detiene y continúa desde el mismo punto al reanudar.
