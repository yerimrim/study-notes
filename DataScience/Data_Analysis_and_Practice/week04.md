### 데이터

- 수치형 데이터 (사칙연산 가능)
    - 연속형: 실수
    - 이산형: 정수
- 범주형 데이터 (사칙연산 불가능)
    - 순서형: 순위 o
    - 명목형: 순위 x

---

### EDA

- EDA: 데이터분석 전, 그래프나 통계적인 방법으로 자료를 **직관적**으로 바라보는 과정
    1. 분석의 목적과 변수가 무엇이 있는지 확인. 개별 변수의 이름이나 설명을 가지는지 확인
    2. 데이터를 전체적으로 살펴보기 : 데이터에 문제가 없는지 확인. head나 tail부분을 확인, 추가적으로 다양한 탐색(이상치, 결측치 등을 확인하는 과정)
    3. 데이터의 개별 속성값을 관찰 : 각 속성 값이 예측한 범위와 분포를 갖는지 확인. 만약 그렇지 않다면, 이유가 무엇인지를 확인.
    4. 속성 간의 관계에 초점을 맞추어, 개별 속성 관찰에서 찾아내지 못했던 패턴을 발견 (상관관계, 시각화 등)
- 이상치 찾아내는 방법
    1. 개별 데이터 관찰: 눈으로 훑어보면서 추세 살피기, 무작위 추출 등
    2. 통계 값 활용: 적절한 요약 통계 지표 (평균, 중앙값, 최빈값, 범위, 분산)
    3. 시각화 활용: 그래프 그리기!
    4. 머신러닝 기법 활용: k-means등 클러스터링 기법으로 outlier 판별

### 시각화

- **수치형 데이터 시각화**
    - 히스토그램
        - 수치형 데이터의 구간별 빈도수를 나타내는 그래프.
        - sns.histplot(data=titanic, x=’age’)
    - 커널밀도추정
        - 히스토그램을 매끄럽게 곡선으로 연결한 그래프. 수치형 데이터의 구간별 빈도수를 나타내는 그래프
        - sns.kdeplot(data=titanic, x=’age’)
    - 분포도
        - 수치형 데이터 하나의 분포를 나타내는 그래프
        - sns.displot(data=titanic, x=’age’, kde=True)
    - 러그플롯
        - 주변 분포(marginal distribution)를 나타내는 그래프
        단독으로 사용하기보다는 주로 다른 분포도 그래프와 함께 사용
        - sns.rugplot(data=titanic, x=’age’)
- **범주형 데이터 시각화**
    - 막대그래프
        - 범주형 데이터 값에 따라 수치형 데이터 값이 어떻게 달라지는지 파악할 때 사용
        - sns.barplot(x=’class’, y=’fare’, data=titanic)
    - 포인트플롯
        - 막대 그래프와 같이 범주형 데이터에 따른 수치형 데이터의 평균과 신뢰구간을 나타낸다. 단, 그래프를 점과 선으로 나타낸다.
        - sns.pointplot(x='class', y='fare', data=titanic)
    - 박스플롯
        - 최댓값, 최솟값, 사분위 수 제공
        - 막대그래프와 포인트플롯보다 더 많은 정보 제공
        - sns.boxplot(x='class', y='age', data=titanic)
    - 바이올린플롯
        - 박스플롯 + 특정 구간에 데이터가 얼마나 분포해 있는지도 확인 가능
        - sns.violinplot(x='class', y='age', data=titanic)
    - 카운트플롯
        - 범주형 데이터의 개수를 확인할 때 사용하는 그래프. 
        주로 범주형 피처나 범주형 타깃값의 분포가 어떤지 파악하는 용도로 사용
        - sns.countplot(x='class', data=titanic)
    - 파이 그래프
        - 범주형 데이터별 비율을 알아볼 때 사용하기 좋은 그래프
        - plt.pie(x=x, labels=labels, autopct='%.1f%%')
- **데이터 관계 시각화**
    - 히트맵
        - 히트맵은 데이터 간 관계를 색상으로 표현한 그래프다. 
        비교해야 할 데이터가 많을 때 주로 사용
        - sns.heatmap(data=flights_pivot)
    - 라인플롯
        - 두 수치형 데이터 사이의 관계를 나타낼 때 사용.
        기본적으로는 x 파라미터에 전달한 값에 따라 y 파라미터에 전달한 값의 평균과 95% 신뢰구간을 나타냄.
        - sns.lineplot(x='year', y='passengers', data=flights)
    - 산점도
        - 두 데이터의 관계를 점으로 표현하는 그래프
        - sns.scatterplot(x='total_bill', y='tip', data=tips)
    - 산점도+회귀선
        - 산점도와 선형 회귀선을 동시에 그려주는 함수
        전반적인 상관관계 파악이 쉽다.
        - sns.regplot(x='total_bill', y='tip', data=tips)

- 시각화
    - Non-graphical Analysis
        - df.info(), df.describe(), df.isnull()
    - Univariate Analysis
        - df[column].plot(kind=’hist’) ⇒ Numerical
        - df[column].plot(kind=’bar’) ⇒ Categorical
    - Multivariate Analysis
        - sns.pairplot(), sns.heatmat() ⇒ Numerical vs Numerical
        - sns.countplot(hue=…) ⇒ Categorical vs Categorical
        - sns.boxplot(), sns.paitplot(hue=…) ⇒ Numerical vs Categorical

---

- Data Engineers: 수집, 정제
- Data Analysts: 정제, EDA
- Machine Learning Engineers: 모델링, 배포
- Data Scientists: 전체 다 관여
