# Tarea-1-Estructuras-Iteractivas
# 🔄 Tarea 1: Estructuras Iterativas Anidadas con Variables de Seguimiento

Este repositorio contiene una solución en consola diseñada para ilustrar el comportamiento interno de los bucles anidados utilizando técnicas de rastreo (tracing) mediante contadores y acumuladores en tiempo real.

**Autor:** Cristian Gómez T.  
**Materia:** Programación / Estructuras Iterativas  

---

## 📋 1. Planteamiento del Ejercicio

**Objetivo:** Desarrollar un algoritmo iterativo utilizando bucles anidados (un bucle dentro de otro bucle) y validar minuciosamente su comportamiento mediante variables de seguimiento. Esto permite auditar el flujo exacto de ejecuciones y sumatorias internas en cada ciclo de memoria.

### Caso de Estudio Seleccionado:
Generar y analizar la tabla de multiplicar de los rangos numéricos **1 al 3** (Matriz de 3x3), registrando de forma acumulativa:
1. Las operaciones individuales de multiplicación en formato de cuadrícula.
2. El número total de veces que el procesador ingresa al bucle más interno (frecuencia de iteración).
3. La suma total agregada de todos los productos resultantes generados por el algoritmo.

---

## 📊 2. Análisis de Entradas, Procesos y Salidas

| Componente | Detalle Técnico | Variables Asociadas |
| :--- | :--- | :--- |
| **Entradas** | Rangos constantes predefinidos para la matriz: <ul><li>Límite del bucle externo (Fila): `1` a `3`</li><li>Límite del bucle interno (Columna): `1` a `3`</li></ul> | `fila` (Entero)<br>`columna` (Entero) |
| **Procesos** | <ul><li>**Anidamiento:** Bucle externo controla las filas; el interno procesa las columnas completas por cada fila.</li><li>**Cálculo:** Multiplicación directa de índices: `producto = fila * columna`.</li><li>**Seguimiento de Frecuencia:** Contador incremental simple por cada paso interno.</li><li>**Seguimiento de Masa:** Acumulación del producto actual al total global.</li></ul> | <ul><li>`producto = fila * columna`</li><li>`contador = contador + 1`</li><li>`suma = suma + producto`</li></ul> |
| **Salidas** | <ul><li>Visualización de cada celda matemática calculada: `Fila x Columna = Producto`.</li><li>Métrica final de iteraciones totales completadas.</li><li>Suma aritmética absoluta de la matriz de datos.</li></ul> | `contador` (Entero)<br>`suma` (Real/Entero) |

---

## 💻 3. Pseudocódigo (Lógica de Control)

```text
Algoritmo Bucle_Anidado_Seguimiento
    // Declaración de variables
    Definir fila, columna, producto Como Entero
    Definir contador, suma Como Entero
    
    // Inicialización de variables de seguimiento (Estado Inicial)
    contador <- 0
    suma <- 0
    
    Escribir "=== EJECUCIÓN DEL BUCLE ANIDADO ==="
    Escribir ""
    
    // Bucle Externo (Controla las filas)
    Para fila <- 1 Hasta 3 Con Paso 1 Hacer
        Escribir "👉 Iniciando Bucle Externo - Fila: ", fila
        
        // Bucle Interno (Controla las columnas)
        Para columna <- 1 Hasta 3 Con Paso 1 Hacer
            // Cálculo matemático básico
            producto <- fila * columna
            
            // Actualización de variables de seguimiento
            contador <- contador + 1
            suma <- suma + producto
            
            // Impresión del log paso a paso
            Escribir "   [Iteracion Int: ", contador, "] -> ", fila, " x ", columna, " = ", producto
        FinPara
        
        Escribir "---------------------------------------"
    FinPara
    
    // Salidas Finales de Auditoría
    Escribir ""
    Escribir "=== REPORTE FINAL DE VARIABLES DE SEGUIMIENTO ==="
    Escribir "Total de iteraciones realizadas en el bucle interno: ", contador
    Escribir "La suma total de todos los resultados es: ", suma
FinAlgoritmo
```

---

## ☕ 4. Código Fuente (Java)

La traducción a **Java** utiliza bucles estructurados `for` ideales para rangos numéricos conocidos, imprimiendo logs tabulados para una legibilidad superior en la terminal.

```java
public class EstructurasIterativas {
    public static void main(String[] args) {
        // 1. Declaración e inicialización de variables de seguimiento
        int contador = 0;
        int suma = 0;
        int producto;

        System.out.println("=== EJECUCIÓN DEL BUCLE ANIDADO ===");
        System.out.println("===================================");

        // 2. Bucle Externo: Controla el multiplicador primario (Fila)
        for (int fila = 1; fila <= 3; fila++) {
            System.out.println("\n👉 Iniciando Bucle Externo - Fila: " + fila);
            System.out.println("   ---------------------------------------");

            // 3. Bucle Interno: Controla el multiplicador secundario (Columna)
            for (int columna = 1; columna <= 3; columna++) {
                // Cálculo de la celda
                producto = fila * columna;

                // Actualización de los registros de seguimiento
                contador++;       // Registra la iteración actual
                suma += producto; // Acumula el resultado aritmético

                // Impresión detallada en pantalla (Rastreo)
                System.out.printf("   [Iteración Int: %d] -> %d x %d = %d\n", 
                                  contador, fila, columna, producto);
            }
        }

        // 4. Salida de resultados consolidados de auditoría
        System.out.println("\n=================================================");
        System.out.println("=== REPORTE FINAL DE VARIABLES DE SEGUIMIENTO ===");
        System.out.println("=================================================");
        System.out.println("✔ Total de iteraciones realizadas (Bucle Interno): " + contador);
        System.out.println("✔ La suma acumulada de todos los resultados es: " + suma);
        System.out.println("=================================================");
    }
}
```

---

## 🧮 5. Cuadro de Prueba Manual (Trace Table / Matriz Resultante)

Para validar la consistencia de los datos, el procesador ejecuta de forma invisible la siguiente secuencia de almacenamiento:

| Fila (i) | Columna (j) | Operación (i × j) | Contador (Estado) | Suma (Acumulado) |
| :---: | :---: | :---: | :---: | :---: |
| 1 | 1 | 1 | 1 | 1 |
| 1 | 2 | 2 | 2 | 3 |
| 1 | 3 | 3 | 3 | 6 |
| 2 | 1 | 2 | 4 | 8 |
| 2 | 2 | 4 | 5 | 12 |
| 2 | 3 | 6 | 6 | 18 |
| 3 | 1 | 3 | 7 | 21 |
| 3 | 2 | 6 | 8 | 27 |
| 3 | 3 | 9 | 9 | **36** |

---

## 🛠️ Tecnologías y Conceptos Clave Utilizados
*   **Java Standard Edition (Java SE)**.
*   **Bucles For Anidados:** Patrón algorítmico esencial para recorrer colecciones bidimensionales (matrices y planos cartesianos).
*   **Variables de Control Fijo:** Control exacto de cotas numéricas para evitar ciclos infinitos en el hilo principal del software.
*   **Format Output (`printf`):** Inserción limpia de marcadores de posición enteros (`%d`) para generar reportes estructurados.
