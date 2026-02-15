### Chapter04 (Deep)

- Deep Neural Network: 은닉층이 2개 이상
- **Hyperparameter**: 학습 전에 직접 설정하는 값
    - `Hidden Layer` = Depth of network
    - `Hidden Unit` = Width of network
    - Learning Rate: 가중치 업데이트 크기
    - Batch Size: 한 번에 학습할 샘플 수
- **Parameter**: 학습 과정에서 데이터로부터 학습해 얻는 값
    - Weight
    - Bias
- Shallow vs Deep
    1. Ability to Approximate Different Functions
    ⇒ Universal Approximation Theorem에 의해 두 방법 모두 모든 연속함수로 근사 가능
    2. Number of Linear Regions per Parameter
    ⇒ Shallow: 조각 선형 영역 수 제한적
    ⇒ Deep: 더 많은 선형 영역 생성 가능, 각 영역이 서로 의존적이며 그 관계는 아직 불명확
    3. Depth efficiency
    ⇒ Shallow: 매우 많은 Hidden Units 필요 → 효율⬇️
    ⇒ Deep: 적은 Hidden Units 필요 → 효율 ⬆️
    4. Fitting and Generalization
    ⇒ Shallow: 학습 빠름, 일반화 성능 낮음
    ⇒ Deep: 학습 느림, 일반화 성능 좋음
