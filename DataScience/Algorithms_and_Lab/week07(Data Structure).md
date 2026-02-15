- Simple array-based data structures: arrays, matrices, stacks, and queues
- ‘2’ and ‘567’ have the same access time
- index starts from $s$, memory address starts from $a$, each occupies $b$ bytes ⇒ $i$ _{th} element occupies bytes $a+b(i-s)$ through $a+b(i+1-s)-1$

---

### Stacks

- last-in, first-out(LIFO)
- Insert: push / Delete: pop
- top idex: recently inserted element 
⇒ S.top=0: stack에 아무것도 없다는 뜻
⇒ S.top==S.size: stack이 꽉 찼다는 뜻
- ex) UNDO/REDO

### Queues

- first-in, first-out(FIFO)
- wrapping around: circulate the array(인덱스가 끝나면 처음부터 다시 시작)
- Insert: enqueuing / Delete: dequeuing
- head: first inserted (starts from index 1)
- tail: lastly inserted (starts from index 1)

⇒ Q.head = Q.tail: the queue is empty.
⇒ Q.head = Q.tail+1: the queue is full.
⇒ Q.head = 1 & Q.tail = n: the queue is full.

- ex) CPU scheduling, Printer, Traffic management

---

### Linked Lists

- x.key: data
x.prev: address of previous node
x.next: address of next node
- Types of the linked lists
    - Singly linked
    - Sorted
    - Unsorted
    - Circular
- Doubly Linked list

- List-Search: seach the specific number in the list
    

- List-Prepend: insert at the first of the list

- List-Insert: insert anywhere

    x: what to insert, y: left side of x
    
- List-Delete: delete anywhere
    


⇒ Insertion and Deletion are faster on doubly linked list than on arrays.

worst case in array: $\phi(n)$, doubly linked list: $\phi(1)$

⇒ Access by index is faster in an array than on doubly linked list.

in array: $\mathbb{0}(1)$, linked ilst: $\phi(k)$
