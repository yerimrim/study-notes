### Quick Sort

- If the subarrays are **balanced**, then quicksort can run **as fast as merge sort**.
- If they are **unbalanced**, then quicksort can run **as slowly as insertion sort**.

### Randomized Version of Quick Sort

- Randomly selecting the pivot element will, on average, cause the split of the input array to be reasonably well balanced.

---

```python
def partition(arr, p, r):
    x=arr[r]
    i=p-1
    for j in range(p,r):
        if arr[j]<=x:
            i +=1
            arr[i], arr[j] = arr[j], arr[i]
    arr[i+1], arr[r] = arr[r], arr[i+1]
    return i+1

def quick_sort(arr, p, r):
    if p < r:
        q = partition(arr, p, r)
        quick_sort(arr, p, q-1)
        quick_sort(arr, q+1, r)

arr = [5,2,7,6,0,8,3,4,9,1]
quick_sort(arr, 0, len(arr)-1)
print("Sorted Array:", arr)
```
