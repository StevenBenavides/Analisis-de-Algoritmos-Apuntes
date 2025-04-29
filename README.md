# Analisis-de-Algoritmos-Apuntes
En este Git se agregaran apuntes de la materia de análisis de algoritmos 


# Apuntes: El Rol de los Algoritmos en la Computación

**Basado en:**
- Cormen et al., 2022 - *Introduction to Algorithms* (Capítulo 1)
- Brassard & Bratley, 2006 - *Fundamentals of Algorithmics* (Capítulo 1)

---

## 1. ¿Qué es un Algoritmo?

Un **algoritmo** es una secuencia **bien definida** de pasos para resolver un problema o realizar una tarea específica.

### Características:
- **Precisión**: cada paso es claro y definido.
- **Entrada**: uno o más valores de entrada.
- **Salida**: al menos un resultado.
- **Finitud**: termina en un número finito de pasos.
- **Efectividad**: cada paso puede realizarse en un tiempo razonable.

---

## 2. Algoritmos como Tecnología

Los algoritmos son una **tecnología esencial** en computación.

### Ventajas:
- Mejoran el **rendimiento** sin necesidad de cambiar el hardware.
- Hacen que los sistemas **escalen** con grandes volúmenes de datos.
- Permiten resolver problemas en menos tiempo y con menos recursos.

### Ejemplo Comparativo:
| Método | Complejidad | Idea Básica |
|--------|-------------|-------------|
| Búsqueda lineal | O(n) | Revisar cada elemento |
| Búsqueda binaria | O(log n) | Dividir y conquistar en lista ordenada |

---

## 3. Preliminares (Brassard & Bratley)

### Conceptos Clave:
- **Abstracción**: simplificar el problema sin perder lo esencial.
- **Modelo RAM**: tiempo constante para operaciones básicas.
- **Costo de un algoritmo**:
  - Tiempo (velocidad de ejecución)
  - Espacio (uso de memoria)

### Estrategias comunes:
- **Divide y vencerás**
- **Algoritmos aproximados** (cuando la solución exacta es costosa)

---

## Ejemplo: Búsqueda Binaria vs. Búsqueda Lineal

### Problema:
Buscar el número `23` en la lista:  
`[4, 8, 15, 16, 23, 42, 50, 60]`

---

### Búsqueda Lineal

- Empieza en el primer número.
- Compara uno por uno.
- Peor caso: O(n) comparaciones.

**Pasos**:  
4 → ❌  
8 → ❌  
15 → ❌  
16 → ❌  
23 → ✅ (5 pasos)

---

### Búsqueda Binaria

- Requiere lista ordenada.
- Divide el rango a la mitad cada vez.
- Complejidad: O(log n)

**Pasos**:
1. Centro = 16 → 23 > 16 → derecha  
2. Centro = 42 → 23 < 42 → izquierda  
3. Único número: 23 → ✅




# Apuntes: Insertion Sort y Análisis de Algoritmos

**Lecturas:**
- Cormen et al., 2022 - *Introduction to Algorithms* (Capítulo 2: Getting Started)
- Brassard & Bratley, 2006 - *Fundamentals of Algorithmics* (Capítulo 2: Algoritmia elemental)

---

## 2.1 Insertion Sort

### ¿Qué es?

**Insertion Sort** es un algoritmo de ordenamiento que construye una lista ordenada **uno a uno**, insertando cada nuevo elemento en su lugar correcto.

### ¿Cómo funciona?

1. Se empieza desde el segundo elemento.
2. Se compara con los elementos anteriores.
3. Se inserta en el lugar correspondiente.

### Pseudocódigo (Cormen):

```text
for j = 2 to A.length
    key = A[j]
    i = j - 1
    while i > 0 and A[i] > key
        A[i + 1] = A[i]
        i = i - 1
    A[i + 1] = key
```

## Ventajas y Desventajas de Insertion Sort

| Ventajas                                | Desventajas                          |
|-----------------------------------------|--------------------------------------|
| Fácil de implementar                    | Ineficiente para arreglos grandes    |
| Estable (mantiene orden relativo)       | Complejidad cuadrática: O(n²)        |
| In-place (no necesita espacio extra)    | No se recomienda para entradas grandes (`n` elevado) |

---

## Tema 2.2 - Analyzing Algorithms

### ¿Qué se analiza en un algoritmo?

-  **Tiempo de ejecución**
-  **Uso de espacio**
-  Se mide el crecimiento usando **notación Big-O**

---

### Complejidades Comunes

| Notación | Tipo         | Ejemplo                          |
|----------|--------------|----------------------------------|
| O(1)     | Constante    | Acceder a un elemento de un array |
| O(log n) | Logarítmica  | Búsqueda binaria                 |
| O(n)     | Lineal       | Recorrer un arreglo              |
| O(n²)    | Cuadrática   | Insertion Sort, Bubble Sort      |

---

## Brassard & Bratley: Algoritmia Elemental
  
### Conceptos clave del Capítulo 2

- Presentan **algoritmos básicos** como ordenamiento y búsqueda.
- Introducen el concepto de **eficiencia computacional** (tiempo y espacio).
- Proponen el uso de **pruebas de escritorio** para validar el comportamiento de un algoritmo.
- Enfatizan la importancia de la **abstracción y el análisis** antes de programar.

---

## Ejemplo con Prueba de Escritorio: Insertion Sort

### Entrada

```text
A = [8, 5, 2, 9]
```
![image](https://github.com/user-attachments/assets/4be04c3c-b1ef-4d82-acfb-dd99dc554d87)

### Resultado
```text
[2, 5, 8, 9]
```
