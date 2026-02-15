### **Insertion Sort**

- **Inplace** 사용 (메모리 효율 ⬆️)
- Slower, Good at small amount of data (Compare to “Merge Sort”)
- 현재 원소를 앞쪽에 올바른 위치에 삽입하며 정렬
- 데이터가 거의 정렬된 경우 매우 빠름, 일반적으로 느림
- Initialization: It is true prior to the first iteration of the loop.
- Maintenance: If it is true before an iteration of the loop, it remains true before the next iteration.
- Termination: The loop terminates, and when it does, the gives us a useful property that helps show that the algorithm is correct.
- How to Minimize the runtime
    - Drop lower-order terms
    - Ignore constant coefficient

### Running Time

- Running Time: $\sum \space(cost \space of \space statement)\space \cdot \space (number \space of \space times \space statement \space is \space executed)$
- pseudocode: starts index from 1

```python
# Insertion Sort
def insertion_sort(arr):
    comparisions = 0
    swaps = 0

    for i in range(1, len(arr)):
        key = arr[i]
        j=i-1

        while j>=0 and arr[j]>key:
            arr[j+1]=arr[j]
            j-=1
            comparisons+=1
            swaps+=1
        arr[j+1]=key
```

---

### Merge Sort

- Merge sort is a sorting algorithm based on divide and conquer.
    - **Divide** the problem into a number of subproblems that are smaller instances of the same
    problem.
    - **Conquer** the subproblems by solving them recursively.
    - **Combine** the subproblem solutions to give a solution to the original problem.
- **Multiple Array** 사용 (메모리 효율 ⬇️)
- Faster (Compare to “Insertion Sort”)
- 배열을 반으로 쪼개서 각각 정렬 후 병합
- 안정 정렬, 항상 빠른 성능, 분할 정복 기반
1. Divide A[p:r] into A[p:q], A[q+1:r], q is the half of the A, q = (p+r)/2
    - Floor or Ceil
2. Sort each array
3. Combine the two sorted arrays

### Running Time

- Total: $c_2n\space logn+c_1n$ ⇒ $n\space logn$ (Ignore the low-order and constant coefficient)
- $2^kT({n\over 2^k})$     ($k$ is the times of dividing)

```python
def merge_sort(arr):
    
    if len(arr)<=1: 
        return arr

    mid = len(arr)//2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])

    return merge(left, right)

def merge(left, right):
    result = []
    i=j=0
    while i<len(left) and j<len(right):
        if left[i] < right[j]:
            result.append(left[i]) 
            i+=1
        else:
            result.append(right[j])
            j+=1

    while i<len(left):
        result.append(left[i]) 
        i+=1

    while j<len(right):
        result.append(right[j])
        j+=1
    
    return result
```
