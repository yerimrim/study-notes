### Linear Interpolation (Given 2 data points)

<aside>

### Q)

$(x_0, f(x_0)),(x_1,f(x_1)), \space True \space value$

</aside>

<aside>

### A)

**Step1)**

$b_0 = f(x_0)$

$b_1 = f[x_1,x_0] = {f(x_1-x_0)\over x_1-x_0}$

$f_1(x) = b_0 + b_1(x-x_0)$

**Step2)**

$\epsilon_t = |\frac{True\space value - f_1(n)}{True\space value}|$

</aside>

---

### Quadratic Interpolation (Given 3 data points)

<aside>

### Q)

$(x_0, f(x_0)), (x_1,f(x_1)), (x_2, f(x_2)), \space True\space value$

</aside>

<aside>

### A)

**Step1)**

$b_0 = f(x_0)$

$b_1 = f[x_1,x_0]= \frac{f(x_1)-f(x_0)}{x_1-x_0}$

$b_2= f[x_2,x_1,x_0]=\frac{\frac{f(x_2)-f(x_1)}{x_2-x_1}-b_1}{x_2-x_0}$

**Step2)**

$f_2(x) = b_0\space + \space b_1(x-x_0)\space + \space b_2(x-x_0)(x-x_1)$

**Step3)**

$\epsilon_t = |\frac{True\space value - f_2(n)}{True\space value}|$

</aside>
