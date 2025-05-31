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


# Apuntes: 2.3 Designing Algorithms

---

## ¿Qué es diseñar algoritmos?

Diseñar algoritmos consiste en construir una **solución paso a paso** para resolver un problema computacional de manera eficiente, correcta y general. No es solo codificar: es **pensar cómo resolver** el problema antes de programarlo.

---

## Etapas del diseño de algoritmos

1. **Comprensión del problema**  
   - ¿Qué se pide exactamente?
   - ¿Qué entradas se reciben?
   - ¿Qué salida se espera?

2. **Diseño de una estrategia**
   - Selección de un enfoque adecuado:
     - Divide y vencerás
     - Programación dinámica
     - Algoritmos voraces
     - Fuerza bruta (en problemas pequeños)

3. **Especificación del algoritmo**
   - Pseudocódigo o lenguaje informal

4. **Análisis**
   - Tiempo de ejecución
   - Uso de espacio (memoria)
   - Notación Big-O

5. **Implementación**
   - Traducir el algoritmo a código

6. **Prueba**
   - Validar con diferentes entradas, incluyendo casos límite

---

## Ejemplo: Buscar el número mayor en un arreglo

### Problema:
Dado un arreglo `A` con `n` números, encontrar el **valor máximo**.

---

### Diseño del algoritmo

**Estrategia**: Recorremos el arreglo una vez y vamos guardando el valor más alto encontrado.

---

### Pseudocódigo

```text
Maximo(A)
  max = A[1]
  for i = 2 to A.length
    if A[i] > max
      max = A[i]
  return max
```

### Ejemplo con Prueba de Escritorio:

```text
A = [4, 17, 3, 21, 8]
```

![image](https://github.com/user-attachments/assets/70417bff-0e94-412d-a2b4-67838321aad6)

### Resultado: 

El número mayor es: 21



# Resumen del Tema 3: "Characterizing Running Times" (Cormen et al., 2022)

En "Introduction to Algorithms" de Cormen et al., el Capítulo 3, "Characterizing Running Times" (Caracterización de los Tiempos de Ejecución), se centra en la importancia de analizar la eficiencia de los algoritmos utilizando la notación asintótica. En lugar de calcular el tiempo de ejecución exacto de un algoritmo, que a menudo es complejo y no es crucial para entradas grandes, este capítulo enfatiza la "tasa de crecimiento" del tiempo de ejecución.

Los puntos clave incluyen:

* Eficiencia Asintótica: El objetivo principal es entender cómo el tiempo de ejecución de un algoritmo aumenta con el tamaño de la entrada (n) a medida que n tiende a infinito. Para entradas lo suficientemente grandes, las constantes multiplicativas y los términos de orden inferior en la función de tiempo de ejecución se vuelven insignificantes en comparación con el término dominante relacionado con n.
* Notación Asintótica: Introduce las notaciones asintóticas estándar para simplificar el análisis de algoritmos. Las más relevantes son:
* Notación Big-O (O): Proporciona un límite superior para el tiempo de ejecución de un algoritmo. Se utiliza para describir el peor escenario o el límite máximo del tiempo de ejecución.
* Notación Omega (Ω): Define un límite inferior para el tiempo de ejecución, describiendo el mejor escenario.
* Notación Theta (Θ): Ofrece un límite ajustado (tanto superior como inferior) para el tiempo de ejecución, lo que significa que el tiempo de ejecución del algoritmo se encuentra dentro de un factor constante de la función dada para entradas suficientemente grandes.

En resumen, el capítulo enseña cómo la notación asintótica permite comparar algoritmos basándose en cómo su tiempo de ejecución escala con el tamaño de la entrada, siendo una herramienta fundamental para predecir el rendimiento en escenarios del mundo real.


# Talleres 

## Taller: Codificación de algoritmo

Realice la codificación del siguiente algoritmo:

![image](https://github.com/user-attachments/assets/11434f94-98ed-41b1-ad7e-1a6b74e6283a)

Registre su aporte con n descripción de la manera en que desarrolló y cual es el resultado.

* Descripción del Desarrollo en Java
Estructura de Clase: En Java, el código debe estar dentro de una clase. He creado una clase MergeAlgorithm para contener el método MERGE y el método main para las pruebas.

* Método MERGE:

Creación de Arrays Temporales (L y R):

En Java, la creación de arrays se hace con new int[tamaño]. Por lo tanto, int[] L = new int[n_L]; y int[] R = new int[n_R]; se utilizan para declarar e inicializar los arrays temporales con el tamaño adecuado.
Los bucles for son para copiar los elementos de A a L y R.
Inicialización de Índices: Las variables i, j, y k se declaran e inicializan como variables int dentro del método.

Proceso de Fusión Principal (Bucle while):

La estructura del bucle while (i < n_L && j < n_R) es la misma.
Las comparaciones (L[i] <= R[j]) y las asignaciones (A[k] = L[i]) son directas.
Los incrementos (i++, j++, k++) son la forma idiomática de incrementar en Java.
Copiado de Elementos Restantes: Los dos bucles while adicionales para copiar los elementos restantes de L o R también se traducen directamente.

Método main (Ejemplos de Uso):

El método public static void main(String[] args) es el punto de entrada para ejecutar la aplicación Java.
Dentro de main, se definen arrays de prueba (int[] arr1 = {...};).
Se llama al método MERGE con los arrays y los índices apropiados.
Para imprimir los arrays, se utiliza java.util.Arrays.toString(array) que es muy útil para obtener una representación legible de un array en Java.

Implementacion del codigo en java:

![image](https://github.com/user-attachments/assets/a5cb6683-e5f2-4114-8d7f-0f6f326aaaff)


## Taller: Análisis de algoritmos - Regla del límite

Desarrolle lo siguiente:

![image](https://github.com/user-attachments/assets/9408f610-100e-48a1-8c58-ffc8959fc71f)


# Notación Big-O (O mayúscula)

Una función `f(n)` pertenece a `O(g(n))` si existen constantes positivas `c` y `n₀` tales que para todo `n ≥ n₀`, se cumple que:

```
f(n) ≤ c · g(n)
```

---

## Parte 1: Análisis con `f(n) = n³ + 9n² log(n)` y `g(n) = n² log(n)`

### Comprobar si `f(n) ∈ O(g(n))`

Tenemos:

```
f(n) = n³ + 9n² log(n)  
g(n) = n² log(n)
```

Queremos demostrar que `f(n) ∈ O(g(n))`, es decir, que existen constantes `c > 0` y `n₀ > 0` tales que:

```
n³ + 9n² log(n) ≤ c · n² log(n)   ∀ n ≥ n₀
```

Dividimos ambos lados entre `n² log(n)` (asumiendo `n > 1` para que `log(n) > 0`):

```
(n³ / n² log(n)) + (9n² log(n) / n² log(n)) ≤ c  
⇒ (n / log(n)) + 9 ≤ c
```

A medida que `n → ∞`, el término `(n / log(n)) → ∞`. Esto implica que no podemos encontrar una constante finita `c` que satisfaga la desigualdad para todo `n ≥ n₀`.

Por ejemplo, si elegimos un `c`, siempre podremos encontrar un `n` suficientemente grande tal que:

```
(n / log(n)) + 9 > c
```

#### Conclusión:

```
f(n) ∉ O(g(n))
```

Esto tiene sentido porque `n³` crece mucho más rápido que `n² log(n)`. Formalmente:

```
lim (n → ∞) [ (n² log(n)) / (n³ + 9n² log(n)) ] 
= lim (n → ∞) [ (log(n)/n) + 9 ]⁻¹ = 0 ⇒ ∞
```

Como el límite tiende a infinito, `f(n)` no puede ser `O(g(n))`.

---

### Comprobar si `f(n) ∈ O(n²)`

Tenemos:

```
f(n) = n³ + 9n² log(n)
```

Queremos demostrar que `f(n) ∉ O(n²)`, es decir, no existen constantes `c > 0` y `n₀ > 0` tales que:

```
n³ + 9n² log(n) ≤ c · n²   ∀ n ≥ n₀
```

Dividimos ambos lados entre `n²` (asumiendo `n > 0`):

```
n + 9 log(n) ≤ c
```

A medida que `n → ∞`, el término `n + 9 log(n) → ∞`, por lo tanto no podemos encontrar un `c` que lo acote.

#### Conclusión:

```
f(n) ∉ O(n²)
```

Esto es coherente, ya que el término dominante en `f(n)` es `n³`, que crece más rápido que `n²`.

Formalmente:

```
lim (n → ∞) [ n² / (n³ + 9n² log(n)) ] = lim (n → ∞) [ 1 / (n + 9 log(n)) ] = 0 ⇒ ∞
```

---

## Parte 2: Demostración Formal con `f(n) = 2ⁿ` y `g(n) = 2²ⁿ`

### Comprobar si `f(n) ∈ O(g(n))`

Tenemos:

```
f(n) = 2ⁿ  
g(n) = 2²ⁿ = (2ⁿ)²
```

Queremos comprobar si existe una constante `c > 0` y `n₀ > 0` tal que:

```
2ⁿ ≤ c · 2²ⁿ  ∀ n ≥ n₀
```

Reescribimos la desigualdad:

```
2ⁿ ≤ c · (2ⁿ)² = c · 2ⁿ · 2ⁿ
```

Dividimos ambos lados entre `2ⁿ`:

```
1 ≤ c · 2ⁿ
```

A medida que `n → ∞`, `2ⁿ → ∞`. Podemos elegir cualquier `c > 0`, por ejemplo `c = 1`, y se cumple que:

```
1 ≤ 2ⁿ  ∀ n ≥ 0
```

#### Conclusión:

```
f(n) ∈ O(g(n))
```

Formalmente:

```
lim (n → ∞) [ g(n) / f(n) ] = lim (n → ∞) [ 2²ⁿ / 2ⁿ ] = lim (n → ∞) [ 2ⁿ ] = ∞
```

El límite es infinito, pero como `f(n)/g(n) → 0`, se cumple que `f(n) ∈ O(g(n))`.

---

### Comprobar si `g(n) ∈ O(f(n))`

Tenemos:

```
g(n) = 2²ⁿ  
f(n) = 2ⁿ
```

Queremos comprobar si:

```
2²ⁿ ≤ c · 2ⁿ  ∀ n ≥ n₀
```

Reescribimos la desigualdad:

```
(2ⁿ)² ≤ c · 2ⁿ  
⇒ 2ⁿ · 2ⁿ ≤ c · 2ⁿ
```

Dividimos ambos lados entre `2ⁿ`:

```
2ⁿ ≤ c
```

A medida que `n → ∞`, `2ⁿ → ∞`. No se puede encontrar una constante finita `c` que lo acote.

#### Conclusión:

```
g(n) ∉ O(f(n))
```

Formalmente:

```
lim (n → ∞) [ f(n) / g(n) ] = lim (n → ∞) [ 2ⁿ / 2²ⁿ ] = lim (n → ∞) [ 1 / 2ⁿ ] = 0
```

Pero:

```
lim (n → ∞) [ g(n) / f(n) ] = 2ⁿ → ∞
```

Por lo tanto, `g(n)` no pertenece a `O(f(n))`.
