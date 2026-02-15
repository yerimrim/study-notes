### Newton’s Interpolating Polynomial

<aside>

### Q)

$(x_0,f(x_0)),(x_1,f(x_1)),(x_2,f(x_2)),(x_3,f(x_3)), \space True\space Value$

</aside>

<aside>

### A)

**Step1) Calculate  $b_0, b_1,b_2,b_3$**

$b_0=f(x_0)$

$b_1 =f[x_1,x_0]=\frac{f(x_1)-f(x_0)}{x_1-x_0}$

$b_2=f[x_2,x_1,x_0]=\frac{\frac{f(x_2)-f(x_1)}{x_2-x_1}-\frac{f(x_1)-f(x_0)}{x_1-x_0}}{x_2-x_0} = \frac{\frac{f(x_2)-f(x_1)}{x_2-x_1}-b_1}{x_2-x_0}$

$b_3 = f[x_3,x_2,x_1,x_0]=\frac{\frac{\frac{f(x_3)-f(x_2)}{x_3-x_2}-\frac{f(x_2)-f(x_1)}{x_2-x_1}}{x_3-x_1}-\frac{\frac{f(x_2)-f(x_1)}{x_2-x_1}-\frac{f(x_1)-f(x_0)}{x_1-x_0}}{x_2-x_0}}{x_3-x_0}$

$= \frac{\frac{\frac{f(x_3)-f(x_2)}{x_3-x_2}-\frac{f(x_2)-f(x_1)}{x_2-x_1}}{x_3-x_1}-b_2}{x_3-x_0}$

**Step2) Calculate $f_3(n)$**

$f_3(x) = b_0+b_1(x-x_0)+b_2(x-x_0)(x-x_1)+b_3(x-x_0)(x-x_1)(x-x_2)$

**Step3) Calculate True error  $(\epsilon _t)$**

$\epsilon_t = |\frac{True\space value - f_3(n)}{True\space value}|$

</aside>

---

### Lagrange Interpolating Polynomial

<aside>

### Q)

$(x_0,f(x_0)),(x_1,f(x_1)),(x_2,f(x_2)),(x_3,f(x_3)), \space True\space Value$

</aside>

<aside>

### A)

**Step1) Calculate $f_3(n)$**

$f_3(x) = \frac{(x-x_1)(x-x_2)(x-x_3)}{(x_0-x_1)(x_0-x_2)(x_0-x_3)}f(x_0)+\frac{(x-x_0)(x-x_2)(x-x_3)}{(x_1-x_0)(x_1-x_2)(x_1-x_3)}f(x_1)+\frac{(x-x_0)(x-x_1)(x-x_3)}{(x_2-x_0)(x_2-x_1)(x_2-x_3)}f(x_2)+\frac{(x-x_0)(x-x_1)(x-x_2)}{(x_3-x_0)(x_3-x_1)(x_3-x_2)}f(x_3)$

**Step2) Calculate True error** $(\epsilon_t)$

$\epsilon_t =  |\frac{True\space value - f_3(n)}{True\space value}|$

</aside>
