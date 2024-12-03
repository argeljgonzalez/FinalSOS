# Lenguaje de Bajo Nivel

## **Definición**
Un **lenguaje de bajo nivel** es un tipo de lenguaje de programación que proporciona poca o ninguna abstracción de los detalles del hardware. Permite interactuar directamente con componentes como registros, memoria y CPU.

### **Características principales:**
1. **Cercanía al hardware:**  
   Trabajan casi directamente con las instrucciones de la máquina.

2. **Alta eficiencia:**  
   Generan código que se ejecuta rápidamente porque es similar al ensamblador.

3. **Menor portabilidad:**  
   Dependen de la arquitectura específica del hardware.

4. **Complejidad:**  
   Son difíciles de aprender y manejar debido a la necesidad de trabajar con detalles técnicos.

**Ejemplos:**  
- Lenguaje ensamblador.  
- Lenguajes como C en ciertos casos.

---

# C como Lenguaje de Bajo Nivel

Aunque C es clasificado como un lenguaje de nivel medio, tiene características que lo acercan a los lenguajes de bajo nivel.

## **Razones para considerarlo de bajo nivel:**

1. **Acceso directo a memoria:**  
   Utiliza punteros para trabajar con direcciones de memoria.
   ```c
   int x = 10;
   int *ptr = &x; // Dirección de memoria de x
   printf("Valor de x: %d\n", *ptr);

2. **Control de hardware:**
   Permite interactuar directamente con registros y dispositivos.

3. **Gestión manual de memoria**:
El programador debe reservar y liberar memoria manualmente.
   ```c
    int *array = (int *)malloc(5 * sizeof(int));
    free(array);

4. **Compatibilidad con ensamblador:**
Puedes incluir instrucciones de ensamblador dentro del código.

5. **Dependencia del sistema:**
Los programas escritos en C dependen del hardware y del sistema operativo.
