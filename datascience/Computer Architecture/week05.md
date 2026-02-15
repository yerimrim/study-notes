<aside>
💡

### Cache memory principles

- Block
- Frame
- Line
- Tag
- Line size

*Structure: Frame → Block → Line → Tag

</aside>

<aside>
💡

### Elements of Cache Design

- **Cache Addresses**
    - Logical
        - Logical cache is faster than physical cache.
        - Virtual Memory
            
            : without regard to the amout of main memory physically available.           ⇒ when we don’t have enough memory, we can use Virtual Memory.
            
    - Physical

- **Cache Size**
    - Cache memory is very fast. So its size increases, then cost also increases.
    - The larger the cache, the larger the number of gates. so, the cache is going to be slower.
    
- **Cache Access Methods**
    - Direct
        - : maps to one unique line of cache.
        - consists of: Tag & Offset & Line number
        - disadvantage: fixed cache location (need to repeatedly map words in different blocks on the same line → hit ratio will be low.)
    - (Fully) Associative
        - : maps to any line of cache
        - consists of: Tag & Offset
        - disadvantage: the complex circuitry (examine the tags of all cache lines in parallel.)
        - ex) CAM(Content-Addressable Memory)
    - Set-Associative (combined Direct and Associcative)
        - : maps to one unique cache set but any line within that set.
        - consists of: Tag & Offset & Set number
    
    *Tag field: uniquely identifies a block of main memory currently stored in a particular cache line (or set ; In set-associative mapping).
    
    *Offset field: indicates the exact location within the cache block where the desired data can be found.
    
    *Line number field: is used to index into the cache to access a particular line.
    
    *Set number field: is used to index the set that contains a number of lines.
    
- **Replacement Algorithms (main memory to cache)**
    - *Replacement Algorithms are designed to maximize the hit ratio.
    - LRU(Least Recently Used)
        - : replace the block that has been in the cache longest with no reference to it.
        - most effective
    - FIFO(First-In-First-Out)
        - : replace the block that has been in the cache longest.
    - LFU(Least Frequently Used)
        - : replace the block that has experienced the fewest references.
    - Random
        - : replace randomly

- **Write policy**
    - Write through
        - : All write operations are made to main memory as well as to the cache.
        - Advantage: 모든 쓰기 작업을 메인 메모리와 캐시에 동시에 수행하여 간단
        - Disadvantage: substantial memory traffic and bottleneck.
    - Write back
        - : Updates are made only in the cache.
        - Advantage: Minimizes memory writes.
        - Disavantage: complex circuitry(메인 메모리와의 일관성을 유지하기 위해) and a potential bottleneck.
- **Write Miss Alternatives**
    - Write allocate: Fetches from main memory into the cache. ⇒ Write through
    - No write allocate: Not loaded into the cache. ⇒ Write back

- **Cache Coherency**
    - There are three approaches to maintaining cache coherency.
        1. Bus watching with write through
            
            : each cache controller monitors the address lines.
            
        2. Hardware transparency
            
            : Additional hardware is used. All updates to main memory.
            
        3. Noncacheable memory (no using cache memory)
            
            : Not use cache. Directly performs read and write operations in SRAM.
            

- **LIne size**
    - As the block size increases, the hit ratio increases.
    - Block size is too much big or small, the hit ratio begins to decrease.
    
- **Number of caches**
    - Multilevel Caches (Single-level & Two-level)
        - Single-level cache
        - Two-level cache : consists of L1(internal) and L2(external).
    - Unified cache and Split cache
        - Unified cache
            - : There is only one L1 cache, which dedicated to both ‘instructions’ and ‘data’.
            - Advantage: Higher hit rate
        - Split cache
            - : There are two L1 cache. one dedicated to ‘instructions’ and the other dedicated to ‘data’.
            - Eliminates cache contention (분쟁).

- **Inclusion policy**
    - Inclusive policy
        - : Data in one cache is also found in all lower levels of caches.
        - Advantage: simplifies searching for data. useful in enforcing cache coherence.
    - Exclusive policy
        - : Data in one cache is not found in all lower levels of caches.
        - Advantage: not waste cache capacity.
        - Disadvantage: need to search multiple cache levels.
    - Noninclusive policy
        - : Data in one cache may or may not be found in lower levels of caches. (Similar as the exclusive policy)

* SRAM(Static RAM) is faster than DRAM(Dynamic RAM)

</aside>

<aside>
💡

### Cache performance

- **Cache Timing Model**
    - `tct`,   `trl`,   `txb`,   `thit`,  `this`

- **Design option for improving performance**
    - To improve performance, we must consider of specific application requirements, access patterns, and performance goals.
</aside>
