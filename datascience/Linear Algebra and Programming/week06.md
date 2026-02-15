### 1. 행렬식 연산

$$
det(AB) =det(A)det(B)
$$

$$
det(A^{-1}) = \frac{1}{det(A)}
$$

$$
det(kA)=k^nA \\ (A_{n\times n})
$$

* 삼각행렬(상삼각행렬, 하삼각행렬, 대각행렬)의 행렬식: 주대각 성분의 곱 *
---
### 2. 블록행렬의 행렬식

- **‘영행렬’과 ‘단위행렬’을 부분행렬로 갖는 블록행렬의 행렬식**

$1)\space A_{n\times n},\space I_{m\times m},\space B_{n\times m},\space 0_{m\times n}$

$$
\begin{vmatrix}A&B \\ 0&I_m\end{vmatrix}=det(A)
$$

$2)\space A_{n\times n},\space I_{m\times m},\space B_{m\times n},\space 0_{n\times m}$

$$
\begin{vmatrix}I_m&B \\ 0&A\end{vmatrix}=det(A)
$$

- **‘영행렬’을 부분행렬로 갖는 블록행렬의 행렬식**

$1)\space A_{n\times n}, \space B_{m\times m},\space C_{n\times m},\space 0_{m\times n}$

$$
\begin{vmatrix}A & C \\ 0 & B \end{vmatrix} = det(A)det(B)
$$

$2)\space A_{n\times n}, \space B_{m\times m},\space C_{m\times n},\space 0_{n\times m}$

$$
\begin{vmatrix}A & 0 \\ C & B \end{vmatrix} = det(A)det(B)
$$

### 3. 행렬식으로 평행사변형의 넓이 구하기

꼭짓점의 좌표가 (0,0), (a,c), (b,d), (a+b, c+d)인 평행사변형의 넓이

$$|det\begin{pmatrix} a&b \\ c&d\end{pmatrix}|$$ $$\space = |ad-bc|$$

</aside>

<aside>

###  4. 동차연립선형방정식이 자명해만 가지기 위한 조건

$$
\begin{pmatrix} a&b \\ c&d\end{pmatrix} \begin{pmatrix}x\\y\end{pmatrix}=0
$$

$$
\space \space det\begin{pmatrix} a&b \\ c&d \end{pmatrix} \neq 0
$$

</aside>

<aside>


### 5. 행렬식으로 평면의 방정식 구하기

$$
(x_1,y_1,z_1),(x_2,y_2,z_2),(x_3,y_3,z_3) \\ \begin{vmatrix}x&y&z&1 \\ x_1&y_1&z_1&1 \\ x_2&y_2&z_2&1 \\ x_3&y_3&z_3&1\end{vmatrix}=0
$$

</aside>

<aside>



### 6. 행렬식으로 이차곡선의 방정식 구하기

$$
(x_1,y_1),(x_2,y_2),(x_3,y_3) \\ \begin{vmatrix}x^2+y^2&x&y&1 \\ x_1^2+y_1^2&x_1&y_1&1 \\ x_2^2+y_2^2&x_2&y_2&1 \\ x_3^2+y_3^2&x_3&y_3&1 \end{vmatrix}=0
$$

</aside>

<aside>



###  7. 수반행렬 (adjA)

$$
adjA=\begin{pmatrix} C_{11}&C_{12}&\dots &C_{1n} \\ C_{21}&C_{22} &\dots & C_{2n} \\ \dots&\dots & \dots &\dots \\ C_{n1} & C_{n2}&\dots & C_{nn}\end{pmatrix}^T=\begin{pmatrix} C_{11}&C_{21}&\dots&C_{n1} \\ C_{12}&C_{22}&\dots&C_{n2} \\ \dots&\dots&\dots&\dots \\ C_{1n}&C_{2n}&\dots&C_{nn} \end{pmatrix}
$$

</aside>

<aside>


  
###  8. 수반행렬의 성질

**1)**

$$
A\times adjA = det(A)I =\begin{pmatrix} det(A)&0&\dots &0 \\ 0&det(A)&\dots&0 \\ \dots&\dots&\dots&\dots \\ 0&0&\dots&det(A)\end{pmatrix}
$$

**2)**

$$
A^{-1}=\frac{1}{det(A)}adjA
$$

**3)**

$$
A_{n\times n} \space 일 \space 때,\\det(adjA)=det(A)^{n-1}
$$

**4)**

$$
adj(AB)=adjB\times adjA
$$

</aside>

<aside>


  
###  9. 크래머 공식

$$
Ax=b \\ x=A^{-1}\times b=\frac{1}{det(A)}adjA\times b
$$

</aside>
