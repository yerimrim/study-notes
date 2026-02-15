<aside>

- External devices that we connect to I/O modules have **three** categories.
    1. Human readable
        
        : human can read data from device.
        
    2. Machine readable 
        
        : 기계가 **사람의 개입 없이** 직접 데이터를 읽고 처리할 수 있는 장치
        
    3. Communication
        
        : 사람 개입 x, device끼리 데이터 송수신 및 연결에 초점
        
- Organization of external device
    - Control logic: 외부 장치의 작동을 **제어**하고 **조정**
    - Buffer: 데이터 전송 간의 **속도 차이**를 조정
    - Transducer: 한 형태의 에너지를 다른 형태로 변환하여 외부 신호를 처리
</aside>

<aside>

- I/O Functions
    1. Control and timing
    2. Processor communicaiton
    3. Device communication
    4. Data buffering
    5. Error detection

- I/O Module: Data Registers, Status/Control Registers, I/O Logic, External device interface logic

- Techniques of I/O opeations
    - Programmed I/O and Interrupt-driven I/O both have drawbacks.
        
        So, when the large amount of data are to be moved, using DMA is more efficient.
        
    1. `Programmed I/O` (no interrupts)
        - Drawbacks: must wait until the I/O operation is completed.
    2. `Interrupt-driven I/O` (using interrupts)
        - Alternative of Programmed I/O.
        - 하던 데이터 처리 작업을 멈추고, 새로운 데이터를 받음 ⇒ 끝날 때까지 기다릴 필요 없음.
        - Two Design Issues in using Interrupt-drive I/O:
            - 여러 개의 I/O modules를 사용 ⇒ 여러 장치가 동시에 인터럽트를 발생시킬 수 있음 ⇒ 어떤 장치가 인터럽트를 발생시켰는가?
            - 여러 개의 인터럽트가 발생 ⇒ 어떤 인터럽트를 우선적으로 처리할 것인가?
        - Two Design Issues 해결방안1: Device Identification
            1. Multiple interrupt lines: 가장 간단, but 정확한 장치 식별에는 한계
            2. Software poll: 시간이 오래 걸리지만 모든 장치를 확인
            3. Daisy chain (hardware poll, vectored): 벡터를 사용하여 더 빠르게 장치를 식별
            4. Bus arbitration (vectored): 벡터를 사용하여 더 빠르게 장치를 식별
        - Two Design Issues 해결방안2: Use of 82C59A Interrupt Controller
            1. Fully nested: 고정된 우선순위에 따라 처리됨
            2. Rotating: 동일한 우선순위를 가진 장치들이 순차적으로 우선순위를 교체하며 처리됨
            3. Special mask: 특정 장치의 인터럽트를 무시하거나 차단 ⇒ 다른 장치의 인터럽트를 우선적으로 처리 가능
    3. `Direct Memory Access(DMA)` (using interrupts)
        - CPU개입 없이, **데이터가 DMA 컨트롤러를 통과**
        - 그동안 CPU는 다른 작업 수행 가능 ⇒ System performance is up!
        - DMA Configurations
            1. Single-bus, detached DMA
            2. Single-bus, Integrated DMA-I/O
            3. I/O bus
- `Fly-By DMA`
    - CPU개입 없이, **데이터가 DMA 칩을 통과하지 않고**, 바로 **I/O 장치와 메모리** 간에 전송됨
- `Direct Cache Access (DCA)`
    - 네트워크 장치의 데이터 전송 속도가 빠르게 증가하면서 **DMA의 성능 한계 ⇒ DCA 필요**
    - Cache Memory에 바로 저장 ⇒ DMA보다 빠름
    - DMA보다 용량이 작음
    - 단, 캐시는 용량이 작으므로, **임시로 자주 사용되는 데이터**만 저장.

- I/O Commands (명령): Control, Test, Read, Write

- I/O Mapping (I/O 장치와 CPU 간의 통신을 처리하는 방법)
    - Memory mapped I/O
        - 장치와 메모리가 같은 주소 공간을 공유
        - I/O 작업을 메모리 읽기/쓰기와 동일하게 처리
        - 프로그래밍이 간편
    - Isolated I/O
        - 장치가 별도의 주소 공간에 위치
        - I/O를 위한 특별한 명령어가 필요
        - 메모리와의 구분이 명확해지는 장점

- Intel 8255A Control Word
    - **Mode 0**: 입출력 중 하나로 고정, 단순히 데이터 입출력 기능만 함.
    - **Mode 1**: 입출력 방향 변경 가능, 독립적 ⇒ 둘 다 입력 방향일 수도 있음, 입출력 기능뿐만 아니라 **핸드쉐이킹** 기능도 함.
    - **Mode 2**: 입출력 방향 변경 가능, 상대적 ⇒ 서로 반대 방향이어야 함. 주로 복잡한 데이터 통신을 위한 모드

- I/O Channel Architecture
    1. Selector Channel: **하나의 입력**만 받아 ****출력
    2. Multiplexor Channel: **여러 입력**을 받아 하나의 출력으로 다중 전송

- External interconnection standards
    - : 컴퓨터와 외부 장치 간에 데이터를 주고받기 위한 규격
    - 이 규격은 서로 다른 제조업체의 기기들이 원활하게 상호작용할 수 있도록 보장.
    - 데이터 전송의 신뢰성과 효율성을 높임.
    1. USB (Universal Serial Bus)
    2. Fire Wire Serial Bus
    3. SCSI (Small Control System Interface)
    4. Thunderbolt
    5. InfiniBand
    6. PCIe
    7. SATA
    8. Ethernet
    9. WiFi

- IBM zEnterprise EC12 I/O structure
</aside>
