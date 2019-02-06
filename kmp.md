# kmp
```python
def kmp(text, pattern):
    i, j = 0, 0
    m = len(text)
    n = len(pattern)
    if m < n: return -1
    if n==0: return 0
    if m==0: return -1
    def createPMT(pattern):
        i = 0
        j = 1
        pmt = [0]*n
        while j<n:
            if pattern[i] == pattern[j]:
                pmt[j] = i+1
                i += 1
                j += 1
            elif i > 0:
                i = pmt[i-1]
            else:
                pmt[j] = 0
                j += 1
        return pmt
    pmt = createPMT(pattern)
    while i < m:
        if text[i] == pattern[j]:
            if j == n-1:
                return i-j
            i += 1
            j += 1
        elif j > 0:
            j = pmt[j-1]
        else:
            i += 1
    return -1
    
```
