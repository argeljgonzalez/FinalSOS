## Planificación de Procesos
La **planificación de procesos** es una de las tareas más importantes del sistema operativo. Su objetivo principal es decidir qué proceso debe utilizar la CPU en un momento dado, de manera que se optimicen los recursos y se maximice el rendimiento del sistema. Existen varios **algoritmos de planificación de procesos**, cada uno con sus características y ventajas específicas.

En este documento, exploraremos tres de los algoritmos más comunes: **First-Come, First-Served (FCFS)**, **Round Robin (RR)**, y **Shortest Job First (SJF)**.

## a. First-Come, First-Served (FCFS)
**First-Come, First-Served (FCFS)** es el algoritmo de planificación más sencillo. En FCFS, los procesos son atendidos en el orden en que llegan a la cola de planificación, es decir, el primer proceso que llega es el primero en ser ejecutado.

### Características de FCFS
1. **Orden de Llegada**: Los procesos son colocados en una cola según el orden en que llegan. El primer proceso que llega es el primero en ejecutarse.
2. **Fácil de Implementar**: Este algoritmo es simple y fácil de implementar, ya que solo requiere mantener una lista de procesos en la orden en que llegan.
3. **No Preemptivo**: Una vez que un proceso comienza a ejecutarse, no se interrumpe hasta que finaliza.

### Ventajas de FCFS
- **Simplicidad**: Es fácil de entender e implementar, lo cual lo hace adecuado para sistemas sencillos.
- **Sin Hambre**: No hay posibilidad de que un proceso quede sin ser ejecutado (no hay **starvation**), ya que todos los procesos eventualmente reciben tiempo de CPU.

### Desventajas de FCFS
- **Tiempo de Espera Alto**: Puede causar un **tiempo de espera promedio** elevado, especialmente cuando un proceso largo bloquea la ejecución de procesos más cortos que llegan después.
- **Efecto Convoy**: Procesos más largos pueden hacer que todos los procesos siguientes en la cola esperen mucho tiempo, creando el efecto conocido como **convoy**.

![Planificación FCFS](https://sisoperativoutp1995.wordpress.com/wp-content/uploads/2016/08/c-program-for-fcfs.jpg)

### Ejemplo
Si los procesos **P1, P2, P3** llegan en ese orden con los tiempos de ejecución de 10, 5, y 2 unidades de tiempo respectivamente, FCFS los ejecutará en el mismo orden, resultando en un **tiempo de espera promedio** elevado, especialmente para procesos que llegan más tarde pero requieren menos tiempo.

## b. Round Robin (RR)
**Round Robin (RR)** es un algoritmo de planificación **preemptivo** que asigna a cada proceso un período de tiempo fijo, conocido como **cuántum**. Si el proceso no termina durante su tiempo asignado, se coloca al final de la cola de listos y se asigna la CPU al siguiente proceso.

### Características de Round Robin
1. **Cuántum de Tiempo**: Cada proceso recibe un tiempo fijo para ejecutarse. Si no termina dentro de ese tiempo, es preemptado y se coloca de nuevo en la cola.
2. **Equitativo**: Cada proceso recibe una oportunidad justa de usar la CPU, lo que lo hace ideal para sistemas de **tiempo compartido**.
3. **Preemptivo**: Este algoritmo puede interrumpir un proceso en ejecución para dar paso a otro proceso, mejorando la capacidad de respuesta.

### Ventajas de Round Robin
- **Equidad**: Todos los procesos reciben la misma cantidad de tiempo para ejecutarse, lo cual evita la **starvation**.
- **Mejora la Capacidad de Respuesta**: Al asignar un tiempo fijo a cada proceso, se asegura que todos los procesos tengan una **respuesta rápida**, especialmente en sistemas interactivos.

### Desventajas de Round Robin
- **Dependencia del Cuántum**: La eficiencia de Round Robin depende en gran medida del tamaño del cuántum. Si el cuántum es muy grande, se comporta como **FCFS**; si es muy pequeño, puede causar **sobrehead** debido a los frecuentes cambios de contexto.
- **Overhead de Cambio de Contexto**: Con cada interrupción, se realiza un cambio de contexto, lo cual puede consumir muchos recursos si el cuántum es pequeño.

![Planificación Round Robin](https://assets.isu.pub/document-structure/210220025928-22eef5a28a31422d6b35315f29a637fd/v1/cb97337e8d4993bf4c11263dceb9661a.jpg)

### Ejemplo
Si los procesos **P1, P2, P3** tienen tiempos de ejecución de 8, 4, y 2 unidades respectivamente, y el cuántum es de **2 unidades**, el orden de ejecución sería intercalado. Primero se ejecuta **P1** durante 2 unidades de tiempo, luego **P2** durante 2 unidades, luego **P3** durante 2 unidades, y luego se vuelve a **P1** y **P2** hasta que todos los procesos se completen. Esto proporciona una **respuesta más rápida** a todos los procesos.

## c. Shortest Job First (SJF)
**Shortest Job First (SJF)** es un algoritmo de planificación que selecciona el proceso con el **tiempo de ejecución más corto** para ser ejecutado a continuación. SJF puede ser **preemptivo** o **no preemptivo**.

### Tipos de SJF
1. **No Preemptivo**: Una vez que el proceso más corto comienza a ejecutarse, no se interrumpe hasta que finalice.
2. **Preemptivo** (también conocido como **Shortest Remaining Time First**, SRTF): Si un proceso nuevo llega con un tiempo de ejecución más corto que el tiempo restante del proceso en ejecución, este será interrumpido para dar lugar al nuevo proceso.

### Ventajas de SJF
- **Tiempo de Espera Promedio Bajo**: SJF ofrece el **menor tiempo de espera promedio** de todos los algoritmos de planificación, ya que siempre selecciona el proceso más corto para ser ejecutado.
- **Eficiencia**: Minimiza el tiempo total que los procesos pasan esperando para ser ejecutados, lo cual mejora el rendimiento general del sistema.

### Desventajas de SJF
- **Difícil de Implementar**: SJF requiere conocer de antemano el tiempo de ejecución de cada proceso, lo cual no siempre es posible en la práctica.
- **Starvation**: Los procesos largos pueden quedar sin ser ejecutados durante un período de tiempo indefinido si llegan procesos más cortos, causando **starvation**.

![Planificación SJF](https://assets.isu.pub/document-structure/210220031703-b6bc41296d5ba6175a83a1ef776f7885/v1/997faa72eabb056e69c84ac5df11688a.jpg)

### Ejemplo
Si los procesos **P1, P2, P3** llegan con tiempos de ejecución de **6, 2, 8** unidades de tiempo respectivamente, el algoritmo SJF seleccionará primero **P2** (con 2 unidades), luego **P1** (con 6 unidades), y finalmente **P3** (con 8 unidades), minimizando así el tiempo total de espera para todos los procesos.

## Comparación de los Algoritmos

| Característica        | FCFS                         | Round Robin                  | SJF                           |
|-----------------------|------------------------------|------------------------------|-------------------------------|
| **Tipo**              | No Preemptivo                | Preemptivo                   | Preemptivo/No Preemptivo      |
| **Orden de Ejecución**| Según el orden de llegada    | En turnos con tiempo fijo    | Tiempo de ejecución más corto |
| **Equidad**           | Baja                         | Alta                         | Baja                          |
| **Starvation**        | No                           | No                           | Sí                            |
| **Overhead**          | Bajo                         | Alto (cambio de contexto)    | Bajo/Moderado                 |
| **Adecuado para**     | Sistemas Sencillos           | Sistemas Interactivos        | Sistemas de Lote              |

## Resumen
La **planificación de procesos** es fundamental para garantizar un uso eficiente de la CPU y de los recursos del sistema operativo. Cada algoritmo de planificación tiene sus ventajas y desventajas, dependiendo del entorno en el que se utilice:
- **FCFS** es simple y justo para procesos que llegan en orden, pero puede generar largos tiempos de espera.
- **Round Robin** asegura equidad y una respuesta rápida en sistemas interactivos, pero depende del tamaño del cuántum.
- **SJF** minimiza el tiempo de espera promedio, pero puede provocar starvation en procesos más largos.
