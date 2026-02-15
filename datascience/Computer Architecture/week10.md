<aside>

### Types of Number System

- Binary: use Base-2 (0,1) ⇒ representing all data and instructions
- Octal: use Base-8 ⇒ embedded systems
- Decimal: use Base-10 (0~9) ⇒ counting, finance, measurement, and commerce
- Hexadecimal: use Base-16 (0~15) ⇒ used for memory addressing and error codes

* ASCII is what I use s.t. A, B, C
and these have own specific Binary, Octal, Decimal, Hexadecimal numbers.

</aside>

<aside>

## The Decimal System (radix = 10, 0~9)

- : have a base or radix of ‘10’
    - Leftmost digit ⇒ Most significant digit
    Rightmost digit ⇒ Least significant digit
    - ex)  $83 = (8*10^1) + (3*10^0)$
    ⇒ 8 is the most significant digit and 3 is the least significant digit.
</aside>

<aside>

### Positional Number System

$10^2$ ⇒ position 2

$10^{-2}$ ⇒ position -2

</aside>

<aside>

### Converting between Other Base systems and Decimal

- How to convert the Decimal Number to the Base-7 Number
    1. Divide the Decimal number by 7.
    2. The remainder from the previous divide is to being the Rightmost digit.
    3. Divide the quotient of the previous divide by 7.

- How to convert the Base-7 Number to the Decimal Number
    1. Base-7 number = 245 ⇒ $2*7^2 + 4*7^1 + 5*7^0 = 98 +28+5 = 124$ 
    2. **$\therefore$**  Decimal number = 124
</aside>

<aside>

### The Binary System (radix = 2, 0 and 1)

- $\red{10}_2 = \red1*2^1+\red0*2^0$
- $\red{1001.101} = \red1*2^3+\red0*2^2+\red0*2^1+\red1*2^0+\red1*2^{-1}+\red0*2^{-2}+\red1*2^{-3} = 9.625_{10}$
</aside>

<aside>

### Converting between binary and decimal

- How to convert Decimal to Binary
    - Method 1 (Integers)
        1. Divide the Decimal number by 2.
        2. The remainder from the previous divide is to being the Rightmost digit.
        3. Divide the quotient of the previous divide by 2. (until the quotient becomes smaller than 2)
        
        ex) 11_0 ⇒ 11/2 =5 \dots 1
        
    - Method 2 (Fractions)
        1. ~~~
        
- How to convert Binary to Decimal
</aside>

<aside>

### Hexadecimal notation (radix = 16, 0~15)

- nibble : sets of four bits (s.t. 0000, 1000, 1001, 1010)
</aside>

<aside>

### Converting among Decimal, Binary, and Hexadecimal

- How to convert Binary to Hexadecimal
    
    ex) 001100100 ⇒ 0/0110/0100 ⇒ 0000/0110/0100 ⇒ 0/6/4 = 64 
    
</aside>

<aside>

### Converting Octor to Decimal, Binary, and Hexadecimal

- Octal to Decimal
- Decimal to Octal
- Octal to Hexadecimal
- Hexadecimal to Octal
- Octal to Binary
- Binary to Octal

* Cannot convert directly Octal to Hexadecimal.
Have to convert Octal to Decimal first, then convert the Decimal to Binary or Hexadecimal.

</aside>
