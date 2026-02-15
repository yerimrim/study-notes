<aside>
💡

### Decision Making Under Uncertainty

1. Maximax Criterion
    1. Choose the **Highest** value in each Alternative
    2. Choose the Alternative which has the **Highest** one
2. Maximin Criterion
    1. Choose the **Lowest** value in each Alternative
    2. Choose the Alternative which has the **Highest** one
3. Minimax Regret Criterion
    1. **Maximum** value in each state of nature - Each value in each state of nature
    2. Choose the **maximum** in each alternative
    3. Choose the **minimum** alternative
4. **The Hurwicz / Realism Criterion**
    - $\alpha$(Highest value of an Alternative) + $(1-\alpha)$(Lowest value of an Alternative)
    - Choose the **Highest** one
5. **The Equal Likelihood / Laplace Criteria**
    - $p= {1\over n}$ (n: the number of Alternatives)
    - $\sum p\times$(each value in an Alternative)
    - Choose the **Highest** one
</aside>

<aside>
💡

Game Theory

1. **Pure Strategy** (Zero-Sum Game) (2 Strategies)
    1. The thing that wants a high one ⇒ Maximin
    2. The thing that wants a low one ⇒ Minimax
    3. ‘Saddle Point’: When the Minimax value and the Maximin value are equal.
2. **Mixed Strategy** (Non-Zero-Sum Game) (More than 2 Strategies)
    1. Calculate the Maximin, Minimax (same as Pure Strategy)
    2. Erase the column including the **highest Minimax**
    3. Erase the row including the **lowest Maximin**
    4. Calculate  $p_a, p_b$
        - $p_aS_{b1}+(1-p_a)S_{b1} = p_aS_{b2}+(1-p_a)S_{b2}$
            - ⇒ $p_a$: probability to use $S_{a1}$
        - $p_bS_{a1}+(1-p_b)S_{a1} = p_bS_{a2}+(1-p_b)S_{a2}$
            - ⇒ $p_b$: probability to use $S_{b1}$
    5. Put $p_a,p_b$ value into previous equations.
    6. Find the ‘Saddle Point’.
</aside>
