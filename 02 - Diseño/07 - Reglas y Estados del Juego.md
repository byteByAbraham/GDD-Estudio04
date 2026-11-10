# Reglas y Estados del Juego

## Descripción de la sección

Define las reglas globales y los estados que puede atravesar el videojuego.

## Estados principales

| Estado | Descripción |
|---|---|
| Menú principal | Primera pantalla del juego. Desde aquí el jugador comienza una nueva partida, retoma la que tiene guardada, ajusta la configuración, consulta los créditos o cierra el juego. |
| Configuración | Reúne las opciones de audio, controles (sensibilidad del mouse e invertir eje Y), video y accesibilidad. Puede abrirse tanto desde el menú principal como desde la pausa. |
| Carga | Mientras la pantalla se funde a negro, el juego prepara la escena `Mundo` y los datos de la partida, ya sea nueva o desde el último checkpoint. |
| Introducción | Solo aparece en una partida nueva: un texto breve cuenta cómo Vadrik terminó confiando en el Dr. Cooper. |
| Jugando | Estado normal de la partida. El jugador controla a Vadrik, recorre el bosque y las cabañas, usa objetos y avanza en sus objetivos mientras se mantiene lejos de la criatura. |
| Lectura | Se activa cuando hay una ventana abierta sobre el juego: un documento, el inventario, el panel de código o un diálogo. Mientras dura, el mundo se detiene y la criatura no puede atrapar al jugador. |
| Pausa | Congela la partida y ofrece reanudar, guardar, entrar a la configuración o regresar al menú principal. |
| Capturado | Ocurre cuando la criatura alcanza a Vadrik. El jugador pierde el control y aparece la pantalla de captura, con las opciones «Reintentar» y «Menú principal». |
| Escena final | Después de que Vadrik lee el archivo de Jereth en la oficina del Dr. Cooper, la criatura aparece a sus espaldas (jumpscare). |
| Créditos | Muestran a los integrantes del equipo y los recursos utilizados. Se reproducen al cerrar la escena final y también pueden verse desde el menú principal. |

## Transiciones

| Estado origen | Evento | Estado destino | Condición |
|---|---|---|---|
| Menú principal | Elegir «Nueva partida» | Carga | Si ya hay una partida guardada, el juego pide confirmar, porque se reemplazará |
| Menú principal | Elegir «Continuar» | Carga | Tiene que existir una partida guardada válida |
| Menú principal | Elegir «Configuración» | Configuración | — |
| Carga | Termina de preparar una partida nueva | Introducción | La escena y el personaje ya están listos |
| Carga | Termina de preparar una partida guardada | Jugando | Se recuperan la posición, la batería y el progreso |
| Introducción | El texto termina o el jugador lo salta | Jugando | — |
| Jugando | Abrir un documento, el inventario (Tab) o el panel de código, o comenzar un diálogo | Lectura | No debe haber otra ventana abierta |
| Lectura | Cerrar la ventana (Esc, Tab o botón) o terminar el diálogo | Jugando | — |
| Jugando | Pulsar Esc | Pausa | — |
| Jugando | La ventana del juego deja de estar activa | Pausa | Solo cuando el estado era Jugando |
| Pausa | Elegir «Reanudar» o pulsar Esc otra vez | Jugando | — |
| Pausa | Elegir «Configuración» | Configuración | Al salir, se regresa a la pausa |
| Pausa | Elegir «Menú principal» | Menú principal | El jugador confirma que quiere abandonar la partida |
| Jugando | La criatura alcanza a Vadrik | Capturado | Está a 3 m o menos durante 0.6 s y el jugador no está escondido |
| Capturado | Elegir «Reintentar» | Carga | Se recupera el último checkpoint |
| Capturado | Elegir «Menú principal» | Menú principal | — |
| Jugando | Leer el archivo de Jereth en la oficina del Dr. Cooper | Escena final | Antes debe haber ocurrido la conversación con el Dr. Cooper |
| Escena final | Termina el jumpscare | Créditos | — |
| Créditos | Terminan o el jugador pulsa «Volver» | Menú principal | — |

## Reglas globales

1. El recorrido es lineal y sigue este orden: cabaña 1, bosque, cabaña 2, fogata, cabaña 3, generadores, puerta del laboratorio y oficina del Dr. Cooper.
2. Cada llave corresponde a una sola cabaña y no abre ninguna otra puerta.
3. El progreso se guarda al empezar la partida, al entrar a las cabañas 2 y 3, al restablecer la energía y al entrar al laboratorio.
4. Cuando la criatura atrapa a Vadrik, el intento termina y el jugador vuelve al último checkpoint.
5. Vadrik no tiene armas ni puede pelear; su única opción es evitar el peligro, esconderse o escapar.
6. La linterna solo gasta batería cuando está encendida, y las pilas son la única forma de recargarla.
7. Para abrir la puerta del laboratorio hay que colocar los dos fusibles, bajar las dos palancas e ingresar el código de la pizarra de la cabaña 3.
8. Cada vez que el jugador completa un paso, el objetivo en pantalla cambia al siguiente.
9. Lo que el jugador responde en los diálogos no altera el rumbo ni el desenlace de la historia.
10. Una puerta desbloqueada, un generador encendido o un objetivo cumplido se conservan durante toda la partida.
11. La criatura no puede entrar a la cabaña 1, ni atrapar al jugador mientras está escondido o tiene una ventana abierta.
12. El juego maneja una única partida guardada.

## Casos especiales

Documenta excepciones importantes para evitar interpretaciones diferentes durante la implementación.

1. Al recoger una pila con la batería casi llena, la carga sube hasta 100 %, lo que sobra se pierde y la pila desaparece de todos modos.
2. Cuando la batería se agota, la linterna deja de alumbrar, pero se conserva una luz ambiental tenue para que el jugador pueda seguir avanzando.
3. Tras una captura, el jugador reaparece en su último checkpoint con un mínimo de 30 % de batería, y la criatura regresa a su ruta de patrulla.
4. Si el jugador pausa en medio de una persecución, la criatura queda congelada y la persecución sigue exactamente donde se quedó al reanudar.
5. Si la ventana del juego deja de estar activa, por ejemplo con Alt + Tab, la partida se pausa sola.
6. Si el jugador entra a un escondite mientras lo persiguen, la captura se cancela y la criatura revisa la zona durante 6 s antes de retomar su patrulla.
7. Si el jugador intenta usar una caseta sin fusible, una puerta sin su llave o el panel sin energía, solo aparece un mensaje que lo indica.
8. Si el código es incorrecto, los dígitos se borran y el jugador puede volver a intentarlo cuantas veces quiera.
9. Si el jugador reaparece en un checkpoint posterior a un diálogo, la conversación no vuelve a reproducirse.
10. Si el archivo de guardado está dañado, el juego intenta cargar la copia de respaldo; si esta tampoco sirve, solo queda iniciar una nueva partida.

> **Navegación:** [[00 - Índice]] · ← [[06 - Economía y Recursos]] · [[01 - Premisa y Trama]] →