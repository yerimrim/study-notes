<aside>

### 대칭행렬

- 대칭행렬 A에 대해 $v^TAw = w^TAv$
- 대칭행렬 A의 역행렬 = 대칭행렬
- 임의의 행렬 A에 대해  $A^TA, \space AA^T =$  대칭행렬

### 대칭행렬의 고유값과 고유벡터를 이용한 전개

- 대칭행렬 A의 고유값 $\lambda_i$, 고유벡터 $v_i$에 대해 $A = \lambda_1v_1v_1^T+\cdots\lambda_nv_nv_n^T$
</aside>

<aside>

### ⭐️ 이차형식

: $x^TAx$

$a_1x^2+a_2y^2+a_3z^2+a_4xy+a_5yz+a_6zx$

$= \begin{pmatrix} x&y&z\end{pmatrix}$$\begin{pmatrix} a_1 & a_4/2 &a_6/2\\a_4/2&a_2&a_5/2\\a_6/2&a_5/2&a3 \end{pmatrix}$$\begin{pmatrix} x\\y\\z\end{pmatrix}$  

### ⭐️주축정리

**혼합항이 없는 이차형식으로 나타내시오.**

⇒  $y^TDy$ (D는 행렬 A의 고유값에 대한 대칭행렬, $D = P^TAP$)

### 이차형식의 최댓값

이차형식을 나타낸 대칭행렬 A에 대해

$||x|| =1$ 이면, $x^TAx$, 즉 이차형식의 최댓값 = 가장 큰 고유값 $= max\{\lambda_i\}$

### 이차형식의 최솟값

이차형식을 나타낸 대칭행렬 A에 대해

$||x|| =1$ 이면, $x^TAx$, 즉 이차형식의 최솟값 = 가장 작은 고유값 $= min\{\lambda_i\}$

</aside>

<aside>

### 대칭행렬의 정부호

- 양의 정부호: $\lambda >0$
- 양의 준정부호: $\lambda \geq 0$
- 음의 정부호: $\lambda < 0$
- 음의 준정부호: $\lambda \leq 0$
- 부정부호: $\lambda >0 \space \& \space \lambda <0$ (둘 다 가짐)
</aside>

<aside>

### ⭐️ 고유값 분해

- $A = PDP^{-1} = PDP^T$
- $D$: $A^TA$ 의 고유값을 크기가 작은 순서로 나타낸 행렬

- $P$: $A^TA$의 고유벡터를 정규직교화한 후, $D$에 대응하게 나타낸 행렬

### ⭐️ 특잇값 분해 (SVM)

- 특잇값: $\sigma_i = \sqrt{\lambda_i}$
- 특잇값 분해: $A=U\sum V^T$

- $U$ ⇒  $AA^T$의 고유벡터를 정규직교화한 후, $\sum$에 대응하게 나타낸 행렬
- $\sum$   ⇒  $A^TA$의 특잇값($\sigma_i = \sqrt{\lambda_i}$)을 큰 것부터 왼쪽에 배열한 행렬 (행렬의 크기는 $A$와 같음, 부족한 부분은 0으로 채워 넣음)
- $V$  ⇒  $A^TA$의 고유벡터를 정규직교화한 후, $\sum$에 대응하게 나타낸 행렬

- $||Av_i||=\sqrt{\lambda_i}=\sigma_i$ ($v_i$는 $A^TA$의 고유벡터)

* $A^TA, \space AA^T$의 양의 고유값은 항상 같음.

</aside>
