<aside>
💡

### 활성화 함수

- Hidden Layer ⇒ 필수 (시그모이드 함수)
- Output Layer ⇒ 선택 (회귀-항등함수, 분류-Sigmoid 함수)

- $\mathrm {Sigmoid(x) = \dfrac{1}{1+e^{-x}} = \dfrac{1}{1+e^{-(w_1x_1+w_2x_2+\cdots)}} }$
</aside>

<aside>
💡

### 순전파

- Input = x_1, Function = w_1 ⇒ Output = x_1w_1
</aside>

<aside>
💡

### 역전파

- 덧셈 노드: 이전 값 그대로 전달
- 곱셈 노드: (이전 값) x (출력값의 미분)
- Sigmoid 함수에 대한 출력
$E\cdot (1-h(x))\cdot h(x)$
</aside>
