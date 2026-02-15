<aside>
💡

### Organization and Arichitecture

Organization is how operational attributes are linked together and contribute to realizing the architectural specification.

Organization comes after the decision of Architecture first.

Architecture describes what the computer does.

**Summary**

**Computer Organization**

- is defined as arranging, classifying things together logically to maximize functional convenience.
- The operational units and their interconnections that realize the architectural specifications.
- Hardware details transparent to the porgrammer, control signals, interfaces between the computer and peripherals, memory technology used.

**Computer Architecture**

- help us define the functional capabilities and requirements for the computer system.
- Attributesof a system visible to the programmer.
- Have a direct impact on the logical execution of a program.
- Instruction set, number of bits used to represent various data types, I/O mechanisms, techniques for addressing memory.
</aside>

<aside>
💡

**IBM system / 370 architecture**

- This model was compatible with another model. (→ called “ industry’s first planned family of computers.”)
- This architecture still remains to this day as the architecture of IBM’s mainframe computers.

- introduced in 1964.
- incompatible with older IBM machines

**💡 IBM system / 360**

- IBM’s mainframe product line has survived to this day.

- New models retain the same architecture of old models so that the customer’s software investment is protected.

- could upgrade to a more expensive and faster model without having to abandon original software.

- introduced in 1970.

</aside>

<aside>
💡

### Structure and Function

Hierarchical system

→ : interrelated subsystems

→ essential to both design and description

**Structure**

- The way in which components relate to each other.
- Main structural components of computer
    - `CPU`: controls the computer operation and performs data processing functions.
    - `Main memory`: stores data.
    - `System Bus` (Interconnection): communication among CPU, main memory, I/O.
    - `I/O`: moves data between the computer and its external environment.
- Main structural components of CPU
    - `Control Unit`: controls the CPU operation.
    - `ALU`(Arithmetic and Logic Unit): perfroms the computer’s data processing function
    - `Registers`: provide storage internal to the CPU
    - `CPU Interconnection`: communicates among the Control unit, ALU, Registers.

**Function**

- The operation of individual components as part of the structure.

<aside>
⭐

- 4 basic functions that a computer can perform:
    - `Data processing` : provided by gates
    - `Data storage`
    
    : provided by Memory Cells
    
    - `Data movement`
    - `Control`
</aside>

**Structure of Multicore computer**

- `CPU`
    
    : Fetches and executes instructions.
    
- `Core`
    
    : An individual processing unit on a processor chip ; Specialized processing units
    
    In terms of functionality, the cores of CPU of muticore computer are same as the cores of single-CPU.
    
- `Processor`
    
    : Interprets and executes instructions.
    
    Contains one or more cores.
    
    Called as a multicore processor if it contains multiple cores.
    
</aside>

<aside>
💡

**Cache Memory**

- multiple layers of memory (between the processor and main memory)

- smaller and faster than main memory.

- It can speed up accesing to memory.

- using multiple levels of cache improves performance.

</aside>

<aside>
💡

### Registers

**MBR (Memory Buffer Register)**

- Contains a word which would be stored in memory or sent to the I/O unit.
- Receiving a word from ‘memory’ or ‘I/O unit’.

**MAR (Memory Address Register)**

- Specifies the address in memory of the word which would be read into the MBR or written from the MBR.

**IR (Instruction Register)**

- Contains the 8-bit opcode(operation code) instruction being executed.

**IBR (Instruction Buffer Register)**

- Employed to temporarily hold the right-hand instruction from a word in memory.

PC (Program Counter)

- Contains the address of the next instruction pair to be fetched from memory

AC (Accumulator) & MQ (Multiplier Quotient)

- Eployed to temporarily hold operands and results of ALU operations.

</aside>

<aside>
💡

### History of computers

[First Generation: Vaccum Tubes]

- Vaccum tubes were used for digital logic elements and memory.
- IAS computer
    - Fundamental design approach was the `stored program` concept.
    - ‘Prototype’ of all subsequent general-purpose computers.
    - Completed in 1952

[Second Generation: Transistors]

- Transistors made computer `smaller`, `cheaper`, `more accessible`
- Arithmetic, logic units, and control units are more complex than the first generation. → Transistor led to breakthroughs in computer system design.
- High-level programming languages
- Provides ‘system software’.
- Dissipates less heat than a vaccum tube.
- Solid state device made from silicon
- Invented at Bell Labs in 1947.
- In late 1950’s, fully transistorized computers were commercially available.

[Third Generation: Integrated Circuit]

- Invented in 1958
- Discrete component
- `Moore’s Law` : Observed the number of transistors which could be put on a single chip was doubling every year.

[Later Generation: Microporcessor ; Semiconductor Memory]

- The density of elements on processor chips continued to rise.
- 1971 Intel developed 4004: First chip to contain all of a CPU on a single chip.
- 1972 Intel developed 8008: First 8-bit Microprocessor
- 1974 Intel developed 8080: First general-purpose Microprocessor (Faster, has a richer instruction set, has a large addressing capability)
</aside>

<aside>
⭐

### Fundamental Computer Elements

1. `Gate`
2. `Memory Cell`
</aside>

<aside>
💡

### The evolution of the Intel x86 Architecture

- Two processor families: ‘Intel x86’, ‘ARM architecture’
- Current ‘Intel x86’ offerings represent the results of decades of design effort on CISCs.
    
    CISCs: Complex Instruction Set Computers
    
    RISC: Reduced Instruction Set Computer
    
- ‘ARM’(Advanced RISC Machine) architecture is a processor that has evolved from RISC design principles and is used in embedded systems.
</aside>

<aside>
💡

### Embedded systems

- The use of electronic and software within a product.
- Today many devices that use electric power have an embedded computing system.
- Two general approaches to developing an embedded OS(Operating System)
    1. Application processors (for general-purpose)
        
        : adapt an existing OS for the embedded system.
        
    2. Dedicated processors
        
        : design and implement an OS intended solely for embedded use.
        
- Embedded system use case: IoT(Internet of Things)
    
    : expanding interconnection of smart devices, ranging from appliances to tiny sensors.
    
</aside>

<aside>
💡

### Cloud Computing

: A model for enabling to access to a configurable computing resources that can be rapidly provisioned and released with minimal management effort or service provider interaction.

The individual or company only needs to pay for the storage capacity and services.

Cloud provider takes care of security.

### 💡 Cloud Networking

: The networks and network management functionality that required for cloud computing to enable.

### 💡 Cloud Storage

: subset of cloud computing.

</aside>
