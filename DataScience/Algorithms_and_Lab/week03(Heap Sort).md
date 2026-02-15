### Heap Sort

1. **Max-Heapify**: 시작점(i)부터 비교하여 Child가 존재하지 않을 때까지 tree 아래쪽으로 내려감.
- Height: edge 개수 of the longest one (node개수 x)
- Max-heap: Largest element at root ⇒ Ascending Sort (Parent is greater than Children)
- Min-heap: Smalles element at root ⇒ Descending Sort
- $L=2i, \space R =2i+1$

1. **Build-Max-Heap**: $i$ starts from $n/2$ (내림) Index to $1$ Index. (Tree 위쪽으로 올라감)
2. **Heapsort**:
    1. Swap the first and last element (the largest)
    2. len(array) - 1
    3. max_Heapify 제일 앞에서 한 번만 실행.
    

---

### Running Time of Heap Sort

- 𝑶(𝒏) calls to MAX-HEAPIFY, each of which takes 𝑶 𝒍𝒐𝒈 𝒏
- the running time of BUILD-MAX-HEAP is 𝑶(𝒏).
    
    ⇒ **𝑂(𝑛 log 𝑛)**
    

---

```python
def heapify(arr, n, i):
    left_child = 2*i+1
    right_child = 2*i+2

    if left_child < n and arr[left_child] > arr[i]:
        largest = left_child
    else:
        largest = i
    
    if right_child < n and arr[right_child] > arr[largest]:
        largest = right_child
    
    if largest !=i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, n, largest)

def build_max_heap(arr,n):
    for i in range(n//2-1, -1, -1):  # range(start, stop, step)
        heapify(arr, n, i)

def heapsort(arr, n):
    build_max_heap(arr,n)
    for i in range(n-1, 0, -1):
        arr[0], arr[i] = arr[i], arr[0]
        heapify(arr, i, 0)
```
