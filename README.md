# practica2: Búsqueda heurística sin adversarios

# ¿Qué variable representa la lista abrierta?
La lista abierta se representa como la variable openSet. Esta lista es utilizada para almacenar los nodos que son candidatos para su evaluación durante la ejecución del algoritmo. Inicialmente, la lista abierta contiene el nodo de inicio. Se utiliza para realizar un seguimiento de los nodos que aún no han sido evaluados y que son candidatos para la expansión en el siguiente paso del algoritmo. La elección del próximo nodo a evaluar se basa en la estimación de la función de costo total desde el inicio hasta el objetivo a través de ese nodo, y esta se utiliza para ordenar la lista openSet en cada iteración del bucle principal del algoritmo.

# ¿Qué variable representa la función g?
La función gg se representa mediante la variable gScore, donde mantiene el costo que se acumula desde el nodo de inicio hasta cada nodo en la lista openSet. gScore es un mapa donde las claves son nodos del grafo y los valores son cosotos acumulados desde el nodo de inicio hasta esos nodos específicos. Se utiliza para evaluar la calidad de los caminos parciales y actualizar la mejor estimación de los costos acumulados a lo largo de esos caminos.

# ¿Qué variable representa la función f ?
La función ff se representa mediante la variable fScore. Se refiere a la suma del costo acumulado desde el inicio hasta el nodo actual (gg) y una heurística que estima el costo restante hasta el objetivo.
fScore es un mapa donde las claves son nodos del grafo y los valores son estimaciones de la función ff para esos nodos específicos. La estimación se calcula sumando el costo acumulado desde el inicio hasta el nodo actual (gg) y una heurística que estima el costo restante hasta el objetivo. La función heuristicCostEstimate proporciona la estimación heurística predeterminada la cual, se puede ajustarse según las necesidades específicas del problema.

# ¿Qué método habría que modificar para que la heurística representarala distancia aérea entre vértice
Para modificar el código y utilizar la distancia aérea como heurística, se puedes ajustar el método heuristicCostEstimate para calcular la distancia entre dos vértices en lugar de simplemente devolver 11 (en este caso).
Versión modificada:
```
protected double heuristicCostEstimate(Graph.Vertex<T> start, Graph.Vertex<T> goal) {
    double startX = start.getX(); 
    double startY = start.getY();
    double goalX = goal.getX(); 
    double goalY = goal.getY();  

    double distance = Math.sqrt(Math.pow(goalX - startX, 2) + Math.pow(goalY - startY, 2));

    return distance;
}
``` 

# ¿Realiza este método reevaluación de nudos cuando se encuentra unanueva ruta a un determinado vértice? Justifique la respuesta.
Sí, el método aStar realiza la reevaluación de nodos cuando se encuentra una nueva ruta a un determinado vértice y esta reevaluación ocurre cuando se encuentra un camino más corto desde el nodo de inicio hasta un nodo específico durante la ejecución del algoritmo A*. En el bucle principal se compara el costo acumulado actual con el nuevo costo acumulado calculado a lo largo de la ruta actualizada. Si el nuevo costo acumulado es menor que el valor almacenado actualmente en gScore para el nodo vecino, se actualiza la información relacionada con ese nodo. El algoritmo A* siempre está buscando el camino más corto y puede ajustarse a medida que encuentra rutas más eficientes durante la ejecución.
