<aside>
💡

### Decision Trees (의사결정 트리)

1. **분류 속성 선택 (Training Set 사용)**
    1. 정보 이득율 (높은 것 선택)
        - 정보 엔트로피 (Information Entropy) (작을수록 순도가 높음)
        $\mathrm{Ent(D)} =-\sum_{k=1}^{|Y|} p_klog_2p_k$
        - 정보 이득 (Information Gain)
        $\mathrm{Gain(D,a)=Ent(D)}-\sum_{v=1}^V\dfrac{|D^v|}{|D|}\mathrm{Ent(D^v)}$
        - 정보 이득율 (Gain Ratio)
        **$\mathrm{Gain \space ratio  (D,a)=\dfrac{Gain(D,a)}{IV(a)}}$**
            
             **$\mathrm{IV(a)}=-\sum_{v=1}^{V}\dfrac{|D^v|}{|D|}log_2\dfrac{|D^v|}{|D|}$**
            
        
    2. 지니 계수 (낮은 것 선택, 작을수록 순도가 높음)
        - $\mathrm{Gini(D^v)}=\sum_{k=1}^{|Y|}\sum_{k'\not=k}p_kp_{k'}=1-\sum_{k=1}^{|Y|}p_k^2$
        - $\mathrm{Gini}\space \mathrm{index(D,a)} = \sum_{v=1}^V \dfrac{|D^v|}{|D|}\mathrm{Gini}(D^v)$

1. **가지치기 (Pruning) (Validation Set 사용)**
    1. 사전 가지치기 (Pre-pruning)
        - 위에서부터 성능 평가
    2. 사후 가지치기 (Post-pruning)
        - 밑에서부터 성능 평가
</aside>

<aside>
💡

### SVM (서포트 벡터 머신)

- Margin: $\dfrac{|w^Tx+b|}{||w||}$     , when 초평면 $w^Tx+b=0$

1. 선형 분리 가능(Hard Margin SVM) ⇒ 오류 허용 x
    - $w^Tx_i+b\geq \delta$      $if \space y_i=1$
    - $w^Tx_i+b\leq -\delta$      $if \space y_i=-1$
    
    - $w^T_{new}x_i + b_{new} \geq 1$       $if \space y_i=1$
    - $w^T_{new}x_i + b_{new} \leq 1$       $if \space y_i=-1$
    
    - 최적화: $min_{w,b} \space \dfrac{1}{2} ||w||^2$    $s.t.\space \space y_i(w^Tx_i+b)\geq 1$

1. 선형 분리 불가능(Soft Margin SVM) ⇒ 약간의 오류 허용 o
    - 최적화: $min_{w,b} \space \dfrac{1}{2} ||w||^2 + C\sum_{i=1}^n l_{0,1}(y_i(w^Tx_i+b)-1)$
    
2. 커널 서포트 벡터 머신 
</aside>
