### Linear Regression

<aside>

### Q)

$y = \beta_0 + \beta _1x$

</aside>

<aside>

### A)

**Step1)**

⇒ $\beta_1 = {S_{xy}\over S_{xx}} = {{n\sum x_iy_i-}\sum x_i\sum y_i\over{n\sum x_i^2-(\sum x_i)^2}}$

⇒ $\beta _0 = \overline{y} - \beta_1\overline{x}$

**Step2) Predict $y$ by inserting $x$ and $\beta_0,\beta_1$**

⇒ $y = \beta_0 + \beta _1x$

**Step3)**

⇒ $r = {S_{xy}\over{\sqrt S_{xx}\sqrt S_{yy}}} = {{\sum (x_i-\overline{x})(y_i-\overline{y})}\over{\sqrt{\sum (x_i-\overline{x})^2}\sqrt{\sum (y_i - \overline{y})^2}}}$

Correlation Coefficient  $r = \sqrt{R^2}$ ⇒ 단순회귀에서만 등호 성립

</aside>

### Quadratic Regression

<aside>

### Q)

$y=\beta_0 +\beta_1x+\beta_2x^2$

</aside>

<aside>

### A)

**Step1) Calculate  $\beta_0,\beta_1,\beta_2$** 

⇒  $\beta_0n + \beta_1\sum x_i + \beta_2\sum x_i^2 = \sum y_i$

⇒ $\beta_0\sum x_i + \beta_1 \sum x_i^2 + \beta_2\sum x_i^3  = \sum x_iy_i$

⇒ $\beta_0\sum x_i^2 + \beta_1\sum x_i^3 + \beta_2\sum x_i^4 = \sum x_i^2 y_i$

**Step2) Predict $y$ by inserting $x$ and $\beta_0,\beta_1, \beta_2$**
⇒  $y = \beta_0 +\beta_1x+\beta_2x^2$

**Step3)**

⇒ $R^2 = 1 - {\sum (y_i-\hat y_i)^2\over \sum(y_i-\bar y)^2}$

⇒ Total Quadratic Error:  $\sum e_i^2 = \sum (y_i-\hat y_i)^2$

</aside>

### ~~Cubic Regression~~

<aside>

### Q)

$y = \beta_0 +\beta_1x+\beta_2x^2+\beta_3x^3$

</aside>

<aside>

### A)

**Step1) Calculate  $\beta_0, \beta_1, \beta_2, \beta_3$**

⇒ $\beta_0n+\beta_1\sum x_i + \beta_2 \sum x_i^2 +\beta_3\sum x_i^3 = \sum y_i$

⇒ $\beta_0\sum x_i + \beta_1\sum x_i^2 + \beta_2 \sum x_i^3 + \beta_3 \sum x_i^4 = \sum x_iy_i$

⇒ $\beta_0 \sum x_i^2 +\beta_1\sum x_i^3 + \beta_2 \sum x_i^4 + \beta_3 \sum x_i^5 = \sum x_i^2 y_i$

⇒ $\beta_0\sum x_i^3 + \beta_1\sum x_i^4 + \beta_2\sum x_i^5 + \beta_3\sum x_i^6 = \sum x_i^3y_i$

**Step2) Predict $y$ by inserting $x$ and $\beta_0,\beta_1, \beta_2,\beta_3$**

⇒ $y = \beta_0 +\beta_1x+\beta_2x^2+\beta_3x^3$

Step3)

⇒ $R^2 = 1 - {\sum (y_i-\hat y_i)^2\over \sum(y_i-\bar y)^2}$

</aside>
