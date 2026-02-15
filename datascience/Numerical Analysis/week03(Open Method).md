### 1. Newton Raphson Method

- Choose only one initial value ‘x₀’

$$
x_{i+1} = x_i - \frac {f(x_i)} {f'(x_i)}
$$

$$
\epsilon_a = |\frac {x_{i+1}-x_i} {x_{i+1}}|
$$

### 2. Secant Method

- Choose two initial values ‘x₋₁ and ‘x₀’

$$
x_{i+1} = x_i - \frac {f(x_i)(x_i-x_{i-1})}{f(x_i)-f(x_{i-1})}
$$

$$
\epsilon_a = |\frac {x_{i+1}-x_i} {x_{i+1}}|
$$

### ⭐️ Comparing ‘Bracketing Method’ and ‘Open Method’

- ‘**Bisection Method**’ and ‘**False Position**’ both need two initial guesses such as $x_l \space \& \space x_u$
- The root is located within an interval.
- Always work but converge slowly.

- ‘**Newton Raphson Method**’ needs one initial value such as  $x_0$
    
    ‘**Secant Method**’ needs two initial value such as $x_{-1}\space \& \space x_0$
    
- Don’t need to bracket the root.
- Not always work but converge much more quickly.
    
    → ‘Open Method’ can only be used for functions that are continuous and have a derivative. (연속이고 도함수가 존재하는 함수)
    
- ‘**Incremental Search Method**’ uses  $x_0 \space \& \space h$
