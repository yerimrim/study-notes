- **탐색적 데이터 분석 : 예측에 도움될 피처를 추리고, 적절한 모델링 방법을 탐색하는 과정**
- **피처 엔지니어링 : 추려진 피처를 훈련에 적합하도록, 성능 향상에 도움되도록 가공하는 과정**

<aside>

### EDA

- EDA: 타깃값 변환 ⇒ 이상치 제거 ⇒ 파생피처추가 ⇒ 피처제거
- info( ) 함수로 결측값 개수와 데이터 타입 파악
- 머신러닝 모델은 숫자만 인식하므로 모델을 훈련할 때 피처 값을 문자로 바꾸면 안 됨
- 타깃값이 정규분포에 가깝지 않으면 ⇒ 로그변환 ⇒ 예측값 최종 출력 시 다시 지수변환

```python
# 정수로 요일 반환
print(datetime.strptime(train['date'][100], '%Y-%m-%d').weekday())
# 문자열로 요일 반환
print(calendar.day_name[datetime.strptime(train['date'][100], '%Y-%m-%d').weekday()])

## 시각화
mpl.rc('font', size=15) # 폰트 크기를 15로 설정
sns.displot(train['count']); # 분포도 출력
sns.displot(np.log(train['count'])); # 로그변환하여 분포도 출력

## 막대그래프 (범주형 데이터 시각화)
sns.barplot()

## 박스플롯(범주형 데이터에 따른 수치형 데이터 정보를 나타내는 그래프)
# 스텝 1 : m행 n열 Figure 준비
figure, axes = plt.subplots(nrows=2, ncols=2) # 2행 2열
plt.tight_layout()
figure.set_size_inches(10, 10)
# 스텝 2 : 서브플롯 할당
# 계절, 날씨, 공휴일, 근무일별 대여 수량 박스플롯
sns.boxplot(x='season', y='count', data=train, ax=axes[0, 0])
sns.boxplot(x='weather', y='count', data=train, ax=axes[0, 1])
sns.boxplot(x='holiday', y='count', data=train, ax=axes[1, 0])
sns.boxplot(x='workingday', y='count', data=train, ax=axes[1, 1])
# 스텝 3 : 세부 설정
# 3-1 서브플롯에 제목 달기
axes[0, 0].set(title='Box Plot On Count Across Season')
axes[0, 1].set(title='Box Plot On Count Across Weather')
axes[1, 0].set(title='Box Plot On Count Across Holiday')
axes[1, 1].set(title='Box Plot On Count Across Working Day')
# 3-2 x축 라벨 겹침 해결
axes[0, 1].tick_params(axis='x', labelrotation=10) # 10도 회전

## 포인트플롯 (범주형 데이터에 따른 수치형 데이터의 평균과 신뢰구간을 점과 선으로 표시)
# 한 화면에 여러 그래프를 겹쳐 그리기에 적합
# 스텝 1 : m행 n열 Figure 준비
mpl.rc('font', size=11)
figure, axes = plt.subplots(nrows=5) # 5행 1열
figure.set_size_inches(12, 18)
# 스텝 2 : 서브플롯 할당
# 근무일, 공휴일, 요일, 계절, 날씨에 따른 시간대별 평균 대여 수량 포인트플롯
sns.pointplot(x='hour', y='count', data=train, hue='workingday', ax=axes[0])
sns.pointplot(x='hour', y='count', data=train, hue='holiday', ax=axes[1])
sns.pointplot(x='hour', y='count', data=train, hue='weekday', ax=axes[2])
sns.pointplot(x='hour', y='count', data=train, hue='season', ax=axes[3])
sns.pointplot(x='hour', y='count', data=train, hue='weather', ax=axes[4]);

## 회귀선을 포함한 산점도 그래프 (수치형 데이터 간 상관관계를 파악하는 데 활용)
# 스텝 1 : m행 n열 Figure 준비
mpl.rc('font', size=15)
figure, axes = plt.subplots(nrows=2, ncols=2) # 2행 2열
plt.tight_layout()
figure.set_size_inches(7, 6)
# 스텝 2 : 서브플롯 할당
# 온도, 체감 온도, 풍속, 습도 별 대여 수량 산점도 그래프
sns.regplot(x='temp', y='count', data=train, ax=axes[0, 0],
scatter_kws={'alpha': 0.2}, line_kws={'color': 'blue'})
sns.regplot(x='atemp', y='count', data=train, ax=axes[0, 1],
scatter_kws={'alpha': 0.2}, line_kws={'color': 'blue'})
sns.regplot(x='windspeed', y='count', data=train, ax=axes[1, 0],
scatter_kws={'alpha': 0.2}, line_kws={'color': 'blue'})
sns.regplot(x='humidity', y='count', data=train, ax=axes[1, 1],
scatter_kws={'alpha': 0.2}, line_kws={'color': 'blue'});

## 히트맵 (데이터 간 상관관계를 색상으로 시각화하는 그래프, default:피어슨상관계수)
corrMat = train[['temp','atemp', 'humidity', 'windspeed', 'count']].corr()
fig, ax= plt.subplots()
fig.set_size_inches(10, 10)
sns.heatmap(corrMat, annot=True) # 상관관계 히트맵 그리기
ax.set(title='Heatmap of Numerical Data');

```

---

### 베이스라인 모델

데이터 임포트 ⇒ 피처엔지니어링 ⇒ 평가지표 계산 함수 ⇒ 모델 훈련 ⇒ 성능 검증

1. 피처엔지니어링
    1. 이상치 제거
    2. 훈련, 테스트 합치기
    3. 파생 피처 추가
    4. 피처 제거
    5. 훈련, 테스트 분할
        
        ```python
        ## 이상치 제거 ##
        train = train[train['weather'] != 4] # 훈련 데이터에서 weather가 4가 아닌 데이터만 추출
        
        ###################################
        ## 훈련, 테스트 합치기
        all_data = pd.concat([train, test], ignore_index=True)
        
        ###################################
        ## 파생피처 추가 ##
        from datetime import datetime
        # 날짜 피처 생성
        all_data['date'] = all_data['datetime'].apply(lambda x: x.split()[0])
        # 연도 피처 생성
        all_data['year'] = all_data['datetime'].apply(lambda x: x.split()[0].split('
        -
        ')[0])
        # 월 피처 생성
        all_data['month'] = all_data['datetime'].apply(lambda x: x.split()[0].split('
        -
        ')[1])
        # 시간 피처 생성
        all_data['hour'] = all_data['datetime'].apply(lambda x: x.split()[1].split(':')[0])
        # 요일 피처 생성
        all_data["weekday"] = all_data['date'].apply(lambda dateString :
        datetime.strptime(dateString,"%Y-%m-%d").weekday())
        ###################################
        ## 피처 제거 ##
        drop_features = ['casual', 'registered', 'datetime', 'date', 'windspeed', 'month']
        all_data = all_data.drop(drop_features, axis=1)
        ###################################
        ## 훈련 데이터와 테스트 데이터 나누기 ##
        X_train = all_data[pd.isnull(all_data['count'])]
        X_test = all_data[pd.isnull(all_data['count'])]
        # 타깃값 count 제거
        X_train = X_train.drop(['count'], axis=1)
        X_test = X_test.drop(['count'], axis=1)
        y = train['count'] # 타깃값
        ```
        
2. 평가지표 계산 함수
    
    ```python
    import numpy as np
    def rmsle(y_true, y_pred, convertExp=True):
    # 지수변환
    if convertExp:
    y_true = np.exp(y_true)
    y_pred = np.exp(y_pred)
    # 로그변환 후 결측값을 0으로 변환
    log_true = np.nan_to_num(np.log(y_true+1))
    log_pred = np.nan_to_num(np.log(y_pred+1))
    # RMSLE RM계산
    output = np.sqrt(np.mean((log_true - log_pred)**2))
    return output
    ```
    
3. 모델 훈련
    - 훈련: 피처(독립변수)와 타깃값(종속변수)이 주어질 때, 최적 가중치(회귀계수)를 찾는 과정
    
    ```python
    from sklearn.linear_model import LinearRegression
    linear_reg_model = LinearRegression() # 선형 회귀 모델 생성
    log_y = np.log(y) # 훈련 전 타깃값 로그변환
    linear_reg_model.fit(X_train, log_y) # 모델 훈련
    ```
    
4. 모델 성능 검증
    - 예측: 최적 가중치를 아는 상태(훈련된 모델)에서 새로운 독립변수(데이터)가 주어질 때, 타깃값을 추정하는 과정
    - 검증 데이터셋으로 예측
    
    ```python
    ## 훈련된 모델로 예측 수행 (검증 데이터 활용)
    preds = linear_reg_model.predict(X_train)
    ## 성능 평가
    print (f'선형회귀의 RMSLE 값 : {rmsle(log_y, preds, True):.4f}')
    ```
    
5. 예측 및 결과 제출
    - 테스트 셋으로 예측
    
    ```python
    linearreg_preds = linear_reg_model.predict(X_test) # 테스트 데이터로 예측
    submission['count'] = np.exp(linearreg_preds) # 지수변환
    submission.to_csv('submission.csv', index=False) # 파일로 저장
    ```
    

---

### 성능 개선

- 성능 개선: 피처엔지니어링, 하이퍼파라미터 최적화, 성능 검증을 반복
- 그리드 서치(하이퍼파라미터 최적화)
:• 하이퍼파라미터의 값을 바꿔가며 ‘모델’의 성능을 교차 검증으로 평가해 최적의 하이퍼파라미터를 찾음
⇒ 각 하이퍼파라미터를 적용한 모델마다 교차 검증하며 성능을 측정해 최종적으로 성능이 가장 좋았을 때의 하이퍼파라미터 값을 찾음(자동화)
    1. 모델 생성
    2. 그리드서치 객체 생성: 하이퍼파라미터 값 목록, 대상 모델, 교차 검증용 평가 함수가 필요함
    3. 그리드서치 수행
1. Ridge Regression: L2규제를 적용한 선형회귀 모델
    - L2 규제: 모델이 훈련 데이터에 overfitting되지 않도록 해줌
        
        ```python
        ## 1. 모델 생성 ##
        from sklearn.linear_model import Ridge
        from sklearn.model_selection import GridSearchCV
        from sklearn import metrics
        ridge_model = Ridge()
        ##################################
        ## 2.그리드서치 객체 생성 ##
        # 하이퍼파라미터 값 목록
        ridge_params =
        {'max_iter':[3000], 'alpha':[0.1, 1, 2, 3, 4, 10, 30, 100, 200, 300, 400, 800, 900, 1000]}
        # 교차 검증용 평가 함수(RMSLE 점수 계산)
        rmsle_scorer = metrics.make_scorer(rmsle, greater_is_better=False)
        # 그리드서치(with 릿지) 객체 생성
        gridsearch_ridge_model = GridSearchCV(estimator=ridge_model, # 릿지 모델
        param_grid=ridge_params, # 하이퍼파라미터 값 목록
        scoring=rmsle_scorer, # 평가지표
        cv=5) # 교차검증 분할 수
        ##################################
        ## 그리드서치 수행 ##
        log_y = np.log(y) # 타깃값 로그변환
        gridsearch_ridge_model.fit(X_train, log_y) # 훈련(그리드서치)
        print('최적 하이퍼파라미터 :', gridsearch_ridge_model.best_params_) # 최적 하이퍼파라미터 값 확인
        ```
        
2. Lasso Regression
    
    ```python
    ## 1. 모델 생성 ##
    from sklearn.linear_model import Lasso
    lasso_model = Lasso()
    ##################################
    ## 2.그리드서치 객체 생성 ##
    # 하이퍼파라미터 값 목록
    lasso_alpha
    = 1/np.array([0.1, 1, 2, 3, 4, 10, 30, 100, 200, 300, 400, 800, 900, 1000])
    lasso_params = {'max_iter':[3000], 'alpha':lasso_alpha}
    # 그리드서치(with 라쏘) 객체 생성
    gridsearch_lasso_model = GridSearchCV(estimator=lasso_model,
    param_grid=lasso_params,
    scoring=rmsle_scorer,
    cv=5)
    ##################################
    ## 3.그리드서치 수행 ##
    log_y = np.log(y)
    gridsearch_lasso_model.fit(X_train, log_y)
    ##################################
    ## 성능 검증 ##
    preds = gridsearch_lasso_model.best_estimator_.predict(X_train)
    print(f'라쏘 회귀 RMSLE 값 : {rmsle(log_y, preds, True):.4f}')
    ```
    
3. RandomForest
    
    ```python
    ## 1.모델 생성 ##
    from sklearn.ensemble import RandomForestRegressor
    randomforest_model = RandomForestRegressor()
    ##################################
    ## 2.그리드서치 객체 생성 ##
    rf_params = {'random_state':[42], 'n_estimators':[100, 120, 140]}
    gridsearch_random_forest_model = GridSearchCV(estimator=randomforest_model,
    param_grid=rf_params,
    scoring=rmsle_scorer,
    cv=5)
    ##################################
    ## 3.그리드서치 수행 ##
    log_y = np.log(y)
    gridsearch_random_forest_model.fit(X_train, log_y)
    print('최적 하이퍼파라미터 :', gridsearch_random_forest_model.best_params_)
    ##################################
    ## 성능 검증 ##
    preds = gridsearch_random_forest_model.best_estimator_.predict(X_train)
    print(f'랜덤 포레스트 회귀 RMSLE 값 : {rmsle(log_y, preds, True):.4f}')
    ```
    
</aside>
