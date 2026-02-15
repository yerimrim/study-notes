<aside>

### Boolean Algebra

Basic logical operation

- NOT
- AND: 곱이 1일 때 ⇒ 1
- OR: 합이 1일 때 ⇒ 1

                     +

- NAND: 곱이 0일 때 ⇒ 1
- NOR: 합이 0일 때 ⇒ 1
- XOR : contains an odd number of ones. (0001, 0100, 1110, …)

![Screenshot 2024-11-22 at 2.55.16 AM.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a3770338-9706-4edc-a979-958163ea1fa2/47ca215d-d2d7-4812-84c1-28d781f4a49d/Screenshot_2024-11-22_at_2.55.16_AM.png)

</aside>

<aside>

### Gates

</aside>

<aside>

### Combinational Circuits

: don’t remember the past operation (ex: ALU)

- Implementation of Boolean Functions
    - SOP (Sum of Product)
        - When the instruction contain more 0.
        - AND ⇒ OR
    - POS (Product of Sum)
        - When the instruction contain more 1.
        - OR ⇒ AND
- Multiplexers
Input= 4, Output = 1

$\bar A + A$

- Decoder (Single Input and Multiple Outputs s.t. ‘n-to-2^n’)
    - Demultiplexer

- Read-Only-Memory
- Adders (Program Counter)
</aside>

<aside>

### Sequential Circuits

: depends on the past operation

- Flip-Flops
    
    : Has two outputs, which are **always** the **complement** of each other.
    
    - Clocked S-R Flip-Flop
    - D  Flip-Flop
        - Adding ‘NOT’
    - J-K  Flip-Flop
        - Adding ‘Feed back’
- Registers
    - Parallel Register
    - Shift Register
- Counters
    - Asynchronous (delay O)
    - Synchronous (delay X)
</aside>

<aside>

### Programmable Logic Devices (PLD)

- Programmable Logic Array (PLA)
    
    : A relatively small PLD
    
- Field-Programmable Gate Array (FPGA)
    
    : A PLD featuring a general structure that allows very high logic capacity
    
</aside>
