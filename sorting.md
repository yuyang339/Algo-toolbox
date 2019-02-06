```python
# bubble sort
def bubble(inp):
    for i in range(len(inp)-1):
        for j in range(i, len(inp)-1):
            if inp[i] > inp[i+1]:
                inp[i], inp[i+1] = inp[i+1], inp[i]
            
        
    return inp
    
inp = [1, 0, 4, 2, 4, 5, 8]
print(bubble(inp))

# insertion sort
def insertion(inp):
    for i in range(1, len(inp)):
        key = inp[i]
        k = i-1
        v=0
        for j in range(k, -1, -1):
            if inp[j] > key:
                inp[j+1] = inp[j]
            else:
                v = j+1
                break
                
        inp[v] = key
    return inp
inp = [1, 0, 4, 2, 4, 5, 8]
print(insertion(inp)) 

# shell sort
def shell(inp):
    gap = len(inp)//2
    while gap > 0:
        for start_pos in range(0, gap):
            insertion_sort(start_pos, gap)
        gap = gap//2
    return inp

def insertion_sort(start_pos, gap):
    for i in range(start_pos+gap, len(inp)):
        j = i-gap
        key = inp[i]
        while j >=0 and inp[j] > key:
            inp[j+gap] = inp[j]
            j -= gap
        inp[j+gap] = key
    
inp = [1, 0, 4, 2, 4, 5, 8]        
print(shell(inp))


def merge_sort(A):
    results = []
    if len(A) < 2:
        return A
    y = merge_sort(A[len(A)//2:])
    z = merge_sort(A[:len(A)//2])
    i = 0
    j = 0
    while i < len(y) and j < len(z):
        if y[i] < z[j]:
            results.append(y[i])
            i += 1
        else:
            results.append(z[j])
            j += 1
    results += y[i:]
    results += z[j:]
    return results

A = [1, 0, 4, 2, 4, 5]
A=merge_sort(A)
print(A)


# heap sort
def heap_sort():
    build_max_heap()
    A[0], A[len(A)-1] = A[len(A)-1], A[0]
    for i in range(len(A)-2, 0, -1):
        max_heapify(i+1, 0)
        A[0], A[i] = A[i], A[0]

def max_heapify(heap_size, i):
    left = 2*i+1
    right = 2*i+2
    largest = i
    if left < heap_size and A[left] > A[i]:
        largest = left

    if right < heap_size and A[right] > A[largest]:
        largest = right
    
    if largest != i:
        A[largest], A[i] = A[i], A[largest]
        max_heapify(heap_size, largest)

def build_max_heap():
    for i in range(len(A)//2-1, -1, -1):
        max_heapify(len(A), i)

A = [1, 0, 4, 2, 4, 5, 8]
heap_sort()
print(A)

# quick sort
def qs(l, h):
    if l < h:
        m = part(l, h)
        qs(l, m-1)
        qs(m+1, h)
def part(l, h):
    pivot = inp[h]
    smallidx = 0
    for loopidx in range(h):
        if inp[loopidx] < pivot:
            inp[smallidx], inp[loopidx] = inp[loopidx], inp[smallidx]
            smallidx += 1
    inp[smallidx], inp[h] = inp[h], inp[smallidx]
    return smallidx
qs(0, 6)
print(inp)

```
