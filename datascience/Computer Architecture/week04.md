<aside>
💡

### Principle of locality

**1. Temporal locality (최근에 사용된 데이터가 곧 다시 사용될 가능성이 높다는 원칙)**

: Recent past

after reading a book, “It is important and I’ll use this book again.” so store on the desk, not return back. 

(What I experienced)

**2. Spatial locality (현재 접근한 데이터 근처에 있는 데이터도 곧 사용될 가능성이 있다는 원칙)**

: Near one another

“maybe I’ll need this book in the future”, so bring that book.
what I usually use is stored in ‘cache memory’, not in ‘main memory’. 

(What I didn’t experienced and just expecting)

</aside>

<aside>
💡

### Instruction

**1. Static Instruction** 

: exists in the code to be executed.

**2. Dynamic Instruction**

: appear in the execution trace of a program.

- 프로그램 개발시: Static Instruction
- 프로그램 실행시: Dynamic Instruction

**Code Reuse** is efficient when a small number of static instructions are reponsible for a large number of dynamic instructions.

</aside>

<aside>
💡

### Characteristics of memory systems

**[Key characteristics of computer memory systems]**

**1. Location**

- Internal (e.g. Processor registers, Cache, Main memory)
- External (e.g. Optical disks, Magnetic disks, Tapes)

**2. Capacity** (Stroage ; how much it can store, like GB, TB, and so on.)

- Number of words
- Number of bytes

**3. Unit of transfer** 

- Word
- Block

**4. Access Method**

- Sequential access (순차적인 액세스)
    - : 기록 단위로 메모리 접근
    - linear sequence
    - Access time - variable
- Direct access
    - : specific memory location address
    - Access time - variable
- Random access
    - : randomly select a location and the location directly addressed and accessed. (’Main memory’, some ‘cache systems’ use this access method)
    - Access time - constant
- Associative access : Instead of using address, take a portion of the words.
    - : using a portion of its contents (not using address, but each location has its own addressing mechanism.) (’cache memories’ use this access)
    - Retrieval time - constant

**5. Performance**

- Access time
    - : For random-access memory, It is the time to perform read or write operation.
    - : For non-random-access memory, It is the time to position the read-write mechanism at the desired loaction.
- Cycle time
    - : Current access starting time ~ Next access starting time
    - concerned with the ‘system bus’, not the processor.
- Transfer rate
    - The rate of transferring data into or out of a memory unit.
    - For random-access memory, (Transfer rate) = 1/(cycle time)

**6. Physical Type**

- Semiconductor (반도체)
    - Volatile or Nonvolatile
- Magnetic
    - Nonvolatile
- Optical (음향 신호 전송 단자)
- Magneto-optical

**7. Physical characteristics**

- Volatile (RAM)
    - : 휘발성(전원이 끊어지면 정보도 잃어버리는 것)
    - : information decays or is lost when electrical power is switched off.
- Nonvolatile (Second memory)
    - : Once recorded, information remains.
    - don’t need electrical power.
- Erasable
    - : Can be altered.
- Nonerasable (ROM: Read-Only Memory)
    - : Cannot be altered, except by destroying the storage unit.

**8.  Oragnization**

- Memory modules

*External memories have both erassible and non erasable types.

*Volatile, Nonvolatile depends on electric power.

*A processor has its own ‘local memory’, `Registers`.

</aside>

<aside>
💡

### The memroy hierarchy

- **Cost and performance characteristics**

*Price : Performance(Speed) > Capacity

*Registers > Cache memories(L1 > L2 > L3 >…) > Main memory > Second memory

As it goes to the Left side, 

- Cost is more expensive

- Capacity is smaller

- Access time will decrease

- Performance is higher

- The frequency of the access of memory by processor will increase.

As capacity of cache memory is increasing, the performance of the cache memory will be decreased. Then, the cost will be decreased.

- **The IBM z13 memory hierarchy**
    - L1 and L2 caches use SRAM and are private for each other.
    - L3 cache uses eDRAM and is shared by all eight cores within the PU chip.
    ****
- **Design principles for a memory hierarchy**
    - Locality (how fast we can find the data)
        - : makes effective use of memory hierarchy.
        - As locality is higher, hit ratio is higher.
    - Inclusion (하위 메모리에 저장된 데이터가 상위 메모리에도 저장되어 있음)
        - 더 작은 L1 캐시에 있는 데이터는 더 큰 L2 캐시에도 포함되어 있음.
    - Coherence (복사본들이 항상 일관된 값을 유지)
        - When a data is modified, copies must be updated immediately.
        - Vertical coherence (수직 일관성, L1, L2, L3 간의 일관성 유지)
        - Horizontal coherence (수평 일관성, L1 내의 데이터들의 일관성 유지)

</aside>

<aside>
💡

### Performance modeling of a multilevel memory hierarchy

**<Two-level memory access>**

: with `Cache` and `Main memory`

- M1: capacity and size are smaller, faster, more expensive (Cache memory)
- M2: capacity and size are larger, slower, cheaper (Main memory)
- M1 is used as temporary store for part of the contents of M2.
- Access time: Cache 1 < Cache 2 < Cache3 < Cache4 < … < Main memory
- Capacity: Cache1 < Cache2 < Cache3 < Cache4 < … < Main memory

- (Figure 4.8) Two-level memory access에는 M1만 access 하는 경우, M1, M2 모두 사용하는 경우로 나뉨.
⇒ M1만 사용하는 경우가 증가할수록, average total access time이 access time of M1에 가까움.
- locality can be exploited in two-level memory access
    - **locality** 덕분에 M1으로 가져온 데이터가 여러 번 사용될 수 있고, 이를 통해 **빠른 전반적인 접근**이 가능해짐. ⇒ 따라서, **locality**가 two-level memory access에서는 성능을 **향상시키는 요인**으로 작용함.
- (Figure 4.11)
    
    hit ratio를 높이고 싶음.
    ⇒ 그럼 그냥 캐시메모리(M1)의 크기를 메인메모리(M2)의 크기에 최대한 가깝게 늘리면 되는거 아냐?
    ⇒ 그럼 당연히 hit ratio는 늘어나겠지만, 비트당 평균가격이 상승한다.
    ⇒ 정리하면 hit ratio 높이겠다고 무작정 캐시메모리 크기를 늘리는 건 경제적이지 않다.
    => 따라서, 메모리에 optimal한 솔루션은 없다. 캐시메모리를 메인메모리 크기에 맞춰서 점점 늘리면 비트당 평균가격이 상승하므로 적절한 균형을 이루어야 한다.
    

___________________________________________________

정리!!!!

- hit ratio: r = T2/T1 (T1: the time to access M1, T2: the time to access M2)
    
    T2 = 1, T1 =1 → r = 1 (Access time of M1 and M2 is same)
    
    (low hit ratio → access time decreases → high access efficiency)
    
    T2 = 100, T1 = 1 → r = 100 (high hit ratio → access time increases → low access efficiency)
    
    ~~T1 = 100, T2 =1 → r = 0.01 (Always T1 < T2, so there not exists this case)~~
    
- If T2 and T1 are almost same, then hit ratio is low, and then the access efficiency is high.
- The gap of access time between T1 and T2 is increasing, then hit ratio is high, and then the access efficiency is low.
- Hit ratio is high → access time increases → low access efficiency → low computer performance
- **Operation of Two-Level Memory access**
    - First, access to Cache1. If we can’t find the data in Cache1 , access to Cache2 , to Cache3, …, to Main memory.
    - When we found the data in Main memory, copy it from Main memory to Cache4 to Cache3 to Cache2 to Cache1.

hit ratio is too small, the size of the cache memory is small

hit ratio is too big, the access time is too long

**<Multilevel memory access>**
: with `Cache`, `Main memory`, `Second memory`

</aside>
