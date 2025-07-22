# Apuntes Del Segundo Bimestre 
## Libros a usar: 
* Cormen et al., 2022 - Introduction to Algorithms 
* Brassard & Bratley, 2006 - Fundamentals of Algorithmics 

## Tema 6: Algoritmos Voraces (Brassard & Bratley, 2006)
Los algoritmos voraces (o greedy algorithms) son una estrategia algorítmica que construye una solución a un problema tomando la mejor elección posible en cada paso, con la esperanza de encontrar una solución óptima global. En otras palabras, en cada etapa de la construcción de la solución, se elige el elemento que parece más prometedor en ese momento, sin considerar las consecuencias futuras de esa elección.

Características clave:
* Elección localmente óptima: En cada paso, el algoritmo toma una decisión que es la mejor posible en ese instante, basándose en la información disponible.

* Irrevocabilidad: Una vez que se toma una decisión, esta no se revoca. El algoritmo no retrocede para reconsiderar una elección anterior, incluso si más adelante resulta que esa elección no fue la mejor globalmente.

* Construcción paso a paso: La solución se construye de forma incremental, añadiendo elementos uno por uno hasta que se completa.

* Cuándo funcionan los algoritmos voraces: Aunque son simples y eficientes, los algoritmos voraces no garantizan una solución óptima para todos los problemas. Sin embargo, son muy efectivos para una clase específica de problemas que poseen dos propiedades fundamentales:

* Propiedad de la elección voraz (Greedy Choice Property): Una solución óptima global puede alcanzarse realizando una elección localmente óptima. Es decir, la elección más "prometedora" en un momento dado forma parte de alguna solución óptima.

* Propiedad de la subestructura óptima (Optimal Substructure Property): Una solución óptima del problema contiene soluciones óptimas de sus subproblemas. Esto significa que si eliminamos la elección voraz de una solución óptima, lo que queda es una solución óptima para el subproblema resultante.

Ejemplos comunes de problemas que se resuelven con algoritmos voraces:

- Problema del cambio de monedas: Dar la menor cantidad de monedas para una cantidad de dinero específica (asumiendo un sistema de monedas "estándar").

- Problema de la mochila fraccionaria: Maximizar el valor de los artículos que se pueden empacar en una mochila, donde los artículos pueden dividirse.

- Planificación de actividades: Seleccionar el máximo número de actividades que no se solapen, dadas sus horas de inicio y fin.

- Árbol de recubrimiento mínimo (MST): Algoritmos como Prim y Kruskal son ejemplos clásicos de algoritmos voraces para encontrar el árbol de recubrimiento mínimo de un grafo.

- Algoritmo de Dijkstra: Para encontrar la ruta más corta desde un nodo fuente a todos los demás nodos en un grafo con pesos de aristas no negativos.

Ventajas:

Simplicidad: Son generalmente fáciles de entender e implementar.

Eficiencia: A menudo, son más eficientes en términos de tiempo de ejecución que otras estrategias como la programación dinámica, si el problema lo permite.

Desventajas:

No siempre óptimos: Como se mencionó, no garantizan una solución óptima para todos los problemas. Es crucial verificar si el problema posee las propiedades de elección voraz y subestructura óptima.

Puede llevar a soluciones subóptimas: Si las propiedades no se cumplen, la elección localmente óptima puede conducir a un resultado globalmente deficiente.

Resumen:

Los algoritmos voraces son una heurística poderosa y eficiente cuando las propiedades de elección voraz y subestructura óptima se cumplen. Su enfoque de "tomar lo mejor ahora" los hace atractivos por su simplicidad y velocidad, pero es fundamental entender sus limitaciones y cuándo aplicarlos correctamente.

## 6.4 Grafos: Caminos Mínimos (Brassard & Bratley, 2006)
En el contexto de los algoritmos voraces, la búsqueda de caminos mínimos en grafos es un problema fundamental y ampliamente estudiado. Un camino mínimo en un grafo con pesos en sus aristas es aquel que, partiendo de un nodo origen, llega a un nodo destino (o a todos los demás nodos) sumando el menor peso posible de las aristas que lo componen.

Definiciones clave:
* Grafo ponderado: Un grafo donde cada arista tiene asociado un valor numérico (peso o costo). Este peso puede representar distancia, tiempo, costo, etc.

* Camino: Una secuencia de vértices y aristas que conecta dos vértices en el grafo.

* Longitud de un camino: La suma de los pesos de las aristas que componen el camino.

* Camino mínimo: Un camino entre dos vértices cuya longitud es la menor posible.

* El problema del camino mínimo desde una única fuente: El objetivo es encontrar los caminos mínimos desde un vértice de origen dado a todos los demás vértices del grafo. Para esto, los algoritmos voraces son una técnica comúnmente aplicada.

Algoritmos Voraces para Caminos Mínimos: Los dos algoritmos más relevantes y estudiados que utilizan una estrategia voraz para encontrar caminos mínimos son:

1. Algoritmo de Dijkstra
El algoritmo de Dijkstra es un clásico ejemplo de un algoritmo voraz para encontrar los caminos más cortos desde un único nodo fuente a todos los demás nodos en un grafo con pesos de aristas no negativos.

¿Cómo funciona (idea voraz)?

Inicialización: Se asigna una distancia de 0 al nodo origen y una distancia de infinito a todos los demás nodos. Se mantiene un conjunto de nodos "visitados" o "definitivos".

Iteración voraz: En cada paso, el algoritmo selecciona el nodo no visitado con la distancia más pequeña conocida desde el origen. Esta es la elección voraz: se asume que este nodo ya tiene su distancia mínima final, ya que no hay forma de acortar su camino pasando por otros nodos que aún no han sido procesados (porque si los hubiera, su distancia sería menor y ya habrían sido seleccionados).

Actualización (Relajación): Una vez seleccionado el nodo, se examinan todos sus vecinos. Para cada vecino, se calcula una nueva distancia tentativa sumando la distancia del nodo actual más el peso de la arista que los conecta. Si esta nueva distancia es menor que la distancia actual del vecino, se actualiza la distancia del vecino.

Repetición: Los pasos 2 y 3 se repiten hasta que todos los nodos sean visitados o hasta que no haya más nodos alcanzables.

Propiedades que lo hacen voraz y correcto:

Elección voraz: En cada paso, se elige el vértice con la etiqueta de distancia mínima entre los vértices no visitados. Esta elección es óptima localmente.

Subestructura óptima: Si un camino P_uv es un camino mínimo de u a v, y w está en P_uv, entonces el subcamino P_u es un camino mínimo de u a w.

Limitaciones:

No funciona con pesos negativos en las aristas: Si existen aristas con pesos negativos, el algoritmo de Dijkstra puede dar resultados incorrectos. Esto se debe a que la suposición de que la primera vez que se visita un nodo, su distancia es la mínima, ya no es válida si un camino más largo, que incluye una arista negativa, podría llevar a un camino final más corto.

2. Algoritmo de Bellman-Ford
A diferencia de Dijkstra, el algoritmo de Bellman-Ford sí puede manejar grafos con pesos de aristas negativos. Aunque también resuelve el problema del camino más corto desde una única fuente, no es puramente voraz en el mismo sentido que Dijkstra, ya que no toma una única "mejor" decisión en cada paso que sea irrevocablemente localmente óptima. Sin embargo, su proceso de relajación iterativa se basa en una idea similar de mejora progresiva.

¿Cómo funciona (idea de relajación iterativa)?

Inicialización: Al igual que Dijkstra, se asigna 0 al nodo origen y infinito a los demás.

Relajación iterativa: El algoritmo itera ∣V∣−1 veces (donde ∣V∣ es el número de vértices). En cada iteración, se recorren todas las aristas del grafo. Para cada arista (u,v) con peso w(u,v):

Si distancia[u]+w(u,v)<distancia[v], entonces se actualiza distancia[v] a distancia[u]+w(u,v). Esto se conoce como "relajación" de la arista.

Detección de ciclos negativos: Después de las ∣V∣−1 iteraciones, se realiza una iteración adicional. Si durante esta iteración se puede seguir relajando alguna arista (es decir, distancia[u]+w(u,v)<distancia[v] para alguna arista (u,v)), significa que el grafo contiene un ciclo de peso negativo accesible desde el origen. En este caso, no existe un camino mínimo bien definido (porque se podría recorrer el ciclo negativo infinitas veces para disminuir la distancia indefinidamente).

¿Por qué es importante considerar Bellman-Ford aquí?

Aunque Bellman-Ford no es un algoritmo voraz "puro" en el sentido de una elección localmente óptima e irrevocable en cada paso, se basa en la idea de relajación, que es una forma de optimización incremental. En el contexto de los caminos mínimos, ambos algoritmos son fundamentales y a menudo se estudian en conjunto para ilustrar diferentes enfoques a problemas de optimización en grafos. Brassard y Bratley lo incluyen en esta sección por su relevancia en la resolución de caminos mínimos, incluso si su clasificación como "voraz" es más matizada que la de Dijkstra.

Conclusión:

Los algoritmos voraces, como el de Dijkstra, son una herramienta poderosa para encontrar caminos mínimos en grafos, siempre que los pesos de las aristas sean no negativos. Cuando existen pesos negativos, el algoritmo de Bellman-Ford se convierte en la solución preferida, aunque su enfoque de relajación iterativa difiere sutilmente del modelo voraz estricto de Dijkstra. Comprender ambos es crucial para abordar eficazmente los problemas de caminos mínimos en la teoría de grafos.

## 4. Divide-and-Conquer (Cormen et al., 2022) y 7. Divide y vencerás (Brassard & Bratley, 2006)
El paradigma "Divide y Vencerás" (Divide-and-Conquer en inglés) es una de las estrategias más poderosas y fundamentales en el diseño de algoritmos. Ambos libros, "Introduction to Algorithms" de Cormen et al. y "Fundamentos de Algoritmia" de Brassard & Bratley, dedican secciones importantes a este tema, destacando su estructura y aplicaciones.

Concepto General

El paradigma Divide y Vencerás aborda un problema de gran tamaño dividiéndolo en subproblemas más pequeños del mismo tipo. Estos subproblemas se resuelven de forma recursiva, y luego las soluciones de los subproblemas se combinan para obtener la solución del problema original.

Este paradigma se describe típicamente en tres pasos:

* Dividir (Divide): El problema se descompone en dos o más subproblemas independientes (o casi independientes) que son instancias más pequeñas del mismo problema original.

* Conquistar (Conquer): Los subproblemas se resuelven recursivamente. Si el tamaño de un subproblema es lo suficientemente pequeño (caso base), se resuelve directamente.

* Combinar (Combine): Las soluciones de los subproblemas se unen para construir la solución del problema original.

Características y Propiedades

* Recursividad: La naturaleza recursiva es inherente al paradigma, ya que los subproblemas se resuelven de la misma manera que el problema original.

* Eficiencia: A menudo, los algoritmos de Divide y Vencerás resultan en una complejidad temporal mucho mejor que los enfoques directos o ingenuos. Esto se debe a que dividir un problema grande en subproblemas más pequeños y manejables puede reducir drásticamente el número total de operaciones.

* Análisis de Recurrencias: El tiempo de ejecución de un algoritmo de Divide y Vencerás se expresa típicamente mediante una ecuación de recurrencia. Métodos como el método de sustitución, el método del árbol de recursión y el teorema maestro (este último muy detallado en Cormen et al.) son herramientas fundamentales para resolver estas recurrencias y determinar la complejidad asintótica del algoritmo.

* Independencia de subproblemas: Idealmente, los subproblemas generados son independientes, lo que permite resolverlos en paralelo. Sin embargo, en muchos casos, la fase de "combinar" requiere un trabajo significativo.

Ejemplos de Algoritmos Divide y Vencerás

Ordenación por mezcla (Merge Sort):

* Dividir: Divide la lista no ordenada en dos sublistas de aproximadamente la mitad del tamaño.

* Conquistar: Ordena cada sublista recursivamente.

* Combinar: Fusiona las dos sublistas ordenadas para producir una única lista ordenada.

Ordenación rápida (Quick Sort):

* Dividir: Elige un elemento (pivote) y particiona la lista en dos sublistas: elementos menores que el pivote y elementos mayores que el pivote.

* Conquistar: Ordena recursivamente las dos sublistas.

* Combinar: Las sublistas ya están ordenadas en relación con el pivote, por lo que la combinación es trivial (la lista ya está ordenada).

Búsqueda binaria (Binary Search):

* Dividir: Compara el elemento a buscar con el elemento central de un array ordenado.

* Conquistar: Si no es el elemento central, recursivamente busca en la mitad izquierda o derecha del array.

* Combinar: Trivial (el elemento se encuentra o no).

Multiplicación de matrices (Algoritmo de Strassen):

* Dividir: Divide las matrices en submatrices más pequeñas.

* Conquistar: Realiza un número menor de multiplicaciones de submatrices recursivamente (7 en lugar de 8).

* Combinar: Combina los resultados de las submultiplicaciones con sumas y restas.

Problema de la submatriz de suma máxima (Maximum-subarray problem) (Cormen et al.): Encuentra el subarreglo contiguo dentro de un array de números (con al menos un número positivo) cuya suma es la mayor.

Ventajas del paradigma

* Resolución de problemas complejos: Permite abordar problemas que de otra manera serían intratables, al descomponerlos en partes más manejables.

* Paralelización: La independencia de los subproblemas en la fase de "dividir" a menudo facilita la implementación paralela de los algoritmos.

* Eficiencia: Como se mencionó, puede llevar a algoritmos con una complejidad temporal significativamente mejorada.

Desafíos y Consideraciones

* Costo de la división y combinación: En algunos problemas, el costo de dividir el problema o de combinar las soluciones puede ser tan alto que anule los beneficios de la recursión.

* Overhead de la recursión: La recursión introduce un overhead en términos de llamadas a funciones y uso de la pila de llamadas, lo que puede ser un factor en la eficiencia práctica para problemas muy pequeños o con una profundidad de recursión excesiva.

* Problemas con subproblemas solapados: Si los subproblemas no son independientes y se solapan (es decir, el mismo subproblema se resuelve múltiples veces), el paradigma "Divide y Vencerás" puro puede ser ineficiente. En estos casos, la programación dinámica suele ser una alternativa más adecuada, ya que almacena las soluciones de los subproblemas para evitar recálculos.

En resumen, el paradigma Divide y Vencerás es una herramienta esencial en la caja de herramientas de cualquier diseñador de algoritmos, ofreciendo una metodología estructurada para resolver una amplia gama de problemas de manera eficiente.

## 10. Algoritmos Probabilistas (Brassard & Bratley, 2006)
Los algoritmos probabilistas (o algoritmos aleatorizados) son aquellos que, en el transcurso de su ejecución, toman decisiones basándose en resultados aleatorios, típicamente generados por una secuencia de bits aleatorios. A diferencia de los algoritmos deterministas, que siempre producen el mismo resultado para la misma entrada, un algoritmo probabilista puede producir resultados diferentes o tener tiempos de ejecución variables para la misma entrada, dependiendo de las "elecciones" aleatorias que realice.

¿Por qué utilizar algoritmos probabilistas?
Aunque la aleatoriedad pueda parecer contraintuitiva en el diseño de algoritmos, los algoritmos probabilistas se utilizan por varias razones poderosas:

Simplicidad: A menudo, un algoritmo probabilista es significativamente más simple de diseñar e implementar que su contraparte determinista.

Eficiencia: Para muchos problemas, el mejor algoritmo probabilista conocido es asintóticamente más rápido que el mejor algoritmo determinista conocido. En algunos casos, los algoritmos probabilistas pueden encontrar una solución en tiempo polinomial donde no se conoce un algoritmo determinista de tiempo polinomial.

Rendimiento en el peor caso: Pueden tener un rendimiento en el peor caso mucho mejor que los algoritmos deterministas para ciertas entradas "patológicas". La aleatoriedad ayuda a "suavizar" el rendimiento, evitando las entradas específicas que podrían llevar a un algoritmo determinista a su peor caso.

Para problemas específicos: Algunos problemas tienen soluciones naturales y eficientes solo a través de métodos probabilistas (ej., algunos problemas criptográficos, muestreo, etc.).

Tipos de Algoritmos Probabilistas

Brassard y Bratley suelen categorizar los algoritmos probabilistas según la forma en que la aleatoriedad afecta su corrección o su tiempo de ejecución:

1. Algoritmos de Las Vegas
* Característica principal: Siempre producen la respuesta correcta. La aleatoriedad afecta únicamente el tiempo de ejecución.

* Tiempo de ejecución: El tiempo de ejecución es una variable aleatoria. Generalmente, se analiza el tiempo de ejecución esperado (promedio).

* Aplicaciones: Son ideales cuando la corrección es primordial y se puede tolerar una variabilidad en el tiempo.

Ejemplos:

Quicksort aleatorizado: La elección del pivote se hace aleatoriamente. Esto garantiza que, con alta probabilidad, el tiempo de ejecución promedio sea O(nlogn), evitando el peor caso O(n2) para entradas mal ordenadas que podrían ocurrir con un pivote determinista.

Algoritmo para encontrar el k-ésimo elemento más pequeño (selección aleatorizada): Similar a Quicksort, la aleatoriedad en la elección del pivote ayuda a garantizar un tiempo esperado eficiente.

2. Algoritmos de Monte Carlo
* Característica principal: Siempre terminan en un tiempo determinado (o un tiempo acotado), pero pueden producir una respuesta incorrecta con cierta probabilidad.

* Probabilidad de error: La probabilidad de error se puede controlar y reducir (a menudo exponencialmente) repitiendo el algoritmo varias veces, aunque esto aumenta el tiempo de ejecución.

Tipos de error:

* Sesgo unilateral (One-sided error): El algoritmo es siempre correcto si da una respuesta positiva/sí, pero puede ser incorrecto si da una respuesta negativa/no (o viceversa). Es decir, el error solo ocurre en una dirección.

* Sesgo bilateral (Two-sided error): El algoritmo puede ser incorrecto tanto si da una respuesta positiva como si da una negativa.

Aplicaciones: Útiles para problemas donde una pequeña probabilidad de error es aceptable, especialmente cuando no se conoce un algoritmo determinista eficiente.

Ejemplos:

Test de primalidad de Miller-Rabin: Un algoritmo de Monte Carlo muy conocido para determinar si un número grande es primo. Si el algoritmo dice que un número es compuesto, es 100% correcto. Pero si dice que es primo, hay una pequeña probabilidad de que en realidad sea compuesto (un pseudoprimo fuerte). Al repetir el test varias veces, la probabilidad de error se puede reducir drásticamente.

Algoritmos para el problema SAT (Satisfiability) o 3-SAT: Algunos algoritmos para estos problemas son de Monte Carlo.

Generación de números aleatorios
Un aspecto crucial de los algoritmos probabilistas es la fuente de aleatoriedad. En la práctica, se utilizan generadores de números pseudoaleatorios (PRNGs), que son algoritmos deterministas que producen secuencias de números que se comportan como si fueran aleatorios. Para aplicaciones que requieren verdadera aleatoriedad (ej., criptografía), se emplean generadores de números aleatorios de hardware (TRNGs).

Notación y Análisis

El análisis de algoritmos probabilistas a menudo implica el uso de conceptos de probabilidad, como:

* Esperanza (Valor Esperado): Para el tiempo de ejecución en algoritmos de Las Vegas.

* Probabilidad de error: Para la corrección en algoritmos de Monte Carlo.

* Desigualdades de Markov, Chebyshev, Chernoff: Herramientas para acotar las probabilidades y el comportamiento de las variables aleatorias.

Resumen:

Los algoritmos probabilistas son una herramienta poderosa y elegante en la algoritmia, que ofrecen ventajas en términos de simplicidad y eficiencia para una variedad de problemas. Al introducir la aleatoriedad, pueden sortear las limitaciones de los algoritmos deterministas puros, ya sea garantizando la corrección con un tiempo esperado eficiente (Las Vegas) o proporcionando una respuesta rápida con una probabilidad controlada de error (Monte Carlo). Su estudio es fundamental para comprender las fronteras del diseño de algoritmos eficientes.


# Talleres Segundo Bimestre 

## Algoritmo de PRIM - Grafos

Grafo no Dirigido

![WhatsApp Image 2025-07-21 at 7 39 24 PM](https://github.com/user-attachments/assets/1d41cbe0-e7d9-4fac-bd27-83e5680c2d9e)

Grafo Dirigido

![WhatsApp Image 2025-07-21 at 7 40 24 PM](https://github.com/user-attachments/assets/339b3774-add7-4c5c-b9c6-28e04a17184c)


## Prueba de Escritorio - Merge Sort
<img width="484" height="634" alt="image" src="https://github.com/user-attachments/assets/84cfe4ff-ca5f-498a-b229-c6623b006d8b" />


![WhatsApp Image 2025-07-21 at 7 45 33 PM](https://github.com/user-attachments/assets/77281a1e-50e2-420a-8516-00d41969bc04)

![WhatsApp Image 2025-07-21 at 7 45 33 PM (1)](https://github.com/user-attachments/assets/1c3a7c4b-2efd-4fbb-86f3-f05e808608ce)

![WhatsApp Image 2025-07-21 at 7 45 33 PM (2)](https://github.com/user-attachments/assets/04bd7436-3534-4e85-8f7a-0b332dbbb69d)

## Prueba de Escritorio - Divide y Venceras

![WhatsApp Image 2025-07-21 at 7 52 16 PM](https://github.com/user-attachments/assets/f3c605de-a1c0-4639-85a9-686358fa5fe6)

## Prueba de Escritorio - Algoritmo QuickSort

![WhatsApp Image 2025-07-21 at 7 56 53 PM](https://github.com/user-attachments/assets/cd0c8882-a60e-4470-aeb3-9975c802f8aa)

![WhatsApp Image 2025-07-21 at 7 56 53 PM (1)](https://github.com/user-attachments/assets/ab1cbb9b-81fa-4fb8-97be-1c9cd3f2f9cd)


