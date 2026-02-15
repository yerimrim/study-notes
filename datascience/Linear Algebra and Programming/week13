<aside>

### 정사영

- 직교기저 $\{ u_1, u_2\}$로 하는 $W$위로의 정사영  $\hat x=proj_{u_1}x+proj_{u_2}x$
- 직교성분 $z = x-\hat x$ (유일하다.)
</aside>

<aside>

### QR 분해

1. $Q=$ A의 열벡터를 정규직교화한 행렬 
2. $A=QR \Longleftrightarrow R = Q^{-1}A = Q^TA$ 를 이용해 상삼각행렬 $R$ 계산
3. $A=QR$ 형태로 나타내기
</aside>

<aside>

### ~~최소 제곱해~~

1. $~~A$의 열벡터의 직교 기저 구하기 $\{ u_1, u_2,\cdots \}$~~
2. $~~\hat b = proj_{u_1}b+proj_{u_2}b+\cdots~~$
3. $~~Ax = \hat b$ 를 만족하는 $x$ 구하기 ⇒ 최소제곱해~~

### 최적근사해

$A^TAx = A^Tb$ 를 만족하는 $x$ 계산

$\Longleftrightarrow \space x = (A^TA)^{-1}A^Tb$

**선형회귀에서 최적근사해**

$\hat \beta = (A^TA)^{-1}A^Tb$

**QR 분해를 이용한 최적근사해**

$\hat x = R^{-1}Q^Tb$  $(\Longleftrightarrow A\hat x=QR\hat x=b)$

</aside>

<aside>

### 닮음행렬

A,B가 닮음 행렬이면 $\Longrightarrow$

- $B=P^{-1}AP$를 만족하는 행렬 $P$가 존재.
- A의 고유값 = B의 고유값
- A 고유벡터 개수 = B 고유벡터 개수 (* 고유벡터는 다를 수 있음)
- $Rank(A) =Rank(B)$
- $det(A)=det(B)$
- $det(\lambda I_n - A) = det(\lambda I_n-B)$
- $tr(A) = tr(B)$

### 대각화

$D=P^{-1}AP \Longleftrightarrow A = PDP^{-1}$

⇒ $D$  : 행렬 A의 고유값

⇒ $P$ : 행렬 A의 고유벡터

- A가 대각화 가능 행렬이면 $\Longrightarrow$
    - n개의 서로 다른 고유값을 가진다. (단, 중근을 갖는다 해서 대각화 불가능한 건 아님.)
    - n개의 선형독립인 고유벡터를 갖는다. (고유값이 중근을 가지더라도 고유벡터만 n개이면 대각화 가능)
    - $A^{-1}$ 도 대각화 가능 ($A^{-1} = PD^{-1}P^{-1})$
- $A^n = PD^nP^{-1}$
</aside>

<aside>

### 직교대각화

: $A = PDP^{-1}=PDP^T$ $\Longleftrightarrow D = P^{-1}AP=P^TAP$

- 직교행렬 $P$ 는  $P^{-1} = P^T$ (P는 행렬 A의 같은 고유공간에 있는 고유벡터만 그람슈미트로 직교화한 것)
- 직교대각화 가능 행렬 A $\Longleftrightarrow$ 행렬 A는 대칭행렬이다.
- 직교대각화 가능 행렬 A $\Longleftrightarrow$ 행렬 A는 n개의 직교하는 고유벡터를 갖는다.
- 실대칭행렬 A $\Longleftrightarrow$ 고유값 모두 실수
</aside>
