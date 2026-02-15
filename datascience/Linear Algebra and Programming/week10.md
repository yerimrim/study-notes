<aside>

### 내적공간

1. $^ \forall v \in V, \space <v,v> \space \geq 0 \space,moreover<v,v>=0\Leftrightarrow\space v=0$ 
2. $^\forall v,w \in V , \space <v,w>=<w,v>$
3. $^\forall v,w,u\in V, \space ^\forall \alpha,\beta \in\mathbb{R}, \space <\alpha v+\beta w, \space u> = \alpha<v,u>+\beta <w,u>$
</aside>

<aside>

### NORM

$||v|| = \sqrt{<v,v>}$

### NORM 공간

1. $^\forall v \in V,\space  ||v|| \geq 0,\space  moreover \space ||v||=0\Leftrightarrow v= 0$
2. $^\forall v \in V ^\forall \alpha \in\mathbb{R},\space  ||\alpha v|| = ||\alpha ||||v||$
3. $^\forall u, v \in V, ||u+v|| \le ||u|| +||v||$
</aside>

<aside>

### 외적

$$u \times v = \begin{vmatrix} i & j& k \\ u_1&u_2&u_3\\ v_1&v_2&v_3 \end{vmatrix}$$

### $\mathbb{R}^3$ 공간 벡터의 표준기저에 대한 외적의 성질

1. $i\times i = j\times j = k\times k = 0$
2. $i\times j = k,\space  j\times k = i ,\space k\times i = j$
3. $i\times k = -j,\space j\times i = -k,\space k\times j = -i$

### $\mathbb{R}^3$ 공간 벡터의 외적의 성질

1. $u\times v = -v\times u$
2. $u \times (v+w) = (u\times v) + (u\times w)$
3. $(u+v)\times w = (u\times w) + (v\times w)$
4. $c(u\times v) = (cu) \times v = u\times (cv)$
5. $u \times 0 = 0 \times u=0$
6. $u\times u = 0$
</aside>

<aside>

### $\mathbb{R}^3$ 공간의 직선

$a$ : 지나는 점

$b$ : 평행한 벡터

⇒  $p = a + bt$

### $\mathbb{R}^3$ 공간에서 벡터의 방향각

$cos\alpha = {v_x\over ||v||}$

$cos\beta = {v_y\over ||v||}$

$cos\gamma = {v_z\over ||v||}$

⇒ $cos^2\alpha + cos^2 \beta + cos^2 \gamma = 1$ (검산용)

### $\mathbb{R}^3$ 공간에서 평면의 방적식

$w$  : 법선벡터

$p = (x,y,z)$

$a$ : 지나는 점

⇒ $w \cdot (p-a) = 0$

### $\mathbb{R}^3$ 공간에서 평면과 점 사이의 거리

$d = {\mid(p-a)\cdot w \mid \over \Vert w \Vert }$

</aside>

<aside>

### 다변수 함수의 그래디언트

$\bigtriangledown f = {\partial f\over \partial x} = ({\partial f\over \partial x_1}, {\partial f\over \partial x_2},{\partial f\over \partial x_3}, \dots)$

### 벡터함수의 스칼라 미분

$\bigtriangledown F = {\partial f\over \partial x_i} = [{\partial f_1\over \partial x_i}, {\partial f_2\over \partial x_i},{\partial f_3\over \partial x_i}, \dots ]$ 

### 야코비안 행렬

$$J_f= {\partial F\over \partial x} = \begin{pmatrix} {\partial f_1\over \partial x_1} & {\partial f_2\over \partial x_1} \dots {\partial f_n\over \partial x_1} \\\\ {\partial f_2\over \partial x_2} & {\partial f_2 \over \partial x_2} \dots {\partial f_n \over \partial x_2} \\ \vdots  & \vdots\end{pmatrix}$$

### 헤시안 행렬

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a3770338-9706-4edc-a979-958163ea1fa2/0e2bf670-59c0-4625-bad0-66552dc6f5ee/image.png)

### 라플라시안

$\bigtriangledown^2f = {\partial^2f \over \partial x_1^2} + {\partial ^2 f\over \partial x_2^2 } + \dots {\partial^2f\over \partial x_n^2}$

### 행렬 미분

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a3770338-9706-4edc-a979-958163ea1fa2/a2c240d6-c94e-468b-a4e0-79e0fc40c92b/image.png)

 

### 행렬의 스칼라 미분

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a3770338-9706-4edc-a979-958163ea1fa2/a401e473-9365-4fe7-bc5f-15855d490872/image.png)

### 편미분

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a3770338-9706-4edc-a979-958163ea1fa2/4e37388a-495c-45c0-a74b-415b2c42ecf2/image.png)

</aside>

<aside>

### 선형변환

아래 조건을 모두 만족해야 함

1. $L(u+v) = L(u)+L(v)$
2. $L(ku) = kL(u)$

- 행렬에 벡터를 곱하는 것 =  $\mathbb{R}^n \longrightarrow \mathbb{R}^m$ 으로의 선형변환

### 반사변환

- x축 기준으로 반사: $$\begin{pmatrix} 1 & 0\\0&-1\end{pmatrix}$$
- y축 기준으로 반사:  $$\begin{pmatrix} -1 & 0\\0&1\end{pmatrix}$$

### 층밀림변환

- x축 방향으로 y의 k배만큼 층밀림: $$\begin{pmatrix} 1 & k\\0&1\end{pmatrix}$$
- y축 방향으로 x의 k배만큼 층밀림: $$\begin{pmatrix} 1 & 0\\k&1\end{pmatrix}$$
</aside>

<aside>

### 선형변환의 합성

아래 조건을 모두 만족할 시 선형변환임

1. $L_2\circ L_1(u+v) = L_2\circ L_1(u) + L_2\circ L_1 (v)$
2. $L_2 \circ L_1(cu) = c\space L_2 \circ L_1(u)$

### 역변환

$L_1^{-1} = L_2, \space L_1 = L_2^{-1} \Longleftrightarrow L_2\circ L_1 = L_1\circ L_2 = I_n$

</aside>

<aside>

- $L:V\longrightarrow W, \space V=W$  ⇒ **선형연산자**  $i.e. \space L:V\longrightarrow V$
- $L: V\longrightarrow V, \space ^\forall u,v \in V, \space\space L(u)\cdot L(v) = u\cdot v$ ⇒ **직교연산자**
- 직교연산자 L의 행렬 A의 모든 열벡터는 정규직교벡터 $\Longleftrightarrow$ $A^TA = I_n$
</aside>

<aside>

- 벡터 b가 행렬 A의 열공간에 존재 $\Longleftrightarrow$ $A^{-1}$ 존재
- nullity(A) = n - Rank(A)  ← n = 열 개수, nullity(A) = 퇴화차수, 영공간 기저의 개수
- 행동치인 행렬은 서로 동일한 영공간을 갖는다.
- 퇴화차수가 0인 행렬이 모든 열벡터는 선형독립 (정방행렬 아닐 수도 있음)
    
    nullity(A) = 0 $\Longleftrightarrow$  n - Rank(A) = 0 $\Longleftrightarrow$  모든 성분이 0인 행 존재 x $\Longleftrightarrow$ 모든 열벡터 선형독립
    
- 퇴화차수가 0인 **정방행렬**은 역행렬을 갖는다.
</aside>
