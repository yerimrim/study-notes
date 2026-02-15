### Riemann

<aside>

### Q

$\int_a^b f(x)\space dx =\space ?$

$m$  (the number of pieces)

</aside>

<aside>

### A

**Step1) Divide the interval $[a,b]$ by $m$**

ex) $[0,1], m=4$  ⇒ $[0,0.25],\space [0.25,0.5],\space [0.5,0.75],\space [0.75,1]$

**Step2) Find the mid point of each interval**

ex) $k = 0.125, \space 0.375,\space 0.625,\space 0.875$

**Step3) Calculate** $\{ \sum f(k_i)\} {|b-a|\over m}$

ex) $\{f(0.125)+f(0.375) +f(0.625)+f(0.875)\}{|1-0|\over 4}$

</aside>

---

### Trapezoidal

<aside>

### Q

$\int_a^b f(x)\space dx =\space ?$

$m$ (the number of pieces)

</aside>

<aside>

### A

**Step1) Divide the interval $[a,b]$  by $m$**

ex) $[0,3], m=3$  ⇒ $[0,1],[1,2],[2,3]$  ⇒  $x_0=0,\space x_1=1,\space x_2=2,\space x_3=3$

**Step2) Calculate** ${|b-a|\over 2m}\{f(x_0)+2f(x_1)+2f(x_2)+\cdots + 2f(x_{n-1})+f(x_n)\}$

ex) ${|3-0|\over 2\times3}\{f(0)+2f(1)+2f(2)+f(3)\}$

</aside>

---

### Simpson

<aside>

### Q

$\int_a^b f(x)\space dx =\space ?$

$m$ (the number of pieces)

</aside>

<aside>

### A

**Step1) Divide the interval $[a,b]$  by $m$**

ex) $[0,8], m=4$  ⇒ $[0,2],[2,4],[4,6],[6,8]$

 ⇒ $x_0=0, \space x_1=2,\space x_2=4,\space x_3=6,\space x_4=8$

**Step2) Calculate**

 ${|b-a|\over 3m}\{f(x_0)+4f(x_1)+2f(x_2)+4(x_3)+2f(x_4)+\cdots +4f(x_{n-1})+f(x_n)\}$

ex) ${|8-0|\over 3\times4} \{ f(0)+4f(2)+2f(4)+4f(6)+f(8)\}$

</aside>
