### 1. Bisection Method

$$
x_r = \frac{x_l + x_u}2
$$

### 2. Fasle Position Method

$$
x_r = x_u - \frac{{f(x_u)(x_l-x_u)}}{f(x_l)-f(x_u)}
$$

### How to make a new interval(subinterval)

$$
f(x_l)f(x_r) < 0 :{lower} subinterval : x_u = x_r \\ f(x_l)f(x_r)>0:uppersubinterval:x_l=x_r\\f(x_l)f(x_r)=0:Terminate the computation
$$

### Type of Error ($\epsilon_t \space \& \space \epsilon_a$  must be smaller than $\epsilon_s$(error tolerance)

- True error (Eₜ)
    
    $$
    E_t  = |True.value - Approximate.value|
    $$
    
- Relative true error (ϵₜ)
    
    $$
    \epsilon_t = |\frac {E_t} {True.value}| \\ = |\frac {True.value - Approximate.value} {True.value}|
    $$
    
- Approximate error (Eₐ)

$$
E_a = |Present.approximate.value - Previous.approximate.value|
$$

- Relative approximate error (ϵₐ)

$$
\epsilon_a = |\frac {E_a}{Present.approximate.value}|=|\frac{Present.approximate.value-Previous.approximate.value}{Present.approximate.value}|
$$
