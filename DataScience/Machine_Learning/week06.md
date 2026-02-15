### 실습

```python
# 행 생성
new_person = pd.Series(['Molly Mooney', 40, 1], index=['Name','Age','Driver'])
# 데이터프레임 형식으로 변환
.to_frame()
# 전치
.T

# append 대신 데이터 추가
## concat ##
dataframe = pd.concat([dataframe, new_person.to_frame().T], ignore_index=True)

## loc ##
dataframe.loc[len(dataframe)]=["aa",50, 0]

# 수치형 데이터에 대해서만 공분산, 상관계수 계산
.cov(numeric=True)
.corr(numeric=True)

# 고유한 값
dataframe['Age'].unique()
# 고유한 값의 개수
dataframe['Age'].nunique()

# 고유값, 고유벡터 추출
eigenvalues, eigenvectors = np.linalg.eig(A)

# SVD
U, S, V = np.linalg.svd(grayscale_cat_as_matrix, full_matrices=True)
```
