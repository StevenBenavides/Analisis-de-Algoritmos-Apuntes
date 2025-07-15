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


