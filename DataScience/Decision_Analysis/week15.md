### Logistic Regression

$w_i:$ feature별 weight

- Logit function
    - $y=\sum w_ix_i +b$
- p ($y:$ from Logit function)
    - $\sigma(y)={1\over1+e^{-y}}$
- Classify the $p$ (decision)
    - $p\geq0.5$ ⇒ 1
    - $p<0.5$ ⇒ 0
- Predict error ($y_i$: target feature)
    - $Log-loss=-y_ilog(p_i)-(1-y_i)log(1-p_i)$
    - If the log-loss in an iteration ≤ tolerance error, the computation is terminated
- Update
    - SAG: $w_{t+1}=w_t+\eta({1\over n}\sum(y-p))$
    - Stochastic Gradient: $w_{t+1}=w_t+\eta(y-p)$
