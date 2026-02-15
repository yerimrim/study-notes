```jsx
[딥러닝 준비사항]
- 데이터 (딥러닝은 데이터를 기반으로 예측 또는 판별을 수행)
- 컴퓨터 (일반 CPU or 특화된 GPU)
- 플랫폼 (파이썬, 텐서플로우 등)
- 프로그램 (프로그래밍)

딥러닝 코드
model = Sequential()
model.add(Dense(30, input_dim=17, acitivation = 'relu'))
model.add(Dense(1, activation='sigmoid')
model.compile(loss='binary_crossentropy', optimizer='adam', netrics=['accuracy'])
model.fit(X,Y, epochs=100, batch_size=10)
```
