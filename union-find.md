
```python
parent = [i for i in range(N+1)]

def find(node):
    if parent[node] == node:
        return node
    # path compression
    # rememeber to pass parent[node] to find
    parent[node] = find(parent[node])
    return parent[node]

def union(node1, node2):
    root1 = find(node1)
    root2 = find(node2)
    if root1 == root2:
        return False
    parent[root1] = root2
    return True
```
