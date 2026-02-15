### Chapter03 (Shallow)

- Regression: Fully connected, one output and real value
- `Shallow Neural Networks`: 비선형, 복잡한 데이터들을 잘 묘사할만큼 유연함, hidden layer 1개
- `Activation Function`: 비선형성을 줌(ex.ReLU)
- `Hidden Units`: 각 은닉층에 있는 뉴런(활성화 함수가 있는 노드) 개수
    - 많아질수록 직선의 꺾이는 부분이 많아짐
    - 너무 많으면 overfitting 위험
- `Hidden Layer`: 은닉층
    - Hidden Layer 1개 ⇒ Shallow Neural Networks
    - Hidden Layer 2개 이상 ⇒ Deep Neural Networks
    - 너무 깊으면 학습 불안정 위험
- `Universial approximation theorem`: 하나의 은닉층(hidden layer)만 있어도, 충분히 많은 뉴런(Hidden Unit)이 있다면 임의의 연속적인 함수를 임의의 정확도로 근사할 수 있다.
- 상수항(Y-offsets): Bias
- 기울기(Slopes): Weight
