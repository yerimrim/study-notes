<aside>
💡

> Computer components
> 

*At a top level, a computer consists of CPU, memory, and I/O components.

- Differences between programming in hardware and software
    - Programming in hardware: 논리 회로와 같은 물리적 구성 요소를 구성하여 특정 작업을 수행하도록 만드는 과정
    - Programming in software: 소프트웨어 프로그래밍은 범용 컴퓨터 또는 임베디드 시스템에서 실행되는 프로그램을 작성하는 것 ; coding that runs on a general-purpose computer or embedded system (like Python, C, C++)

- The fundametal computer elements: `Gates` and `Memory cells`
- `Registers` is the memory in CPU.

- In CPU, there are 4 Registers.
    - MAR (Memory Address Register)
        
        : 현재 CPU가 접근하려고 하는 ‘메모리의 주소를 저장’하는 레지스터
        
    - MBR (Memory Buffer Register)
        
        : MAR이 지정한 메모리 주소에서 읽어온 데이터나 CPU가 메모리에 쓰고자 하는 ‘데이터를 저장’하는 레지스터
        
    - I/OAR (I/O Address Register)
        
        : I/O 장치의 주소를 저장하는 레지스터
        
    - I/OBR (I/O Buffer Register)
        
        : I/O 장치와 CPU 간의 데이터를 임시로 저장하는 레지스터
        
        **CPU Components**
        
        ![Screenshot 2024-10-02 at 10.40.28 PM.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a3770338-9706-4edc-a979-958163ea1fa2/e527c742-4d38-47f5-9b7e-f0f18416ed1f/Screenshot_2024-10-02_at_10.40.28_PM.png)
        
</aside>

<aside>
💡

> Computer function
> 
- General categories of functions are specified by computer instructions
    
    : `Processor-Memory`, `Processor-I/O`, `Data processing`, and `Control` 
    

- Basic Instruction Cycle consists of `Fetch Cycle` and `Execute Cycle`
    - Fetch Cycle
        - : CPU fetches an instruction from memory
        - PC (Program Counter):  패치될 지시의 주소를 가지고 있음
        - The fetch instruction is loaded into IR(Insrtuction Register)
    - Execute Cycle

- ICSD (Instruction Cycle State Diagram) : has `Fetch Cycle` & `Execute Cycle`
    
    (the possible states that define an instruction execution)
    
    1. Instruction address calculation
    2. Instruction fetch
    3. Instruction operation decoding
    4. Operand address calculation
    5. Operand fetch
    6. Data operation
    7. Operand address calculation
    8. Operand store

- Interrupts
    - : A signal sent from a device or from software to the operating system. (장치나 소프트웨어에서 운영 체제에 전송되는 신호로, 운영 체제 또는 프로세서가 현재 작업을 일시 중단하고 인터럽트를 처리하도록 함.)
    - Switching of the tasks is due to the Interrupts. (인터럽트를 사용하면 프로세서가 I/O 작업이 진행되는 동안 다른 명령을 실행할 수 있음. ; 처리 효율성을 개선하는 데 도움을 줌.)
- ICI (Instruction Cycle with Interrupts) : has `Fetch Cycle` & `Execute Cycle` & `Interrupt Cycle`
- Two approaches to dealing with multiple interruptions: `Sequential Interrupt processing` `Nested interrupt processing`,.
→ Nested interrupt processing is better than the Sequential interrupt processing.
- Classes of interrupts:
    - Program interrupts
    - Timer interrupts
    - I/O interrupts
    - Hardware failure interrupts

- Time:  Short-term I/O + Interrupts ⇒ the most effective processor
- Time: Using no Interrupt > Using Interrupt & Long term of I/O > Using Interrupt & Short term of I/O → When we use Interrupts and short term I/O,
we can use the processor the most meaningfully

*I/O Function: can exchange data directly with the processor

</aside>

<aside>
💡

> Interconnection structures
> 
- Interconnection structures:
    - Memory → Processor : Processor reads an instruction or data from memory.
    - Processor → Memory: Processor writes data to memory
    - I/O → Processor: Processor reads data from I/O
    - Processor → I/O: Processor sends data to I/O
    - I/O → Memory, Memory → I/O:: exchanges data
</aside>

<aside>
💡

> Bus interconnection
> 
- Data Bus
    
    : 데이터 전송을 담당
    
- Address Bus
    
    : 메모리 또는 I/O 장치의 주소 지정
    
- Control Bus
    
    : 데이터 전송의 조정 및 관리
    
- Control lines
    
    : 특정 제어 신호를 전달
    
    Control lines include Memory write, Memory read, I/O write, I/O read, Transfer ACK(Acknowledge), Bus request, Bus grant, Interrupt request, Interrupt ACK(Acknowledge), Clock, and Reset.
    
- As Data lines are wider, can carry more data, signal, address

*Omnibus system: all components use the same bus

</aside>

<aside>
💡

> Point-to-Point Interconnection
> 

: 각 장치가 하나의 공유 버스를 사용하는 대신, **직접적인 연결**을 통해 데이터를 주고받는 구조

- 공유버스방식은 연결 장치가 많아질수록 성능이 저하되었지만, Point-to-Point 방식은 그렇지 않다.

- 특징: 전용 경로, 더 높은 데이터 속도, 낮은 지연 시간, 확장성

</aside>

<aside>
💡

> QPI (Quick Path Interconnection)
> 
- 한 번에 많은 데이터 전송 가능
- 컴퓨터 성능 향상에 도움
- 코어 간 직접 연결로 데이터 전송
- Bus system이 아닌 구성 요소 간의 상호 연결
- Features: Multiple direct connetions, Layered protocol architecture, Packetized data transfer
- QPI has a four-layer protocol architecture.
    1. **Physical layer**
        
        : 신호를 실제로 전달하는 물리적 경로와 관련된 계층
        
    2. **Link layer**
        
        : 흐름 제어와 오류 제어를 담당
        
        Link layer performs two key functions
        
        - Flow control function: ensure that a sending QPI entity doesn’t overwhelm a receiving QPI entity.
        - Error control function: detects and recovers.
    3. **Routing layer**
        
        : 패킷이 전송될 경로를 결정
        
    4. **Protocol layer**
        
        : 패킷 전송에 필요한 규칙과 절차를 관리 (캐시 일관성 유지)
        
    
    ~~피린룻프~~
    
</aside>

<aside>
💡

> PCI (Peripheral Component Interconnection)
> 
- 컴퓨터 메인보드에 주변 장치를 장착하는 데 쓰이는 컴퓨터 버스의 일종.
- PCI는 여러 장치가 하나의 버스를 공유하는 방식으로, 성능과 확장성에 한계가 있음.
- PCIe (PCI express): PCI에 Point-to-Point 연결 방식을 도입해 위에서 설명한 한계를 극복.
- PCIe PL (PCIe Protocol Layers) has 3 layers.
    1. **Physical layer**
        
        : 신호를 전달하는 물리적 전선과 회로 및 논리 장치
        
    2. **Data link layer**
        
        : 데이터 패킷 전송의 신뢰성과 오류 수정, 흐름 제어를 담당
        
    3. **Transaction layer**
        
        : 데이터 패킷을 구성하고 해석 (읽기/쓰기)
        

- **PCIe MD (Multilane Distribution)**
    
    : PCI Express 인터페이스에서 여러 개의 **Lane**(전송 경로)를 활용하여 데이터를 전송하는 방식을 나타낸 그림
    
- **PCIe TRBD (Transmit and Receive Block Diagrams)**
    
    : PCIe 데이터의 전송 및 수신 과정을 시각적으로 나타낸 그림
    

*QPI and PCI are integrated

</aside>
