### Euler Method

<aside>

### Q) calculate $f(\alpha)$

$f'(x) = a+bx+cx^2 + \dots \\f(n) = p\\ h$

</aside>

<aside>

### A)

$x_{n+1} = x_n + h$

$f(x_{n+1}) = f(x_n) + hf'(x_n)$

</aside>

---

### Heun Method

<aside>

### Q) calculate $f(\alpha)$

$f'(x)= a+bx +cx^2+\dots$
$f(x_0) = k$   (Interval = $[m,n]$)

$h = p$

</aside>

<aside>

### A)

$x_{i+1} = x_i + h$

$y_{i+1}^0 = y_i + hf'(x_i,\space y_i)$

$y_{i+1} = y_i + h {f'(x_i,\space y_i) + f'(x_{i+1}, \space y_{i+1}^0) \over 2}$

</aside>
