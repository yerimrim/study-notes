### Chapter05 (Loss)

- `Loss function`: 실제값과 예측값 사이의 오차를 계산하는 함수
- **Maximum Likelihood**: **argmax$( \sum P[y_i|f(x_i,\phi)])$**
- **Maximum Log Likelihood**: **argmax$( \sum log(P[y_i|f(x_i,\phi)]))$**
- **Mimimum Negative Log Likelihood**: **argmin$(- \sum log(P[y_i|f(x_i,\phi)]))$**
- `Heteroscedastic Regression`(이종분산회귀): 입력값에 따라 분산이 달라짐을 모델링 (Regression에서 쓰임)
- `Softmax 함수`: k개의 실수 출력을 확률값으로 변환해주는 함수 (Multicalss Classification에서 쓰임)
- `Cross-Entropy`: 두 확률분포의 차이를 측정하는 지표 (Classification에서 쓰임)
- `Least squares loss function(MSE)`: $L(\phi)=\sum(f[x_i,\phi]-y_i)^2$
⇒ 이를 이용해 Loss를 최소화하는 파라미터를 찾음
- 문제상황과 적절한 손실함수
    - 출력=연속값 1개 - `Univariate Regression`
        - MSE: $L(\phi)=(f[x_i,\phi]-y)^2$
    - 출력=연속값 여러 개 - `Multivariate Regression`
        - MSE의 합: $L(\phi)=∑_{i=1}^I∑_{d=1}^{D_o}​(f_d​[x_i​,ϕ]−y_{id}​)^2$
    - 출력=1개 클래스 - `Binary Classification`
        - Binary Cross-Entropy: $L(\phi)=\sum^I_{i=1}-(1-y_i)log(1-sig[f(x_i|\phi)])-y_ilog(sig[f(x_i|\phi)])$
    - 출력=2개 이상 클래스 - `Multiclass Classification`
        - Multiclass Cross-Entropy: $-\sum_{i=1}^{D_o} p_i\space log[\hat y_i]$
        - $\hat y​_i​= {softmax}(f_i​[x,ϕ])={exp(f_i[x,\phi])\over \sum_{k=1}^{D_o}exp(f_k[x,\phi])}$
