
```python
p = [i for i in range(n+1)]
def find(x):
    nonlocal p
    while x!=p[x]:
        p[x] = p[p[x]]
        x = p[x]
    return x
def union(x, y):
    nonlocal p
    nonlocal n
    px = find(x)
    py = find(y)
    if px != py:
        p[px] = py
```
