## ¿Qué es Git?
**Git** es un sistema de control de versiones distribuido utilizado por desarrolladores y equipos para gestionar el código fuente de proyectos de software. Git permite llevar un registro detallado de todos los cambios realizados en un proyecto, facilita la colaboración entre desarrolladores y ayuda a mantener el historial de versiones de manera eficiente.

## Funciones Principales de Git

1. **Control de Versiones Distribuido**
   - Git permite que cada desarrollador tenga una copia completa del historial del proyecto. Esto significa que cada copia del repositorio es un respaldo completo del proyecto, asegurando que no se pierda información importante si ocurre un problema con el servidor central.
   - Al trabajar con Git, los usuarios pueden realizar acciones como commits, ramas y revisiones del historial de forma local, incluso sin conexión a internet, lo cual hace que el flujo de trabajo sea más eficiente y rápido.

   ![Control de Versiones Distribuido](https://labitstudio.com/wp-content/uploads/2021/05/Captura-de-pantalla-2021-05-26-a-las-13.39.59.png)

2. **Ramas (Branches)**
   - Las ramas son una parte fundamental de Git, permitiendo trabajar en diferentes funcionalidades de manera aislada. Esto facilita la colaboración sin alterar el código principal hasta que los cambios estén listos.
   - Las ramas se utilizan para probar nuevas funcionalidades, corregir errores o realizar experimentos, sin afectar la estabilidad del código en la rama principal (`main` o `master`). 

   ![Git Branches](https://res.cloudinary.com/snyk/images/f_auto,q_auto/w_1240,h_384,c_scale/v1/wordpress-sync/image1-11/image1-11-1240x384.png)

3. **Comandos Básicos**
   - **git init**: Inicializa un nuevo repositorio Git. Este comando se utiliza al crear un proyecto nuevo que aún no está bajo el control de versiones de Git.
     ```bash
     $ git init
     ```
     Después de inicializar el repositorio, Git comenzará a rastrear los cambios de los archivos en el proyecto, permitiendo guardar diferentes versiones a lo largo del tiempo.

   - **git clone**: Clona un repositorio existente. Para clonar un repositorio, usa el siguiente comando:
     ```bash
     $ git clone <url-del-repositorio>
     ```
     Este comando crea una copia completa del repositorio, incluyendo todo el historial de cambios. Es muy útil cuando quieres empezar a colaborar en un proyecto existente. Puedes clonar repositorios alojados en plataformas como **GitHub**, **GitLab**, o **Bitbucket**.
   
     Cuando clonas un repositorio, también se descargan todas las ramas del proyecto, y se puede trabajar con cualquiera de ellas de manera local. Esto permite a los desarrolladores trabajar en paralelo en diferentes características.

   - **git add**: Añade cambios al área de preparación (staging). El área de preparación es como un borrador donde puedes agrupar los cambios que se incluirán en el siguiente commit.
     ```bash
     $ git add <archivo>
     ```
     Puedes añadir un archivo específico o todos los archivos del proyecto con `git add .`. Esto te permite controlar qué cambios se incluirán en el commit, asegurando que solo los cambios completos o revisados se confirmen.

   - **git commit**: Guarda los cambios en el repositorio, creando un punto en el historial del proyecto. Los commits son la base del control de versiones, ya que permiten documentar cada cambio realizado en el proyecto.
     ```bash
     $ git commit -m "Descripción del cambio"
     ```
     Es importante usar mensajes descriptivos en cada commit, ya que estos ayudan a que el historial del proyecto sea entendible para otros desarrolladores y para el futuro.

   - **git push**: Sube los cambios al repositorio remoto. Esto permite que los demás desarrolladores vean y trabajen con los cambios que has realizado.
     ```bash
     $ git push origin nombre-de-la-rama
     ```
     Subir los cambios garantiza que todo el equipo esté sincronizado y que el repositorio remoto tenga la versión más reciente del proyecto.

   - **git pull**: Actualiza el repositorio local con los cambios del repositorio remoto. Esto es esencial cuando trabajas en equipo, ya que permite mantener tu copia del proyecto actualizada con los cambios realizados por los demás miembros.
     ```bash
     $ git pull
     ```
     El comando `pull` es una combinación de `fetch` y `merge`, que primero descarga los cambios del repositorio remoto y luego los fusiona con la copia local.

## Trabajar con Ramas en Git

4. **Trabajo en Equipo**
   - Git permite a varios desarrolladores trabajar simultáneamente en un proyecto, resolviendo conflictos cuando ocurren cambios en las mismas partes del código. Los desarrolladores pueden crear sus propias ramas para trabajar en una nueva característica y luego fusionar sus cambios a la rama principal una vez completados y probados.
   - Para cambiar a una rama existente, utiliza:
     ```bash
     $ git checkout nombre-de-la-rama
     ```
     Por ejemplo:
     ```bash
     $ git checkout main
     ```
     Esto es especialmente útil cuando se trabaja en diferentes aspectos de un proyecto a la vez, permitiendo a los desarrolladores integrar los cambios de forma ordenada.

   - **Crear y Fusionar Ramas**: Para crear una nueva rama y moverse a ella al mismo tiempo, se usa:
     ```bash
     $ git checkout -b mi-nueva-rama
     ```
     Esto crea una nueva rama para trabajar de forma aislada. Una vez terminada la tarea en esa rama, puedes integrarla a la rama principal mediante:
     ```bash
     $ git merge mi-nueva-rama
     ```
     Fusionar (merge) es un paso esencial que permite mantener el trabajo colaborativo limpio y actualizado, minimizando conflictos de código.

## Resolución de Conflictos

Cuando dos desarrolladores editan la misma línea de un archivo, Git no puede determinar automáticamente cuál es el cambio correcto. En estos casos, se genera un **conflicto** que debe ser resuelto manualmente.

- Los conflictos se presentan de la siguiente forma en el archivo afectado:
  ```plaintext
  <<<<<<< HEAD
  Código de la rama actual
  =======
  Código de la otra rama
  >>>>>>> mi-nueva-rama
