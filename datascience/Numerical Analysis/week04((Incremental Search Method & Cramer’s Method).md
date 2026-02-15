### 1. Incremental Search Method

**[Step1]**

**Start with x₀ and h**

$$
x_n = x_{n-1} + h
$$


**[Step2]**

$$
f(x_n)f(x_{n-1})
$$

**> 0 ⇒ repeat Step2**

**< 0 ⇒ Step3 and repeat Step2**

**= 0 ⇒ Step4**

**[Step3]**

$$
x_r = \frac{x_l + x_u}{2} \\x\in[x_l, x_u]
$$


**[Step4]**

$$
\epsilon_a = |\frac {x_{r(present)}-x_{r(previous)}}{x_{r(present)}}|
$$


**[Step5]**

**If it satisfies this, stop the computation.**

$$
\epsilon_a < \epsilon_s 
$$

### 2. Cramer’s Method

calculate  $det(D)$

$$
a_1x+b_1y+c_1z=d_1\\a_2x+b_2y+c_2z=d_2\\a_3x+b_3y+c_3z=d_3
$$

$$
x = \frac {D_x}{D}, \space\ y = \frac {D_y}{D}, \space z = \frac {D_z}{D}
$$

$$
D = \begin{vmatrix} a_1 & b_1 & c_1 \\ a_2 & b_2 & c_2 \\ a_3 & b_3 &c_3 \end{vmatrix}
$$

$$
D_x = \begin{vmatrix} d_1 & b_1 & c_1 \\ d_2 & b_2 & c_2 \\ d_3 & b_3 & c_3 \end{vmatrix}, \space \space D_y = \begin{vmatrix} a_1 & d_1 & c_1 \\ a_2 & d_2 & c_2 \\ a_3 & d_3 & c_3 \end{vmatrix}, \space D_z = \begin{vmatrix} a_1 & b_1 & d_1 \\ a_2 & b_2 & d_2 \\ a_3 & b_3 & d_3 \end{vmatrix}
$$

- Linear Equation: a collection of two or more linear equations involving the same variables.
- Simultaneous Linear Equation: a set of two or more linear equations, each containing two or more variables that are solved together, to find a value that simultaneously satifies all the equations in the set.
