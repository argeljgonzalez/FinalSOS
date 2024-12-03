# Permisos en Archivos Unix (`chmod`)

El comando `chmod` en sistemas Unix y similares (como Linux) se utiliza para cambiar los permisos de acceso a archivos y directorios. Estos permisos determinan quién puede leer, escribir o ejecutar un archivo o directorio.

---

## Formato de los Permisos

### Grupos de Permisos
1. **Propietario (Owner)**: El usuario que posee el archivo.
2. **Grupo (Group)**: Los usuarios que forman parte del grupo del archivo.
3. **Otros (Others)**: Cualquier otro usuario.

### Tipos de Permisos
- **Lectura (`r`)**: Permite leer el contenido del archivo o listar el directorio.
- **Escritura (`w`)**: Permite modificar el contenido del archivo o crear/borrar archivos en un directorio.
- **Ejecución (`x`)**: Permite ejecutar un archivo (si es un programa/script) o acceder a un directorio.

---

### Representación en Notación

1. **Simbólica**: Una secuencia de 10 caracteres.       
    - Ejemplo:  
`x-rwxr-xr--`

Aquí:
- El primer carácter indica el tipo de archivo (`-` para archivo regular, `d` para directorio, `l` para enlace simbólico, etc.).
- Los siguientes 9 caracteres están divididos en tres grupos de tres:
  - `rwx` (propietario)
  - `r-x` (grupo)
  - `r--` (otros)

2. **Octal**: Una representación numérica, donde:
- `r` = 4
- `w` = 2
- `x` = 1  
Los valores se suman por cada grupo. Ejemplo:  
`rwxr-xr--` → `7` (propietario) `5` (grupo) `4` (otros) → `754`.

---

## Uso de `chmod`
- El comando chmod en sistemas Unix y similares se utiliza para modificar los permisos de acceso de archivos y directorios. Estos permisos controlan quién puede leer, escribir o ejecutar el archivo o directorio. chmod es clave para gestionar la seguridad y el control de acceso en el sistema.
### Cambiar permisos usando notación simbólica
- #### La sintaxis básica es:
    - `chmod [quién][operador][permisos] archivo`

- **Quién**:
  - `u`: Propietario (user)
  - `g`: Grupo (group)
  - `o`: Otros (others)
  - `a`: Todos (all)
- **Operador**:
  - `+`: Añadir permiso
  - `-`: Quitar permiso
  - `=`: Establecer permiso exacto
- **Permisos**: Combinación de `r`, `w` y/o `x`.

#### Ejemplo:

- Añadir permiso de ejecución al propietario:
    - `chmod u+x archivo`
- Quitar permisos de escritura a otros:
    - `chmod o-w archivo`

### Cambiar permisos usando notación octal
- ### Notación Octal en Unix/Linux
    La **notación octal** es una forma compacta y numérica de representar los permisos de archivos y directorios en sistemas Unix/Linux. En esta notación, los permisos se describen usando un número de **tres dígitos** (a veces cuatro, si se incluye un permiso especial como `setuid` o `sticky bit`).

- #### **La sintaxis básica es**:
    - `chmod [permisos_octal] archivo`

#### Ejemplo:

- Establecer permisos `rwx` para el propietario, `r-x` para el grupo y `---` para otros:

    - `chmod 750 archivo`
        - El código chmod 750 archivo establece permisos específicos para el archivo o directorio llamado archivo.

---

## Permisos Especiales

1. **Setuid (`s`)**: Si se configura en un archivo ejecutable, permite que los usuarios ejecuten el archivo con los privilegios del propietario.

    - `chmod u+s archivo`

2. **Setgid (`s`)**: Similar al `setuid`, pero aplica al grupo.

    - `chmod g+s archivo`
 
3. **Sticky Bit (`t`)**: En un directorio, permite que solo el propietario de un archivo lo elimine.
    - `chmod +t directorio`


---
## Ver Permisos de un Archivo
- Usa el comando `ls` con la opción `-l`:
    - `ls -l archivo`

# Conclusión

La gestión de permisos en Unix/Linux mediante `chmod` es esencial para garantizar la seguridad y el control de acceso en archivos y directorios. La notación octal ofrece una forma compacta y eficiente de definir permisos, permitiendo al propietario, grupo y otros usuarios interactuar de manera específica con los recursos, según las necesidades del sistema o proyecto.







