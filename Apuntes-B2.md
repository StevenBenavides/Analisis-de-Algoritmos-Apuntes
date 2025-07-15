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
