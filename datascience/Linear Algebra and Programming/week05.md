<aside>

### ⭐️<LU 분해>

$A=LU$ ($L$: 하삼각행렬, $U$: 상삼각행렬)

- LU분해가 성립할 조건: 행렬 A를 행연산을 통해 상삼각행렬로 만들 수 있는 경우.

Method)

Step1) 행렬 A를 기본 행 연산을 통해 U(상삼각행렬)로 변환 (i.e. 행사다리꼴 만들면 됨.)

Step2) $A=LU <=> L=AU^{-1}$ 를 활용하여 L(하삼각행렬) 구함.

</aside>

<aside>

### <행렬식>

- 정방행렬$(n\times n)$에서만 정의됨.

$$\begin{vmatrix} a \end{vmatrix} = a$$

$$\begin{vmatrix} a & b \\ c & d \end{vmatrix} = ad-bc$$

</aside>

<aside>

### <소행렬식>

$$A = \begin{pmatrix} a & b & c \\ d&e&f\\g&h&i \end{pmatrix}$$

$$A_{11} = \begin{vmatrix} e&f\\h&i \end{vmatrix}$$   $$A_{12} = \begin{vmatrix} d&g \\ f&i \end{vmatrix}$$ $$\dots$$

</aside>

<aside>

### <여인수>

$C_{ij} = (-1)^{i+j}A_{ij}$

</aside>
