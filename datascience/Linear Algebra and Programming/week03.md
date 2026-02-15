<aside>

### <행렬의 거듭제곱> (정방행렬만)

$$
A^0 = I \\ (A^b)^c = A^{bc} \\ A^bA^c = A^{b+c}
$$

</aside>

<aside>

### <행렬 연산의 기본성질 (o,x 문제 출제)>

1. $A + 0 = 0 + A$
2. $IA = AI = A$
3. $A + B = B + A$
4. $(A + B) + C = A + (B + C)$
5. $(AB)C = A(BC)$
6. $A(B + C) = AB + AC, \space (A + B)C = AC + BC$
7. $a(B + C) = aB + aC, \space (a+b)C = aC + bC$
8. $(ab)C = a(bC)$
9. $a(BC) = (aB)C = B(aC)$
</aside>

<aside>

### <행렬 합과 차의 거듭제곱>

* In general, $AB\neq BA$

$$
(A+B)^2 = (A+B)(A+B) \\ = A^2+AB+BA+B^2 \\ \neq A^2+2AB+B^2
$$

$$
(A-B)^2 = (A-B)(A-B) \\ =A^2-AB-BA+B^2 \\ \neq A^2-2AB+B^2
$$

</aside>

<aside>

### <역행렬의 성질>

$$
(A^{-1})^{-1}=A \\ (AB)^{-1} = B^{-1}A^{-1} \\ (kA)^{-1}=\frac1kA^{-1} \\ (A^{-1})^k=(A^k)^{-1} \space (k\geq0,\space k\in Z) \\ AA^{-1}=A^{-1}A=I_n \\  
$$

### * 모든 원소가 0인 행 또는 열이 존재 ⇒ 비가역 ⇒ 역행렬 존재 x

</aside>

<aside>

### <Thm>

**Thm) 역행렬은 유일하다.**

- Answer
    
    (O)
    
    **pf)** $Assume \space that \space B,C \space are \space inverse\space of\space A.$
    
    $Then,\space AB=BA=I_n,\space AC=CA=I_n.$
    
    $B=BI_n=B(AC)=(BA)C=I_nC=C.$
    
    $Therefore,\space the\space inverse\space of\space A\space is\space unique.$
    

____________________________________________________________________________

**Thm) 행렬 A,B,C에 대해 AB=AC 라고 해서, 반드시 B=C 는 아니다. ( $\because$ A must be invertible.)**

→ A의 역행렬이 존재할 때, AB=0이면, B=0이다?

- Answer
    
    (O)
    

→ A의 역행렬이 존재할 때, AB=0이면, A=0이다?

- Answer
    
    (X) 
    
    (전제와 결과가 모순 ; A=0이면 A의 역행렬 존재 x)
    
    (B의 역행렬이 존재한다고 가정해야 명제가 성립함.)
    

→ A,B의 역행렬이 존재할 때, AB=0이면, A=0 또는 B=0이다?

- Answer
    
    (X)
    
    (전제와 결과가 모순 ; A=0, B=0이면 A,B의 역행렬은 존재하지 않음.)
    

____________________________________________________________________________

**Thm) AB = 0 일때, 일반적으로 A=0 또는 B=0 이라고 할 수 있다?**

- Answer
    
    (X)
    
     ( $\because A \neq 0, B\neq 0$ 인 경우도 존재)
    

→ 대각행렬 A,B에 대하여 AB = 0 일때, 일반적으로 A=0 또는 B=0 이라고 할 수 있다?

- Answer
    
    (X)
    
    ( $\because A \neq 0, B\neq 0$ 인 경우도 존재)
    
</aside>
