### Chapter10 (Convolutional)

- Fully-Connected Network의 문제점
    1. 크기 문제: 입력이 커지면 파라미터 수가 급격히 증가
    2. 지역적 상관 무시: 인접 픽셀끼리는 통계적으로 관련이 있으나, 이를 무시하고 모두 연결함 → 공간 정보 비효율적 활용
    3. 변형 불안정: 입력이 조금만 바뀌어도 다시 학습해야 함 → 일반화 어려움
- Invariance(불변성): 입력에 변형이 있어도 출력값이 항상 같음
- Equivariance(등가성): 입력이 변하면 출력도 변함

- `Convolutional Network`: 모든 뉴런을 연결하지 않고, 필터 공유 + 지역적으로 연결
- `Zero padding`: 양쪽 끝에 0 추가 ⇒ 차원 유지됨
- `Valid`: 0 추가 x ⇒ 차원 축소됨
- `Size`: 필터 개수
- `Stride`: 이동 간격(점프 개수)
- `Dilation`: 커널 사이 공백

- 합성곱 파마리터 수 계산 ⭐️
    - **Weight = 입력 채널 수 $\times$ 출력 채널 수 $\times$ 커널 높이 $\times$ 커널 너비 
                   = 입력 채널 수 $\times$ 출력 채널 수 $\times$ 커널 size**
    - **Bias = 출력 채널 수**
- **Receptive Field(수용장)⭐️
: 한 유닛에 영향을 미치는 입력 데이터의 영역 크기 (Layer가 깊어질수록 영향력이 커져 더 넓은 범위의 정보를 파악 가능)**
    - **$R_L​=R_{L−1}​+(kernel_L​−1)×stride ^{(누적)}_{L−1​}×dilation_{L−1}​$**
- **Downsampling**: 차원 축소
    - sample every other position: 모두 동일한 위치의 값
    - Max pooling: 각 구역별 max값
    - Mean pooling: 각 구역별 mean값
- **Upsampling**: 차원 확대
    - Duplicate: 복제
    - Max-upsampling: max pooling 한 값을 원래 위치에 놓고, 나머지는 0으로 채움
    - Bilinear interpolation: 빈 노드를 smooth해지도록 채워넣음
    - Transposed convolutions: 합성곱을 역으로 적용해 출력 크기를 늘림, 나머지는 0으로 채움
