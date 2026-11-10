# Estructura del Contenido

## Estructura

Dark Mutant se desarrolla en un único escenario conectado, con una progresión lineal dividida en las siguientes zonas:

```text
Dark Mutant
├── Prólogo
│   └── Cinemática que muestra cómo y por qué Vadrik llega a la cabaña.
├── Bosque y cabañas
│   ├── Cabaña 1: despertar, encontrar la llave y salir.
│   ├── Cabaña 2: localizar la llave, investigar y obtener el primer fusible.
│   ├── Cabaña 3: encontrar la llave, obtener el segundo fusible y descubrir el código del laboratorio en una pizarra.
│   ├── Fogata: Vadrik experimenta una alucinación en la que cree encontrarse con Jereth.
│   └── Recorridos: explorar, seguir pistas y evitar a la criatura mutante.
├── Laboratorio
│   ├── Exterior
│   │   ├── Colocar los fusibles en las dos casetas eléctricas.
│   │   ├── Accionar las palancas para restablecer la energía.
│   │   └── Introducir el código en el panel de acceso.
│   └── Interior
│       ├── Explorar las instalaciones.
│       ├── Presenciar la muerte del Dr. Cooper.
│       └── Entrar a su oficina y descubrir la verdad mediante los expedientes de Jereth.
└── Final abierto
    └── El destino de Vadrik y Jereth queda sin confirmar.
```

## Cantidad estimada

| Contenido              |                                                        Cantidad y uso actual |
| ---------------------- | ---------------------------------------------------------------------------: |
| Personajes principales |                                              3: Vadrik, Jereth y Dr. Cooper. |
| Criatura mutante       |                                1: amenaza principal durante la exploración. |
| Escenarios             |      1 bosque, 3 cabañas principales, cabañas secundarias y 1 laboratorio. |
| Generadores            |         2 en el exterior del laboratorio; ambos deben activarse para entrar. |
| Fusibles               |                                              2: uno en cada cabaña (2 y 3). |
| Llaves                 | 3: una para salir de la primera cabaña y dos para acceder a las siguientes. |
| Panel de código       |                                                    1: acceso al laboratorio. |
| Pizarra                |                                            1: contiene el código de acceso. |
| Linterna               |                                       1, utilizada para iluminar el entorno. |
| Pilas                  |                          4 repartidas por el mapa para recargar la linterna. |
| Inventario             |                                           1: almacenar objetos recolectados. |
| NPC                    |                                                                            0 |

## Dependencias

| Contenido                                 | Requisito previo                                          |
| ----------------------------------------- | --------------------------------------------------------- |
| Despertar en la primera cabaña           | Finalizar la cinemática introductoria.                   |
| Salida al bosque                          | Encontrar y utilizar la llave de la primera cabaña.      |
| Acceso a la segunda cabaña               | Encontrar su llave correspondiente.                       |
| Primer fusible                            | Explorar el interior de la segunda cabaña.               |
| Acceso a la tercera cabaña               | Encontrar su llave correspondiente.                       |
| Segundo fusible y código                 | Explorar la tercera cabaña y revisar la pizarra.         |
| Checkpoint de cada cabaña                | Entrar a la cabaña correspondiente.                      |
| Generadores del laboratorio               | Colocar los dos fusibles y accionar las palancas.         |
| Entrada al laboratorio                    | Restablecer la energía e introducir el código correcto. |
| Investigación y conversación con Cooper | Entrar al laboratorio.                                    |
| Final abierto                             | Descubrir la verdad mediante los expedientes de Jereth.   |
