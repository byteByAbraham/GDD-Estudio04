# Economía y Recursos

## Descripción de la sección

Documenta cualquier recurso cuantificable: dinero, vida, energía, munición, experiencia, materiales, tiempo, puntos, etc.

## Recursos

| Recurso                | Obtención                                        | Uso                            | Límite                                  | Pérdida                                    |
| ---------------------- | ------------------------------------------------ | ------------------------------ | --------------------------------------- | ------------------------------------------ |
| Batería de la linterna | Inicia al 100%. Se recarga con pilas             | Mantener la linterna encendida | 100%                                    | Baja 0.3% por segundo con la luz encendida |
| Pila                   | 4 repartidas por el mapa, se recogen con **[E]** | Recarga 40% de la batería      | Se consume al recogerla y no se acumula | No aplica                                  |
| Linterna               | Disponible desde el inicio                       | Iluminar el entorno            | 1 unidad                                | No se puede perder                         |

## Fuentes y sumideros

**Fuentes:** las 4 pilas, repartidas por el bosque, las cabañas y el laboratorio.

**Sumideros:** el consumo de la linterna mientras está encendida.

## Reglas

- **Límites:** la batería nunca supera el 100%. Si el jugador recoge una pila con la batería casi llena, se completa hasta 100% y la pila se consume.

- **Sin acumulación:** las pilas se usan al recogerlas. No hay inventario de pilas.

- **Consumo:** la linterna apagada no consume. Pausar o abrir el archivo de notas tampoco.

- **Agotamiento:** al llegar a 0%, la linterna se apaga y queda una luz ambiental mínima para que la partida siga siendo jugable.

- **Garantía de diseño:** siempre hay una pila alcanzable antes del siguiente puzle.

- **Checkpoint:** al reaparecer, la batería queda al menos en 30%.

- **Sin regeneración:** las pilas no reaparecen ni se intercambian.

## Balance

¿Qué comportamiento queremos incentivar?
Que el jugador decida cuándo encender la linterna y cuándo avanzar a oscuras para ahorrar batería.

¿Qué comportamiento queremos evitar?
Que mantenga la luz siempre encendida sin consecuencias, o que se quede sin luz sin forma de recuperarla.

**Valor de referencia:** con 4 pilas, el jugador dispone de unos 14 minutos de luz continua. Es un valor provisional que se ajusta en las pruebas de calidad.


> **Navegación:** [[00 - Índice]] · ← [[05 - Progresión]] · [[07 - Reglas y Estados del Juego]] →
