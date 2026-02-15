### Decision Tree

- **분류 속성 선택 (Training Set 사용)**
    1. **정보 이득율 (높은 것 선택)**
        - 정보 엔트로피 (Information Entropy) (작을수록 순도가 높음)
        $\mathrm{Ent(D)} =-\sum_{k=1}^{|Y|} p_klog_2p_k$
        - 정보 이득 (Information Gain)
        $\mathrm{Gain(D,a)=Ent(D)}-\sum_{v=1}^V\dfrac{|D^v|}{|D|}\mathrm{Ent(D^v)}$
    2. **지니 계수 (낮은 것 선택, 작을수록 순도가 높음)**
        - $\mathrm{Gini(D^v)}=1-\sum_{k=1}^{|Y|}p_k^2$
        - $\mathrm{Gini}\space \mathrm{index(D,a)} = \sum_{v=1}^V \dfrac{|D^v|}{|D|} \cdot \mathrm{Gini}(D^v)$
