<aside>

### 고유공간

- 고유공간은 영벡터를 포함한다.

### 고유값

- n차 정방행렬은 복소수 범위에서 n개의 고유값을 갖는다. (중복도까지 포함)
- 대칭행렬의 고유값은 모두 실수이다.
- 삼각행렬의 고유값 = 주대각 성분
- $A^n$ 의 고유값  $=\lambda^n$
- $A^{-1}$ 의 고유값  $={1 \over \lambda}$
- $A^T$ 의 고유값 $= \lambda$
- $det(A) = \lambda_i$ 의 곱,  $tr(A) =\lambda_i$ 의 합
- $A+cI_n$ 의 고유값 $=\lambda +c$

### 고유벡터

- 고유벡터: 정방행렬 A에 의한 변환 전과 변환 후가 ‘**평행**’한 벡터
- 서로 다른 고유값에 대해서는 고유벡터는 선형독립이다.
</aside>

<aside>

### 케일리-해밀턴 정리

$p(\lambda) = det(\lambda I_n - A) = \lambda^n + a_{n-1}\lambda^{n-1}+\cdots +a_1\lambda+a_n =0$

⇒  $p(A) = A^n + a_{n-1}A^{n-1}+\cdots +a_1A+a_nI=0$

⇒ $a_nI = (-A^n - a_{n-1}A^{n-1}-\cdots - a_1A) = A(A^{n-1} - a_{n-1}A^{n-2}-\cdots - a_1)$

⇒ $A^{-1} = {1\over a_n} (A^{n-1} - a_{n-1}A^{n-2}-\cdots - a_1)$

</aside>

<aside>

### 평균벡터와 공분산 행렬

- $m={1\over k}\sum x_i$   ⇒ 평균 벡터
- $C = {1\over k}\sum (x_i - m)(x_i-m)^T$    ⇒ 공분산 행렬 (열벡터 x 행벡터)
- $\hat x _i= \sum (x_i-m)^Tu_i$   ⇒ 차원 축소 해

### 주성분 분석 (차원 축소)

- $\hat x_i = (x_i-m)^Tu_i$
    - $x_i$: 문제에서 주어진 벡터들
    - $m$: 평균 벡터
    - $u_i$: 공분산 행렬 $C$의 고유벡터
</aside>

<aside>

### 직교행렬

- 직교 집합의 모든 벡터는 선형독립이다.

### 직교행렬의 성질

1. $U^TU=UU^T=I$
2. $U^T = U^{-1}$
3. $Ux\cdot Uy = x\cdot y$
4. $||Ux||=||x||$
5. 두 직교행렬의 곱은 직교행렬이다.
</aside>

<aside>

### 복소벡터공간

- $v\cdot w=w^*v=\bar w^Tv$
- $||v||=\sqrt{ v\cdot v}=\sqrt{v^*v}=\sqrt{\bar v^T v}$
- $v\cdot w = \bar w\bar \cdot \bar v $
- $ (v^*)^* = v $
- $ (\alpha A + \beta B)^* = \bar{\alpha} A^* + \bar{\beta} B^* $
- $ (AB)^* = B^* A^* $
  
</aside>
