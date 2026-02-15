<aside>

### <전치행렬의 성질>

$$
(A^T)^T=A \\ (A+B)^T=A^T+B^T \\ (AB)^T=B^TA^T \\ (\alpha A)^T=\alpha A^T \\ (A^T)^{-1}=(A^{-1})^T
$$

</aside>

<aside>

### <대칭행렬 & 반대칭행렬>

$$
대칭행렬:A=A^T \\ 반대칭행렬: -A=A^T
$$

</aside>

<aside>

### <대각행렬>

: 주대각 성분을 제외한 모든 원소가 0인 정방행렬

- **대각행렬끼리의 곱**: 주대각 성분의 곱 (⇒ 대각행렬 형태)
</aside>

<aside>

### <대각합 tr(A)>

: 주대각 성분의 합

### <대각합의 성질>

- A,B,C가 정방행렬일 때만

$1) \space tr(A+B)=tr(A)+tr(B)$

$2) \space tr(cA)=c  \times tr(A)$

$3)\space tr(ABC)=tr(ACB)=tr(BAC) =tr(BCA)=tr(CAB)=tr(CBA)\space \space \space \space (어떻게\space 변환해도 \space같음)(단, ABC\neq ACB \neq BAC\neq BCA \neq CAB\neq CBA)$

- A,B가 정방행렬이 아니어도 됨

$4)\space tr(AB)=tr(BA)$

</aside>

<aside>

### <상삼각행렬 & 하삼각행렬>

- $상삼각행렬 \times 상삼각행렬 = 상삼각행렬$
- $하삼각행렬 \times 하삼각행렬 = 하삼각행렬$
</aside>

<aside>

### <블록행렬>

: 행렬의 특정 행과 열 사이를 경계로 나누어 부분행렬로 표현한 것

</aside>

<aside>

### <기본행렬의 역행렬>

- 기본행렬은 가역행렬이며, 기본행렬의 역행렬은 기본행렬이다.
- 두 행을 교환하는 기본행렬의 역행렬
    - $$E_1 = \begin{pmatrix} 0&1&0\\1&0&0\\0&0&1 \end{pmatrix}$$     $$E_1^{-1}=\begin{pmatrix} 0&1&0\\1&0&0\\0&0&1\end{pmatrix}$$
- 한 행을 상수배하는 기본행렬
    - $$E_2 = \begin{pmatrix} 1&0&0\\0&1&0\\0&0&a \end{pmatrix}$$    $$E_2^{-1}=\begin{pmatrix} 1&0&0\\0&1&0\\0&0&1/a\end{pmatrix}$$

- 한 행의 상수배를 다른 행에 더하는 기본행렬
    - $$E_3 = \begin{pmatrix} 1&0&0\\0&1&0\\a&0&1 \end{pmatrix}$$      $$E_3^{-1}=\begin{pmatrix} 1&0&0\\0&1&0\\-a&0&1\end{pmatrix}$$
</aside>

<aside>

### <행 동치>

$B=E_nE_{n-1}...E_1A$ 를 만족하는 $E_1, E_2,...,E_n$ 이 존재하면 $A$와 $B$는 행 동치이며,  $A$ ~ $B$로 표기

</aside>

<aside>

###  <기본행렬 곱에 의한 역행렬 계산>

$E_n…E_2E_1A=I$ 을 만족하는 $E_n…E_2E_1$에 대해,

$A^{-1} = E_n…E_2E_1$ 을 활용하여 역행렬을 구할 수 있음.

$pf)$  $E_n…E_2E_1AA^{-1}=IA^{-1}$

   ⇒  $E_n…E_2E_1=A^{-1}$

</aside>

<aside>

### <행연산을 이용한 역행렬 계산>

$[\space A\space |\space I\space]$  ⇒  $[\space I\space |\space A^{-1}\space ]$

</aside>

<aside>

### <자명해>

동차 연립선형방정식 $Ax=0$에서 $A$가 가역이라면, $x=0$인 자명해만 존재한다.

$pf)$

$Ax=0$

⇒ $A^{-1}Ax=A^{-1}0$

⇒ $Ix=0$

⇒ $x=0$

</aside>

<aside>

### <비자명해>

미지수의 개수 > 선형방정식의 개수 ⇒ $x \neq 0$ (비자명해)

</aside>
