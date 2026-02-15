### **Question)**

$$
a_1x + b_1y + c_1z = d_1\\a_2x+b_2y+c_2z=d_2\\a_3x+b_3y+c_3z=d_3\\ x^{(0)} = k_1,\space yx^{(0)} = k_2, \space z^{(0)} = k_3 \\w=m\\ \epsilon_a=n\%
$$

### Solving)

Check the value of $\bold{w}$

If  $\bold{ 0<w<1}$  ⇒ **SUR**

If  $\bold{1<w<2}$  ⇒ **SOR**

### 1. SUR(Successive Under Relaxation Method)

### 2. SOR(Successive Over Relaxation Method)

**Step1)**

**Check the main diagonals are non-zeros.** 

**Check the question is Diagonally Dominant.**

$a_1,b_2,c_3 \neq 0$

$|a_1| \geq |b_1| + |c_1| \\ |b_2| \geq |a_2| + |c_2| \\ |c_3| \geq |a_3| + |b_3|$

**Step2)**

**Calculate  $\bold{x, y, z}$ (using Gauss Seidel Method)**

$$
x^{(k)} = \frac {d-by^{(k-1)}-cz^{(k-1)}}{a}\\y^{(k)} = \frac {d-ax^{(k)}-cz^{(k-1)}}{b} \\ z^{(k)} = \frac {d-ax^{(k)}-by^{(k)}}{c}
$$

**Step3)**

**Calculate  $\bold{ x_i^{(k)}, y_i^{(k)}, z_i^{(k)}}$ by using SOR formula.**

$$
x_i^{(k)} = (1-w)x_i^{(k-1)}+w(x_i^{(k)})_{\red{GS}}
$$

$$
y_i^{(k)} = (1-w)y_i^{(k-1)}+w(y_i^{(k)})_{\red{GS}}
$$

$$
z_i^{(k)} = (1-w)z_i^{(k-1)}+w(z_i^{(k)})_{\red{GS}}
$$

**Step4)**

**Calculate the Relative Approximate Error(%)** 

$$
\epsilon_{ax}\space^{(k)} = |\frac {x_{(current)}-x_{(previous)}}{x_{(current)}}| \\ \epsilon_{ay} \space^{(k)}= |\frac {y_{(current)}-y_{(previous)}}{y_{(current)}}| \\ \epsilon_{az}\space^{(k)} = |\frac {z_{(current)}-z_{(previous)}}{z_{(current)}}|\\if \space\epsilon_{ax}, \epsilon_{ay},\epsilon_{az}<\epsilon_a , \space terminated.
$$
