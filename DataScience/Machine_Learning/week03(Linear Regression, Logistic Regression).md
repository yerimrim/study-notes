<aside>

### Linear Regression

- 모형:
$y=\beta _0+\beta_1x_1+\beta_2x_2+\cdots$
- $\hat y = X\hat\beta$
$$\begin{bmatrix} \hat y_1 \\ \hat y_2 \\ \vdots\\ \hat y_n \end{bmatrix} = \begin{bmatrix} x_{11} & x_{12} & \cdots & x_{1m} & 1 \\ x_{21} & x_{22} & \cdots & x_{2m} & 1 \\ \vdots & \vdots & \vdots & \vdots \\ x_{n1} & x_{n2} & \cdots & x_{nm} & 1 \end{bmatrix} \begin{bmatrix} \hat\beta_1 \\ \hat\beta_2 \\ \vdots \\ \hat\beta_n \\ \hat\beta_0 \end{bmatrix}$$

- $\hat\beta$ 구하는 방법
    - 최소제곱법: **Input feature가 1개**일 때 (i.e. $\beta_0,\beta_1$만 구하면 될 때)
        - $\beta_1 = \dfrac{S_{xy}}{S_{xx}}, \space \beta_0= \bar y-\beta_1 \bar x$
    - 정규방정식 (Normal Equation): **Input feature가 여러 개**일 때
        - $\hat\beta = (X^TX)^{-1}X^Ty$

- 평가
$MSE = \dfrac{1}{n} \sum_{i=1}^n (y_i-\hat y_i)^2 = \dfrac{1}{n} \sum_{i=1}^n (y_i-\beta_0-\beta_1x_1-\beta_2x_2-\cdots)^2$
</aside>

<aside>

### Logistic Regression (Classification)

- 확률이 0.5보다 크면 ⇒ 1, 작으면 ⇒ 0
- 시그모이드 함수 (Sigmoid Function)
$\sigma(z)= \dfrac{1}{1+e^{-z}}$
</aside>
