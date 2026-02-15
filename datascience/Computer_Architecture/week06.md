<aside>

### Five External Memories

1. Magnetic Disk
2. SSD
3. Magnetic Tape
4. RAID
5. Optical Memory
</aside>

<aside>

### Magnetic Disk

- Materials
    - Aluminium substrate → Glass substrate
    - Benfits of using the glss substrate:
        - store more data
        - reduce read-write errors
        - damage 에 강함

- Magnetic read and wrtie mechanisms
    - First, data are recorded on the magnetic disk.
    - Then, the data are retrieved from tne magnetic disk by the ‘read head’.

- Data organization and formatting
    - Inner sector is smaller than the outer sector, but the inner sector is dense.
        
        ⇒ The amount of the data which can be stored in inner and outer sectors is same.
        
    - As we store more data, need more ECC(Error Correction Code).
    - Disk Layout Methods
        - CAV (Constant Angular Velocity) (In past)
            - dived into ‘sectors’ and ‘tracks’.
            - Capacity of inner and outer sectors are same.
            - Rotates the disk at a fixed speed.
        - MZR (Multiple Zone Recording) (In modern)
            - dived into ‘sectors’, ‘tracks’ and ‘zones’.
            - Capacity of inner and outer sectors are same. (like CAV)
            - Outer zone is composed to more tracks and sectors.
            - Inner rotates slower, outer rotates faster.

- Physical characteristics
    - Head motion
        - Fixed head: Each track has its own head, but the head itself is fixed in place.
        - Movable head:  A single head moves across tracks and sectors to access data.
    - Disk portability
        - Nonremovable disk
        - Removable disk (e.g Floppy disk, ZIP cartridge disk)
    - Sides
        - Single sided disk
        - Double sided disk
    - Platters
        - Single platter
        - Multiple platter
    - Head Mechanism
        
        : Narrower head ⇒ greater data density. 
        
        : Closer head to the disk ⇒ generates more risk of error.
        
        - Contact (Floppy disk): high damage ⇒ used in past
        - Fixed gap: As larger gaps, storage is decreased. but reduces the damages and impurities.
        - Aerodynamic gap (Winchester Heads) : ‘Gap is smaller’ than the conventional rigid disk head, but the ‘storage is larger’.                                (used in sealed drive assemblies that are almost free of contaminants. i.e. not polluted)

- Disk performance parameters
    - `Seek time`: the time it takes to position the head at the track.
    - `Latency time` (Rotational delay): begining of the sector ~ reach the head.
    - `Transfer time` : the time it takes to do read and write operation
    - `Access time` (Bloc access time): seek time + latency time + transfer time
</aside>

<aside>

### RAID

Consists of 7(0~6) levels (Not hierarchy)

- RAID 0: No redundancy, disks required `n`
    - 성능과 용량은 최대한으로 사용하는 대신, 안정성은 극악.
- RAID 1: High redundancy, disks required `2n`
    - 안정성 좋음, 비용 안 좋음.
- RAID 2: High redundancy, disk required `n+log(n)`
    - bit 단위로 striping, error correction을 위해 [H](https://en.wikipedia.org/wiki/Hamming_code)amming code 사용.
- RAID 3: High redundancy, disks required `n+1`
    - Byte 단위로 striping, 용량 및 성능이 단일 디스크 대비 (N-1) 배 증가
- RAID 4: High redundancy, disks required `n+1`
    - Block 단위로 striping, 용량 및 성능이 단일 디스크 대비 (N-1) 배 증가
- RAID 5: High redundancy, disks required `n+1`
    - Block 단위로 striping, 용량 및 성능이 단일 디스크 대비 (N-1) 배 증가,
        
        RAID 0 에서 성능, 용량을 조금 줄이는 대신 안정성을 높인 level
        
- RAID 6: Highest redundancy, disks required `n+2`
    - 용량 및 성능이 단일 디스크 대비 (N-2) 배 증가
</aside>

<aside>

### Solid State Drives (SSD)

- SSD compared to HDD (Hard Disk Drives (e.g. magnetic disk))
    - high-performance IOPS (Input/Output Operations per Second)
    - Durability (내구성)
    - Loger lifespan
    - Lower power consumption
    - Quiter and cooler running capabilities
    - Lower access times and latency rates

- Two practical issues of SSD
    1. As SSD is used, SDD performance is going to be slowed down.
    2. Flash memory becomes unusable after a certain number of writes.
        
        (Flash memory is non-volatile, so we can’t erase or rewrite anything on flash memory)
        
- Types of SSD
    - Internal SSD: PCIe
    - External SSD: USB
</aside>

<aside>

### Optical Memory (CD & DVD)

- CD (Compact Disk)
    - CD easily gets scratches.
    - Compare to Magnetic disk, CD uses the laser and rotates center to the outer side.
- DVD (Digital Versatile Disk)
    - DVD has two layers that can store data (CD has only one layer)
    - DVD’s beam spot is smaller than CD
        
        ⇒ DVD’s storage capacity is higher than CD
        
- Differences between CD and CD-ROM:
    - CD-ROM is more rugged.
    - CD-ROM has error correction devices to ensure that data are properly transferred.

- Optical Disk Products
    - CD(Compact Disk): Non-erasable (sotres digitized audio information)
    - CD-ROM(CD Read-Only Memory): Non-erasable (used for storing computer data)
        - Advantage: can insert it in any different computer
        - Disavantage: Cannot be updated.
    - CD-R(CD Recordable): can write only once
    - CD-RW(CD Rewritable): can erase and rewrite multiple times.
    - DVD(Digital Versatile Disk): stores video information
    - DVD-ROM (DVD Read-Only Memory): Non-erasable
    - DVD-R(DVD Recordable): can write only once.
    - DVD-RW(DVD Rewritable): can erase and rewrite multiple times.
    - Blu-ray DVD: High-definition video disk.

- Comparison of Magnetic Disk and CD
    - Magnetic Disk
        - CAV(Constant Angular Velocity): The speed of rotation of disk is the same on both the inner and outer tracks.
    - CD
        - CLV (Constant Linear Velocity): Disk rotates more slowly on the inner tracks and faster on the outer tracks.

- Structure of CD-ROM
    - SYNC: includes the information where the sector starts or ends.
    - ID: refers to the addresses of data (consists of min, sec, sector, mode)
    - Data
    - L-ECC (Longitudinal(→ 세로) Error Correction Code)
</aside>

<aside>

### Magnetic Tape

- e.g. Cassette Tape
- Typical Magnetic Tape Features
    1. **Serpentine reading and writing**
        
        : Data must be recorded to only one track in one go.
        
    2. **Block layout of system that reads/writes four tracks simultaneously** 
        
        : Data can be recorded to many different tracks in one go.
        
</aside>
