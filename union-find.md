
```python
sets = [-1 for _ in range(n)]
def find(x, sets):
        if sets[x] < 0:
            return x
        else:
            sets[x] = find(sets[x], sets)
            return sets[x]

    def union(u, v, sets):
        a = find(u, sets)
        b = find(v, sets)

        newSize = sets[a] + sets[b]

        if sets[a] > sets[b]:
            sets[a] = b
            sets[b] = newSize
        else:
            sets[b] = a
            sets[a] = newSize
```
