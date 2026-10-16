# Enemigos y NPC

## Descripción de la sección

Documenta las entidades controladas por el juego y su comportamiento.

## Enemigos

### La Criatura

**Rol de combate:**

No aplica como rol de combate. Es la amenaza principal de sigilo y persecución. Su función es acechar al jugador, reaccionar a los estímulos del entorno y generar tensión durante la exploración. No puede ser derrotada.

**Comportamiento:**

La criatura patrulla determinadas zonas del bosque y reacciona a estímulos visuales y auditivos. Puede investigar sonidos o la luz de la linterna, pero no conoce automáticamente la ubicación actual del jugador.

Cuando confirma visualmente al jugador, inicia una persecución. Si pierde el contacto visual, se dirige a la última posición en la que lo vio y busca señales antes de regresar a su patrulla. Si observa al jugador entrar en un escondite, puede comprobarlo al llegar.

El tarareo funciona como una señal sonora de amenaza. Advierte al jugador de la posible presencia de la criatura, pero no confirma por sí solo que esta lo haya detectado.

**Vida:**

No aplica. La criatura no tiene una barra de vida y no puede ser derrotada mediante combate.

**Daño:**

No se utiliza un sistema de daño numérico. Si la criatura alcanza al jugador y completa la captura, el intento termina y se activa el flujo de reinicio de la partida.

**Defensas:**

No se definen defensas de combate, ya que el jugador no puede atacar ni derrotar a la criatura.

**Velocidad:**

| Estado      | Velocidad |
| ----------- | ------------------: |
| Patrulla    |             1.5 m/s |
| Persecución |               4 m/s |

**Rango de detección:**

*Detección visual*

| Parámetro                              | Valor |
| -------------------------------------- | --------------- |
| Apertura del cono visual               | 70°             |
| Alcance sin lluvia                     | 10 metros       |
| Alcance con lluvia                     | 7 metros        |
| Tiempo de confirmación visual de pie   | 0.8 segundos    |
| Tiempo de confirmación visual agachado | 1.2 segundos    |


*Detección auditiva*


| Acción del jugador   | Sin lluvia | Con lluvia |
| -------------------- | ---------: | ---------: |
| Caminar              |        5 m |        3 m |
| Correr               |       12 m |        8 m |
| Desplazarse agachado |        2 m |        1 m |

Los sonidos conducen a la criatura hacia el punto de origen del estímulo; no revelan automáticamente la posición actual del jugador.

*Detección de la linterna*

- Si el haz de la linterna alcanza a la criatura a una distancia de 8 metros o menos y no hay obstáculos, esta investiga el origen de la luz.
- La linterna sirve para iluminar y explorar, pero su batería limitada obliga al jugador a administrar su uso.
- Los avisos de percepción se limitan a uno por segundo para evitar reacciones repetitivas.

**Ataques:**

La criatura no utiliza un sistema de combate. Su única acción de captura ocurre cuando consigue alcanzar al jugador.

1. Se aproxima hasta una distancia de 1.2 metros.
2. Comprueba que no haya obstáculos entre el y el jugador.
3. Inicia una preparación visible de 0.6 segundos.
4. Si el jugador continúa a su alcance al terminar la preparación, la criatura lo captura.
5. La captura termina el intento actual y activa el flujo de reinicio de la partida.

La preparación visible sirve como oportunidad para que el jugador intente escapar o alcanzar un lugar seguro.

**Debilidades:**

- Los obstáculos sólidos bloquean su visión.
- La pérdida de contacto visual hace que busque en la última posición confirmada, en lugar de conocer la ubicación actual del jugador.
- Los sonidos y la luz pueden atraerla hacia el origen del estímulo.
- Los escondites pueden ocultar al jugador si la criatura no observó su entrada.
- Las zonas protegidas del nivel impiden que lo alcance directamente.

**Recompensa:**

No otorga objetos ni recompensas por derrotarla, ya que no puede eliminarse. La recompensa por superar sus encuentros consiste en poder continuar la exploración, descubrir información narrativa y avanzar hacia el laboratorio.

**Estados de IA:**

```
Patrullar
    ↓
Investigar señal → Detectar al jugador
    ↑                       ↓
    │                   Perseguir
    │                       ↓
    └── Buscar ← Perder de vista al jugador
         ↓
      Patrullar
------------------------------------------
Perseguir → Preparar captura → Capturar al jugador
                   ↓
       El jugador escapa o alcanza
             una zona segura
------------------------------------------
Perseguir → Comprobar escondite
             (si observó la entrada)
```

**Reglas complementarias de IA:**

- Si pierde la visión durante 2 segundos, se dirige a la última posición confirmada.
- Al llegar a esa posición, busca durante 8 segundos. Si no recibe señales nuevas, vuelve a patrullar.
- Si observa al jugador entrar en un escondite, puede comprobarlo.
- La captura requiere que el jugador permanezca dentro del alcance al finalizar la preparación.
- La criatura no navega ni captura dentro de la cabaña inicial ni del vestíbulo del laboratorio.
- La IA no incluye estados de combate, daño, aturdimiento ni interrupción mediante golpes o luz defensiva.

## NPC

### El niño

**Función:**

Representar el vínculo emocional entre el padre y su hijo, reforzar el conflicto narrativo y mantener la duda sobre cuánto de la identidad del niño permanece en la criatura.

**Ubicación:**

En un punto del bosque definido por la progresión narrativa. La ubicación exacta y el momento de aparición se establecerán durante el diseño del nivel.

**Interacción:**

Aparece como un evento narrativo no jugable. El jugador no lo controla ni inicia una conversación interactiva. El encuentro se presenta a distancia y está diseñado para provocar incertidumbre.

**Diálogos:**

No se han definido líneas de diálogo completas. Durante el encuentro, el niño parece pedir ayuda, lo que lleva al jugador a cuestionar si conserva su identidad o si la criatura está imitando su comportamiento.

**Condiciones:**

- Se activa en un punto determinado de la progresión narrativa.
- Se presenta a distancia y no funciona como un enemigo independiente.
- No inicia un combate ni añade una mecánica de enfrentamiento.
- Su aparición debe mantener la incertidumbre sin revelar toda la historia anticipadamente.

**Recompensas / información:**

No otorga objetos ni recompensas físicas. Su función es narrativa: reforzar el vínculo entre el padre y el niño y hacer que el jugador cuestione la naturaleza de la criatura.

### Animal del bosque

**Función:**

Complementar la atmósfera del bosque mediante sonidos ambientales.

**Ubicación:**

Entorno natural del bosque. No se establece una ubicación física visible.

**Interacción:**

No tiene interacción con el jugador. Se representa únicamente mediante sonido ambiental.

**Diálogos:**

No aplica.

**Condiciones:**

Los sonidos forman parte de la ambientación. No se define un comportamiento de enemigo, persecución ni inteligencia artificial para el animal.

**Recompensas / información:**

No otorga recompensas ni información narrativa directa. Su propósito es exclusivamente ambiental y sonoro.


> **Navegación:** [[00 - Índice]] · ← [[02 - Niveles]] · [[04 - Objetos y Coleccionables]] →
