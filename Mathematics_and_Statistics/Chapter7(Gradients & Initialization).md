### Chapter7 (Gradients & Initialization)

- `Backpropagation`: 모든 가중치에 대한 Gradient를 효율적으로 계산하기 위해 사용하는 알고리즘
    - 장점: 매우 효율적
    - 단점: 메모리 많이 사용, 순차적 계산
- `Initialization:` 학습 전 bias, weight 설정 (적절한 초기화를 통한 빠르고 안정적인 수렴이 필요)
    - bias는 일반적으로 0으로 초기화
    - weight는 특정 분포 안에서 랜덤 추출
        - **He initialization**: 각 레이어의 hidden units 수에 맞춰 가중치 분산 $\sigma^2$을 결정
            - Forward Pass: $\sigma^2={2\over D_h}$
            - Backward Pass: $\sigma^2={2\over D_{h'}}$
            - Both Pass: $\sigma^2={4\over D_h+D_{h'}}$
            - $D_h$: 현재 레이어의 hidden units 개수
            - $D_{h'}$: 다음 레이어의 hidden units 개수
