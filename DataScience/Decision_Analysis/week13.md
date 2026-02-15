### KNN

- Distance Formula ($x_i$: what i want to classify, $y_i$: given data, $i$: feature)
    - Euclidean: $\sqrt{(x_1-y_1)^2+(x_2-y_2)^2+\cdots}$
    - Manhattan: $\sum|x_i-y_i|$
    - Minkowski: $(\sum|x_i-y_i|^{p})^{1\over p}$          p=1 → Manhattan, p=2 → Euclidean
    - Cosine: $1-{\sum x_iy_i \over \sqrt{\sum x_i^2}\sqrt{\sum y_i^2}}$
    - Hamming: $\sum|x_i-y_i|$   ( $x_i=y_i$ → 0,  $x_i \not= y_i$ → 1 )
- Rank (sorted from smaller value to bigger value)
    - The class of the new data ⇒ choose the majority value in k=n
