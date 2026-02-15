### Chapter6 (Fitting)

- **Non-Covex**: local minimum과 saddle point가 많은 상황 ⇒ Gradient Descent로 global minimum을 찾을 수 없음
- Hessian Maxtrix: 2차 편미분 정사각행렬 ⇒ $n$개의 파라미터를 가진 모델 $H=n^2$
- **Epoch**: 전체 학습 데이터를 한 번 사용해 학습을 완료한 상태
- **Mini-Batch**: 전체 데이터셋의 subset
- `Gradient Descent(GD)`: 손실(loss)을 줄이는 방향으로 조금씩 이동하면서 최적의 파라미터를 찾는 방법
$w_{new}=w_{old}-\eta {\partial L\over \partial w}$
- `Stochastic Gradient Descent(SGD)`: 노이즈 추가 + 일부 데이터에 대해서만 GD 실행
    - 노이즈 추가 ⇒ local minimum, saddle point 탈출 + 탐색범위를 확대
    - 일부 데이터에 대해서만 GD 실행 ⇒ 계산량 ⬇️
    - 경사 흔들림 ⇒ 안정적 수렴을 위해 Learning Rate 점진적 감소 필요
    - 일반화 성능 향상
- `Momentum`: 이전 업데이트를 일정 비율 누적
    - $m_{t+1}\leftarrow \beta\cdot m_t +(1-\beta)\sum_{i\in B_t}{\partial ℓ_i[\phi_t]\over \partial \phi}\\ \phi_{t+1} \leftarrow \phi_t -\alpha \cdot m_{t+1}$
    - local minimum, saddle point 탈출 가능
    - 경사가 작아도 속도 유지
    - 진동을 줄이고 빠른 수렴
- `Adam`: Momentum + Adaptive Learning rate
    - 속도, 안정성 모두 좋음
- `Normalized Gradient`: Gradient 크기를 1로 정규화, 방향만 고려
    - 불안정한 업데이트 방지
