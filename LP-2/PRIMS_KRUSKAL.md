
Practical3_Prims&Kruskals

Code:

# Edge Representation of Graph
edges = [
    ('A', 'B', 2),
    ('A', 'C', 6),
    ('A', 'D', 3),
    ('B', 'D', 5),
    ('C', 'D', 4)
]

# List of vertices
vertices = ['A', 'B', 'C', 'D']

# ---------------- Prim's Algorithm ----------------

print("Prim's Minimum Spanning Tree:\n")

selected = ['A']
mst_cost = 0

while len(selected) < len(vertices):

    minimum = 999

    for edge in edges:

        u, v, weight = edge

        # Select edge with one selected vertex
        if (u in selected and v not in selected) or (v in selected and u not in selected):

            if weight < minimum:

                minimum = weight
                selected_edge = edge

    u, v, weight = selected_edge

    print(u, "-", v, ":", weight)

    mst_cost += weight

    # Add new vertex
    if u not in selected:
        selected.append(u)

    if v not in selected:
        selected.append(v)

print("Total Cost =", mst_cost)

# ---------------- Kruskal's Algorithm ----------------

print("\nKruskal's Minimum Spanning Tree:\n")

# Sort edges according to weight
edges.sort(key=lambda x: x[2])

parent = {}

# Initialize parent
for vertex in vertices:
    parent[vertex] = vertex

# Find function
def find(vertex):

    if parent[vertex] == vertex:
        return vertex

    return find(parent[vertex])

# Union function
def union(v1, v2):

    root1 = find(v1)
    root2 = find(v2)

    parent[root2] = root1

mst_cost = 0

for edge in edges:

    u, v, weight = edge

    # Avoid cycle
    if find(u) != find(v):

        union(u, v)

        print(u, "-", v, ":", weight)

        mst_cost += weight

print("Total Cost =", mst_cost)

