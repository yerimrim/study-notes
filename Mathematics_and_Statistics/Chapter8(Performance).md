### Chapter8 (Performance)

- Training Error (⬆️ ⇒ 복잡도 증가, Epoch 증가, Learning rate 적절히 조절해야 함)
- Validation Error (⬆️ ⇒ 모델 일반화)
- Test Error (Validation Error을 낮추면 자연스럽게 낮아짐)
    1. `Noise Error`: 데이터 자체의 noise로 인해 발생 ⇒ 줄일 수 없음
    2. `Bias Error`: 모델 단순성 문제, **Underfitting**
    3. `Variance Error`: 모델 복잡성 문제, **Overfitting**
- **Bias Error 줄이는 방법**: 파라미터 개수 늘리기, 복잡한 모델 사용
- **Variance Error 줄이는 방법**: 학습 데이터 개수 늘리기, 단순한 모델 사용
- Bias-Variance Trade off: 학습 데이터 개수가 고정일 때, 
파라미터가 증가하면 ⇒ bias는 감소하지만, variance는 증가
- Double Descent(이중하강): 
모델 복잡도가 증가하면 Test Error가 처음에는 감소
데이터를 완전히 암기하는 지점에서는 Test Error 급증+ 더 복잡해지면 Test Error 다시 감소하는 현상
