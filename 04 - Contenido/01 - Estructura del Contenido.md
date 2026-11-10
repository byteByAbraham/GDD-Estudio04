# Estructura del Contenido

## Estructura

Dark Mutant se desarrolla en un único escenario conectado, con una progresión lineal dividida en las siguientes zonas:

```text
Dark Mutant
├── Prólogo 
│   ├──cinemática que muestra cómo y por qué Vadrik llega a la cabaña, antes de despertar.
├── Bosque y cabañas
│   ├──Cabaña 1: despertar y encontrar la salida.
│   ├── Cabaña 2: buscar la llave e investigar.
│   └── Cabaña 3: continuar la investigación.
│   └── Recorridos: evitar a la criatura mutante.
├── Laboratorio
│   └── Exterior: activar los dos generadores.
│   └── Interior: investigar los expedientes y descubrir la verdad.
└── Final abierto
│   └──El destino de Vadrik y Jereth queda sin confirmar.
```

## Cantidad estimada

| Contenido            |                                                                       Cantidad y uso actual |
| -------------------- | ------------------------------------------------------------------------------------------: |
| Bosque               |                                entorno principal que conecta las cabañas y el laboratorio. |
| Cabañas principales |                               3 destinadas a la exploración, investigación y checkpoints. |
| Laboratorio          | 1, dividido en exterior e interior; concentra el desafío de acceso y la revelación final. |
| Generadores          |                        2 en el exterior del laboratorio; ambos deben activarse para entrar. |
| Llaves               |                3: una para salir de la primera cabaña y dos para acceder a las siguientes. |
| Linterna             |                                                      1, utilizada para iluminar el entorno. |
| Pilas                |                                         4 repartidas por el mapa para recargar la linterna. |
| NPC                  |                                                                                           0 |

## Dependencias

| Contenido                                 | Requisito previo                                     |
| ----------------------------------------- | ---------------------------------------------------- |
| Despertar en la primera cabaña           | Finalizar la cinemática introductoria.              |
| Salida al bosque                          | Encontrar y utilizar la llave de la primera cabaña. |
| Acceso a la segunda cabaña               | Encontrar su llave correspondiente.                  |
| Acceso a la tercera cabaña               | Encontrar su llave correspondiente.                  |
| Checkpoint de cada cabaña                | Entrar a la cabaña correspondiente.                 |
| Objetivo del laboratorio                  | Completar el recorrido por las tres cabañas.        |
| Entrada al laboratorio                    | Activar los dos generadores del exterior.            |
| Investigación y conversación con Cooper | Entrar al laboratorio.                               |
| Final abierto                             | Completar la revelación sobre Jereth.               |
