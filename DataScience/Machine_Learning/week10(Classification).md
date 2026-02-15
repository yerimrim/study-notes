### 베이지안 결정 이론 (Bayesian Decision Theory)

- 베이즈 결정 규칙 (Bayes Decision Rule):  
`$R(c_i|x)=1-P(c_i|x)$ 를 최소화하는 클래스 레이블 선택` 
⇒ `사후확률 $P(c_i|x)$를 최대화하는 클래스 레이블 선택`
- 베이즈 정리 (Bayes Theorem)
$P(A|B)={P(A)P(B|A)\over P(B)}$
$P(c|x)={P(c)P(x|c)\over P(x)}$
- MLE (가정한 확률분포와 실제 데이터 분포 간의 일치성에 과하게 의존) ⇒ 나이브 베이즈 분류기 (확률분포 가정x, 데이터에만 의존) 2
