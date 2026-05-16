
Practical2_A*Algo

Code:

# Simple A* Algorithm Implementation

graph = {
    'A': {'B': 1, 'C': 3},
    'B': {'D': 3, 'E': 1},
    'C': {'F': 5, 'G': 2},
    'D': {},
    'E': {'G': 1},
    'F': {},
    'G': {}
}

heuristic = {
    'A': 5,
    'B': 3,
    'C': 2,
    'D': 6,
    'E': 1,
    'F': 4,
    'G': 0
}

def astar(start, goal):

    open_list = [start]

    closed_list = []

    g = {start: 0}

    parent = {start: start}

    while open_list:

        current = open_list[0]

        for node in open_list:
            if g[node] + heuristic[node] < g[current] + heuristic[current]:
                current = node

        if current == goal:

            path = []

            while current != start:
                path.append(current)
                current = parent[current]

            path.append(start)
            path.reverse()

            print("Shortest Path:")
            print(path)

            return

        open_list.remove(current)

        closed_list.append(current)

        for neighbour in graph[current]:

            if neighbour in closed_list:
                continue

            cost = g[current] + graph[current][neighbour]

            if neighbour not in open_list:
                open_list.append(neighbour)
                parent[neighbour] = current
                g[neighbour] = cost

            elif cost < g[neighbour]:
                g[neighbour] = cost
                parent[neighbour] = current

astar('A', 'G')
