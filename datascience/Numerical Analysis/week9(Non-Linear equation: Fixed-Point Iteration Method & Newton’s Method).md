### Fixed-Point Iteration Method

<aside>

### Q)

$x_1^2 + x_1x_2 = 10 \\ x_2 + 3x_1x_2^2 = 57$

$x_1^{(0)} = 1.5$ ,   $x_2^{(0)} = 3.5$ ,  $\epsilon_a = 0.0001\%$

</aside>

<aside>

### A)

**Step1)**

$x_1 = \sqrt{10-x_1x_2}$

$x_2 = \sqrt{\frac{57-x_2}{3x_1}}$ 

**Step2)**

$x_1^{\space(1)} = \sqrt{10-x_1^{(0)}x_2^{(0)}}$

$x_2^{\space(1)} = \sqrt{\frac{57\space-\space x_2^{(0)}}{3x_1^{(1)}}}$ 

**Step3)**

$\epsilon_{x1}^{\space\space(1)} = |\frac {x_1^{(1)} - x_1^{(0)}}{x_1^{(1)}}|$ ,   $\epsilon_{x2}^{\space\space(1)} = |\frac {x_2^{(1)} - x_2^{(0)}}{x_2^{(1)}}|$

</aside>

---

### Newton’s Method

<aside>

### Q)

$x^2+xy = 10$

$y+3xy^2=57$

$x^{(0)} = 1.5$  , $y^{(0)} = 3.5$ , $\epsilon_a=0.0001\%$

</aside>

<aside>

### A)

**Step1)**

Let $f1$ and $f2$

$f_1(x,y) = x^2 + xy -10$

$f_2(x,y) = y + 3x^2 -57$

**Step2)**

Calculate  $\frac{\partial f_1}{\partial x}$ ,  $\frac{\partial f_1}{\partial y}$  ,  $\frac{\partial f_2}{\partial x}$ ,  $\frac{\partial f_2}{\partial y}$

Calculate $f_1(x_0, y_0), f_2(x_0, y_0)$

** Step3)** Find  $\triangle x$ , $\triangle y$

$\begin{pmatrix} \frac{\partial f_1}{\partial x} & \frac{\partial f_1}{\partial y} \\\\ \frac {\partial f_2}{\partial x} & \frac{\partial f_2}{\partial y} \end{pmatrix}$$\begin{pmatrix} \triangle x \\ \\\triangle y \end{pmatrix}$ $=$  $\begin{pmatrix} -f_1(x_0, y_0) \\ \\ -f_2(x_0,y_0) \end{pmatrix}$

**Step4)** Calculate $x^{(1)}$,  $y^{(1)}$

$x^{(1)} = x^{(0)} + \triangle x$ 

$y^{(1)} = y^{(0)} + \triangle y$

**Step5)** Calculate  $\epsilon_{x1}^{\space\space(1)}$ ,  $\epsilon_{x2}^{\space\space(1)}$

$\epsilon_{x1}^{\space\space(1)} = |\frac {x_1^{(1)} - x_1^{(0)}}{x_1^{(1)}}|$ ,   $\epsilon_{x2}^{\space\space(1)} = |\frac {x_2^{(1)} - x_2^{(0)}}{x_2^{(1)}}|$

</aside>
