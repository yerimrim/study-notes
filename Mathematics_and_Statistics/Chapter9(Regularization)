### Chapter9 (Regularization)

- `Generalization Gap(Generalization error)`: **Training error과 Validation error 사이의 Gap** = **Variance error**
- **Variance error을 줄이는 방법**(=Generalization Gap 줄이는 방법)
    1. `Regularization`
        1. Explicit Regularization: 손실함수에 파라미터에 대한 제약 항을 추가해 일반화
            - L2 Regularization(Ridge): 가중치가 너무 커지지 않도록 제어
            ⇒ $\hat L=L+\lambda \sum w_i^2$
               (decay 효과)
            ⇒ L2 Regularization $\neq$ Weight decay
            ⇒  GD + L2 Regularization $=$ GD + Weight decay
        2. Implicit Regularization: 항 추가 x, 학습구조나 과정에서 자연스럽게 일반화
    2. `Early Stopping`: Validation Error가 증가하기 전에 훈련 중단 ⇒ overfitting 방지
    3. `Ensemble`: 여러 모델 평균 ⇒ overfitting 완화
        1. bagging: 서로 다른 데이터 subset 사용
    4. `Dropout`: 일부 뉴런을 랜덤으로 제거 ⇒ overfitting 방지
    5. `Adding Noise`: 학습 데이터에 noise 추가 ⇒ 모델 강건화
    6. `Data Augmentation`: 데이터를 변형시켜 학습 데이터 개수를 늘림 ⇒ overfitting 방지
