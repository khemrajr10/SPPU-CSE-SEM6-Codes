
Practical1_BFS_DFS

Implement depth first search algorithm and Breadth First Search algorithm, Use an undirected 
graph and develop a recursive algorithm for searching all the vertices of a graph or tree data 
structure.

Code:

# Implementation of DFS and BFS using Undirected Graph

# Create Undirected Graph using adjacency list
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}

# ---------------- DFS ----------------

# Set to store visited nodes for DFS
visited_dfs = set()

# Recursive DFS Function
def dfs(node):

    # Mark node as visited
    visited_dfs.add(node)

    # Print current node
    print(node, end=" ")

    # Visit all neighbours
    for neighbour in graph[node]:

        # Check if neighbour is not visited
        if neighbour not in visited_dfs:

            # Recursive call
            dfs(neighbour)

# ---------------- BFS ----------------

# BFS Function
def bfs(start):

    # List to store visited nodes
    visited_bfs = []

    # Queue for BFS traversal
    queue = []

    # Add starting node
    visited_bfs.append(start)
    queue.append(start)

    # Run until queue becomes empty
    while queue:

        # Remove first element from queue
        node = queue.pop(0)

        # Print current node
        print(node, end=" ")

        # Visit all neighbours
        for neighbour in graph[node]:

            # Check if neighbour is not visited
            if neighbour not in visited_bfs:

                # Mark as visited
                visited_bfs.append(neighbour)

                # Add to queue
                queue.append(neighbour)

# ---------------- Driver Code ----------------

print("Depth First Search (DFS):")
dfs('A')

print("\n")

print("Breadth First Search (BFS):")
bfs('A')

