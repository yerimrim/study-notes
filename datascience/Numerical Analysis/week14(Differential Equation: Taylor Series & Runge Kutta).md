### Talyor Series

<aside>

### Q)

$f(x) = x^3 -x^2 + 0.5x +1$

$x_i = 0,\space  x_{i+1} = 0.5, \space \triangle x = 0.5$

</aside>

<aside>

### A)

**Step1) Calculate $f(x_{i+1})$**

$True\space value = f(x_{i+1})$ 

**Step2) Estimate $f(x_{i+1})$**

- $0^{th}$ order
    - $f(x_{i+1}) = f(x_i)$
- $1^{st}$ order
    - $f(x_{i+1}) = f(x_i) + f'(x_i){\triangle x \over 1!}$
- $2^{nd}$  order
    - $f(x_{i+1}) = f(x_i) + f'(x_i){\triangle x \over 1!} + f''(x_i){(\triangle x)^2 \over 2!}$
- $3^{rd}$ order
    - $f(x_{i+1}) = f(x_i) + f'(x_i){\triangle x \over 1!} + f''(x_i){(\triangle x)^2 \over 2!} + f'''(x)  {(\triangle x)^3 \over 3!}$
- $n^{th}$ order
    - $f(x_{i+1}) = f(x_i) + f'(x_i){\triangle x \over 1!} + f''(x_i){(\triangle x)^2 \over 2!} + f'''(x)  {(\triangle x)^3 \over 3!} +\dots + f^n(x_i){(\triangle x)^n \over n!}$

**Step3) Calculate the error**

$error = |{True\space value - Approximation\over True \space value}|$

</aside>

---

### Runge Kutta

<aside>

### Q)

Estimate the value of $y_1$ by using  $n^{th}$ order

${dy \over dx} = {y - x^2y\over 2}$

$h = 0.5, \space y(0) = 2$

</aside>

<aside>

### A)

**Step1) Calculate  $k_1, k_2, k_3$**

- $1^{st} order$
    - $k_1 = hf(x_i, y_i)$

- $2^{nd} order$
    - $k_1 = hf(x_i,y_i)$
    - $k_2 = hf(x_i+h,\space y_i+k_1)$

- $3^{rd} order$
    - $k_1 = hf(x_i, y_i)$
    - $k_2 = hf(x_i+{1\over 2}h,\space y_i+{1\over2}k_1)$
    - $k_3 = hf(x_i+h, \space y_i-k_1+2k_2)$

- $4^{th} order$
    - $k_1 = hf(x_i, y_i)$
    - $k_2 = hf(x_i+{1\over2}h,\space y_i+{1\over 2}k_1)$
    - $k_3 = hf(x_i+{1\over 2}h, \space y_i+{1\over 2}k_2)$
    - $k_4 = hf(x_i+h, \space y_i+k_3)$

**Step2) Calculate $y_i$**

- $1^{st} order$
    - $y_{i+1} = y_i + k_1$
- $2^{nd} order$
    - $y_{i+1} = y_i + {k_1+k_2\over 2}$
- $3^{rd} order$
    - $y_{i+1} = y_i + {k_1 + 4k_2 + k_3 \over 6}$

**4th**

- $4^{th} order$
    - $y_{i+1} = y_i + {k_1+2k_2+2k_3+k_4\over 6}$
</aside>
