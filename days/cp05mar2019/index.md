# Обход графа

###### (с) МЭИ, АВТИ, ПМ, 5 марта 2019 года


## Графы
$G = (V,E)$

* $V$ - множество вершин
* $E$ - множество рёбер/дуг


## Представления графов
* Список смежности
* Матрица смежности


## Список смежности

Коллекция списков вершин. 
Каждой вершине графа соответствует список, состоящий из "соседей" этой вершины.

|   |          |     |
|---|----------|-----|
| a | смежно к | b,c |
| b | смежно к | a,c |
| c | смежно к | a,b |


## Матрица смежности

Квадратная матрица $A$ размера $n$, 
в которой значение элемента $a_{ij}$ 
равно числу рёбер из $i$-й вершины графа в $j$-ю вершину.

|   | a | b | c |
|---|---|---|---|
| a | 0 | 1 | 1 |
| b | 1 | 0 | 1 |
| c | 1 | 1 | 0 |


## Виды обходов графа

* DFS - Обход в глубину
* BFS - Обход в ширину

## Обход в глубину

Общая идея алгоритма состоит в следующем: 

Для каждой не пройденной вершины необходимо найти все не пройденные смежные вершины и повторить поиск для них.

## DFS Визуализация

<iframe width="100%" height="480" src="https://www.youtube.com/embed/NUgMa5coCoE?autoplay=1" allow="accelerometer; autoplay; picture-in-picture" allowfullscreen></iframe>


## DFS Код

![](https://cdncontribute.geeksforgeeks.org/wp-content/uploads/cycle.png)

```python
garage = [[1,2],[2],[0,3][3]]
visited = [False] * 4

def dfs(node):
    visited[node] = True
    for next_node in garage[node]:
        if not visited[next_node]:
            print(next_node)
            dfs(next_node)
            
dfs(2)
```


## Обход в ширину

Общая идея алгоритма состоит в следующем: 

Для каждой вершины в очереди необходимо найти все не пройденные смежные вершины и добавить их в очередь.


## BFS Визуализация

<iframe  width="100%" height="480" src="https://www.youtube.com/embed/cfhP-6jDEd0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## BFS Код

![](https://cdncontribute.geeksforgeeks.org/wp-content/uploads/bfs-5.png)

```python
garage = [[1,2],[2],[0,3][3]]
visited = [False] * 4

def bfs(s):
    queue = [s]
    while queue:
        v = queue.pop(0)
        print(v)
        for w in garage[v]: 
            if not visited[w]: 
                visited[w] = True
                queue.append(w)
                
bfs(2)
```