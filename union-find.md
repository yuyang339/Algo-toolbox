
```python
p = [i for i in range(n)]
rank = [1 for i in range(n)]
def find(x):
    while x!=p[x]:
        p[x] = p[p[x]]
        x = p[x]
    return x
def union(x, y):
    px = find(x)
    py = find(y)
    if px != py:
        if rank[px] > rank[py]:
            p[py] = px
        elif rank[px] < rank[py]:
            p[px] = py
        else:
            p[px] = py
            rank[py] += 1
```
