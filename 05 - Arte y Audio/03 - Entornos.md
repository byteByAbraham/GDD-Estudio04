# Entornos

## Zonas

| Zona                     | Estilo                                                     | Elementos                                                                                                                                                   | Función                                                                                                     |
| ------------------------ | ---------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Bosque                   | Nocturno, oscuro y de tonos fríos.                         | Árboles altos, troncos, vegetación de formas simples y angulares, hierba, terreno irregular y lluvia intermitente.                                          | Conectar las zonas y permitir la exploración, el escondite y las persecuciones.                             |
| Cabañas                  | Construcciones rurales envejecidas y deterioradas          | Paredes, pisos, puertas y escalones de madera desgastada, ventanas y mobiliario antiguo.                                                                    | Alojar los objetivos de acceso, notas que aportan información sobre la historia y checkpoints.              |
| Exterior del laboratorio | Industrial, sencillo y deteriorado.                        | Edificio principal, cercado perimetral, entrada de acceso y dos generadores                                                                                 | Presentar el desafío de restablecer la energía para entrar.                                                 |
| Interior del laboratorio | Instalación de investigación antigua, oscura y deteriorada | Habitaciones, áreas similares a quirófanos, mesas de procedimientos, equipo de laboratorio, mobiliario médico, expedientes y evidencias de los experimentos | Permitir la exploración de las instalaciones y concentrar las evidencias que conducen a la revelación final |

## Modularidad

- Árboles y vegetación para distribuirlos en distintas zonas del bosque.
* Componentes de las cabañas, como puertas, ventanas y superficies de madera.
* Secciones del cercado del laboratorio.
- Modelo de generador reutilizado en las dos ubicaciones del exterior del laboratorio.
* Materiales de madera, piedra, concreto, y suelo.
* Modelos base de notas y expedientes, cambiando sus imágenes y textos.

## Iluminación

La iluminación global es nocturna y tenue, con predominio de azul oscuro. Permite distinguir el relieve del terreno y las siluetas cercanas, mientras el fondo permanece en penumbra.

La linterna proporciona luz dirigida para reconocer objetos y detalles durante la exploración. No existe un ciclo de día y noche.

En el interior del laboratorio, la iluminación mantiene una atmósfera oscura e inquietante, utilizando luces de tonos blancos y amarillentos de baja intensidad. Estas permiten distinguir las habitaciones, el mobiliario y los equipos sin iluminar completamente los espacios, conservando las zonas de sombra y la sensación de tensión.

## Efectos visuales

- **Clima:** Lluvia intermitente y presencia de neblina durante el recorrido exterior, sin afectar los espacios interiores.
- **Niebla ambiental:** Neblina distribuida por el bosque que limita la visibilidad de los elementos lejanos y refuerza la sensación de aislamiento. 
- **Iluminación:** Contraste entre las zonas oscuras y la luz de la linterna durante la exploración.

## Recursos requeridos

Lista los modelos, sprites, texturas, materiales y efectos necesarios.

| Tipo de recurso    | Recursos                                                                                                                                                  |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Modelos 3D         | Árboles, vegetación, terreno, cabañas, laboratorio, cercado, puertas, mobiliario, equipo de laboratorio, generadores, llaves, fusibles, linterna y pilas. |
| Objetos narrativos | Notas, expedientes y fotografías colocados en el escenario.                                                                                               |
| Texturas           | Corteza, suelo, madera envejecida, piedra, vegetación, musgo, concreto deteriorado, metal y papel.                                                        |
| Materiales         | Superficies mates y desgastadas, metal oxidado y acabados húmedos con reflejos discretos.                                                                 |
| Imágenes           | Diseños de notas, expedientes y fotografías utilizados como texturas.                                                                                     |
| Efectos            | Lluvia intermitente, neblina, iluminación de la linterna y efectos visuales de peligro durante la detección y persecución de la criatura mutante.         |

## Modelos 3D

| Cabaña | Laboratorio |
| ------- | ----------- |
| ![[Entorno_Cabana.gif\|276]]        | ![[Entorno_Laboratorio.gif\|344]]            |
