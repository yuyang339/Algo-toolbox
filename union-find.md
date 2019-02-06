
```python
def find(x):
    #while x!=p[x]: x = p[x]
    # path compression
    while (x != p[x]):
        p[x] = p[p[x]]
        x = p[x]
    return x
def union(x, y):
    px = find(x)
    py = find(y)
    if px != py:
        p[px] = py
        return False
    else:
        return True
```
