### SVM (Linear)

1. Feature Scaling
    - $X_{new}={(2X-max-min)\over max-min}$
2. Create the equations
    - $y_1(w_1x_1+w_2x_2+b)\geq1$
3. Manually Choose the 3 equations ⇒ Gaussian Elimination ⇒ Calculate $w_1,w_2,b$
4. Calculate $x_1,x_2$ (by using $w_1,w_2,b$) ⇒ Draw the hyperplane
5. using the Testing Data
    - SVM hyperplane value:  $f(x)=w_1x_1+w_2x_2+b$
