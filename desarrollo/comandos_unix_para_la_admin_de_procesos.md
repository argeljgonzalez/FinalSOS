## Comandos de Unix para la Administración de Procesos
En **Unix** y **Linux**, los procesos son gestionados mediante una serie de comandos que permiten ver, crear, modificar y finalizar procesos en ejecución. Estos comandos son fundamentales para los administradores de sistemas y usuarios que desean tener un control completo sobre los recursos y el rendimiento del sistema.

Unix proporciona varias herramientas poderosas para la administración de procesos, que incluyen la monitorización del uso de la CPU, la memoria, y la gestión de los procesos activos.

## Principales Comandos de Unix para la Administración de Procesos

1. **ps (Process Status)**
   - El comando `ps` se utiliza para mostrar información sobre los procesos que se están ejecutando en el sistema. Muestra una instantánea de los procesos en ejecución en el momento de su ejecución.
   - Por defecto, `ps` muestra solo los procesos iniciados por el usuario que ejecuta el comando y asociados a la terminal en uso.
     ```bash
     $ ps
     ```
   - Para ver una lista más detallada de todos los procesos en el sistema, se puede utilizar:
     ```bash
     $ ps aux
     ```
   - La opción `-a` muestra procesos de otros usuarios, `-u` muestra el nombre del usuario y `-x` muestra procesos que no están asociados con una terminal.

2. **top**
   - El comando `top` proporciona una vista en tiempo real de los procesos que se están ejecutando en el sistema. Muestra información como el uso de la CPU, la memoria, y otros recursos importantes para cada proceso.
   - Es especialmente útil para monitorizar el rendimiento y ver qué procesos están utilizando más recursos.
     ```bash
     $ top
     ```

3. **htop** 
   - `htop` es una versión mejorada de `top` con una interfaz más amigable. Ofrece una vista interactiva del uso de recursos del sistema, con opciones para navegar y gestionar los procesos de forma más sencilla.
     ```bash
     $ htop
     ```
   - Para utilizar `htop`, es posible que necesites instalarlo con:
     ```bash
     $ sudo apt-get install htop
     ```

4. **kill**
   - El comando `kill` se utiliza para finalizar un proceso específico. Para usarlo, necesitas conocer el **PID** (Process ID) del proceso que deseas terminar, el cual se puede obtener usando `ps` o `top`.
     ```bash
     $ kill <PID>
     ```
   - También puedes enviar diferentes señales al proceso usando `kill`. Por ejemplo, `kill -9 <PID>` envía una señal **SIGKILL** que fuerza la finalización inmediata del proceso.

5. **killall**
   - `killall` se utiliza para finalizar todos los procesos que comparten el mismo nombre. Esto es útil cuando necesitas detener múltiples instancias de un mismo proceso.
     ```bash
     $ killall nombre_proceso
     ```
   - Por ejemplo, para finalizar todos los procesos de `firefox`:
     ```bash
     $ killall firefox
     ```

6. **pkill**
   - El comando `pkill` es similar a `killall`, pero permite finalizar procesos usando patrones. Puedes especificar parte del nombre del proceso o utilizar expresiones regulares para encontrar los procesos.
     ```bash
     $ pkill nombre_parcial
     ```

7. **nice y renice**
   - Los comandos `nice` y `renice` se utilizan para ajustar la **prioridad** de los procesos. Esto determina la cantidad de recursos que la CPU asignará al proceso.
   - **nice** se utiliza al iniciar un proceso para definir su prioridad:
     ```bash
     $ nice -n 10 comando
     ```
     Cuanto mayor sea el valor (`-n`), menor será la prioridad.
   - **renice** se utiliza para cambiar la prioridad de un proceso que ya está en ejecución:
     ```bash
     $ renice 5 -p <PID>
     ```

8. **bg y fg**
   - Los comandos `bg` y `fg` se utilizan para gestionar procesos en **segundo plano** y **primer plano**, respectivamente.
   - Si un proceso se inició y luego se detuvo con `Ctrl+Z`, se puede enviar al segundo plano con `bg`:
     ```bash
     $ bg %1
     ```
   - Para traer un proceso del segundo plano al primer plano, se usa `fg`:
     ```bash
     $ fg %1
     ```

9. **jobs**
   - El comando `jobs` muestra los procesos que se están ejecutando en segundo plano desde la terminal actual.
     ```bash
     $ jobs
     ```

10. **nohup**
    - `nohup` (No Hang Up) se utiliza para ejecutar un proceso que continuará funcionando incluso después de cerrar la terminal. Esto es útil para procesos largos que necesitan seguir ejecutándose sin supervisión.
      ```bash
      $ nohup comando &
      ```
    - El símbolo `&` se utiliza para enviar el proceso al segundo plano automáticamente. Los resultados se redirigen a un archivo llamado `nohup.out` a menos que se especifique lo contrario.

11. **pgrep**
    - `pgrep` se utiliza para buscar procesos que coincidan con un patrón específico y devolver sus **PIDs**.
      ```bash
      $ pgrep nombre_proceso
      ```

12. **pidof**
    - El comando `pidof` se utiliza para encontrar el **PID** de un proceso específico por su nombre.
      ```bash
      $ pidof nombre_proceso
      ```
    - Por ejemplo, para obtener el PID de `sshd`:
      ```bash
      $ pidof sshd
      ```

13. **top -p**
    - Puedes usar `top` para monitorear un proceso específico utilizando su **PID**.
      ```bash
      $ top -p <PID>
      ```
    - Esto es útil para enfocarse en un proceso particular y monitorizar su uso de recursos de manera continua.

14. **uptime**
    - El comando `uptime` muestra cuánto tiempo ha estado encendido el sistema y cuántos procesos están activos.
      ```bash
      $ uptime
      ```
    - También proporciona información sobre la carga media del sistema en los últimos 1, 5 y 15 minutos.

15. **watch**
    - El comando `watch` se utiliza para ejecutar un comando repetidamente, mostrando el resultado en intervalos de tiempo regulares. Es útil para monitorizar los cambios en el estado del sistema.
      ```bash
      $ watch ps aux
      ```
    - De esta forma, puedes ver una actualización continua de los procesos en ejecución.

16. **nice**
    - El comando `nice` también puede ser usado directamente para iniciar un proceso con una prioridad más baja.
      ```bash
      $ nice -n 15 myscript.sh
      ```
    - Esto asegura que el proceso tenga menos prioridad y no consuma muchos recursos.

17. **atop**
    - `atop` es otra herramienta para monitorizar el rendimiento del sistema, muy similar a `top` y `htop`. Proporciona información detallada sobre los procesos, la CPU, la memoria, la actividad del disco y la red.
      ```bash
      $ atop
      ```
    - Necesitas instalarlo primero, y es especialmente útil para ver cuellos de botella en el sistema.

18. **lsof (List Open Files)**
    - `lsof` se utiliza para listar todos los archivos abiertos por un proceso específico. En Unix, todo es un archivo, incluidos sockets y conexiones de red.
      ```bash
      $ lsof -p <PID>
      ```
    - Esto te permite ver todos los recursos (archivos, puertos, etc.) que están siendo utilizados por un proceso específico.

19. **strace**
    - El comando `strace` se usa para rastrear las llamadas al sistema y las señales recibidas por un proceso.
      ```bash
      $ strace -p <PID>
      ```
    - Es útil para depurar programas y entender qué hace un proceso en particular.

20. **timeout**
    - El comando `timeout` permite ejecutar un comando durante un período específico. Si el proceso sigue en ejecución después del tiempo especificado, será terminado automáticamente.
      ```bash
      $ timeout 30s myscript.sh
      ```
    - Esto asegura que un proceso no corra más allá del tiempo asignado.

