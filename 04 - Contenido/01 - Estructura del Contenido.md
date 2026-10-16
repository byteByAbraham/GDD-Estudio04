# Estructura del Contenido

## Descripción de la sección

Organiza el contenido del videojuego en unidades manejables: mundos, capítulos, zonas, niveles, misiones y desafíos.

## Estructura

```text
Juego
├── Zona 1: Cabaña 1 
│   ├── Tutotial de escondite,linterna y puzzle de salida 1 
│   ├── Evento: 1.er Avistamiento del moustro
├── Zona 2: Cabaña 2
│   ├── Busqueda de baterias y puzzle de cabaña 2  
├── Zona 3: Cabaña 3 
│   ├── Busqueda de baterias y puzzle de cabaña 3
│   ├── Puzzle de casa escondite: Obtecion de llave de acceso 
│   ├── Evento 2. Avistamiento del moustro
├── Zona 4: Fogata
│   ├── Encendido del generador principal 
│   ├── Evento 3. Avistamiento del niño / Desbloque de energia
├── Zona 5: Cabaña 2
    ├── Requisito: Uso de llave de acceso + Energia activa del            ├   generador  
    ├── Evento: Desenlace del juego 
```

## Cantidad estimada

| Tipo            | Cantidad |
| --------------- | -------: |
| Mundos          |        1 |
| Niveles /Zonas  |        5 |
| Puzzle          |        4 |
| Enemigos        |        1 |
| Misiones        |        5 |
| Escondites      |        4 |
| Objetivos clave |        6 |

## Dependencias

¿Qué contenido debe existir antes de otro?
Secuencia de puzle y progreso 
+ El puzle de C1 debe resolver para poder salir hacia c2
+ Resolver el puzle de la casa para obtener la llave de acceso al laboratorio 
Requisitos de entrada del laboratorio 
+ Conseguir la llave de acceso 
+ Encender el generador para suministra la energía a la puerta del laboratorio 
Elementos: Los 4 escondites, las 4 baterías  
> **Navegación:** [[00 - Índice]] · ← [[04 - Diálogos y Narrativa]] · [[02 - Niveles]] →
