# Comandos Adicionales de Unix

## 1. Wildcards
Los **wildcards** (comodines) son caracteres especiales utilizados para representar uno o más caracteres en el nombre de un archivo o directorio, lo que facilita las operaciones sobre múltiples archivos o directorios.

- **Asterisco (\*)**: Representa cualquier cadena de caracteres (incluido ningún carácter).
  - Ejemplo: `ls *.txt` listará todos los archivos con extensión `.txt` en el directorio actual.

- **Interrogación (?)**: Representa un único carácter.
  - Ejemplo: `ls file?.txt` listará archivos como `file1.txt`, `fileA.txt`.

- **Corchetes ([ ])**: Representan un conjunto de caracteres específicos.
  - Ejemplo: `ls file[1-3].txt` listará `file1.txt`, `file2.txt`, `file3.txt`.

## 2. rm (Remove)
El comando **rm** se utiliza para eliminar archivos y directorios del sistema de archivos.

- **Eliminar un Archivo**: Elimina un archivo específico.
  ```bash
  $ rm archivo.txt

- **Eliminar Directorios**: Elimina un directorio y todo su contenido.

    ```bash
    $ rm -r nombre_directorio

- **Forzar Eliminación**: Elimina sin confirmación, se utiliza la opción -f junto con -r.
    ```bash
    $ rm -rf nombre_directorio

## 3. mv (Move)
El comando **mv** se utiliza para mover o renombrar archivos y directorios.

- **Mover Archivos o Directorios**: Mueve un archivo o diretorio a otra ubicación.
    ```bash
    $ mv archivo_origen ruta_destino

- **Renombrar Archivos o Directorios**: Cambia el nombre de un archivo o directorio.
    ```bash
    $ mv nombre_actual nuevo_nombre

## 4. ls (List)
El comando **ls** se utiliza para listar archivos y directorios en Unix.

- **Listar en Formato Largo**: Se usa para obtener información detallada sobre los archivos, como permisos, tamaño, y fecha de modificación.
    ```bash
    $ ls -l

- **Listar Archivos Ocultos**: Muestra los archivos ocultos.
    ```bash
    $ ls -a

- **Ordenar por Tamaño**: Lista los archivos por tamaño.
    ```bash 
    $ ls -lS

- **Formato Humano Legible**: Muestra el tamaño de los archivos en KB, MB, GB.
    ```bash
    $ ls -lh

## 5. Obtener Peso de Archivos Ordenado
Para obtener el peso de los archivos y directorios de manera ordenada, se puede utilizar el comando tree junto con otras opciones que nos permiten visualizar de forma estructurada el tamaño de cada archivo.

- **Instalar `tree`**
    Primero, es necesario instalar tree (en algunas distribuciones no está instalado por defecto).
    ```bash
    $ sudo apt-get install tree

- **Listar Archivos con Tamaño**:
    El comando `tree` muestra la estructura de comandos y directorios, junto con el tamaño de cada uno.
    ```bash 
    $ tree -h --du


