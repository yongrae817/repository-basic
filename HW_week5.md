# P3.1
그림 P3.1에 스프링–질량–감쇠기 시스템이 주어져 있다.  
(a) 적당한 상태변수를 설정하라.  
(b) 상태변수로 표현된 1차 미분방정식을 구하라.  
(c) 상태미분방정식을 행렬 형태로 구하라.

---

## (a) 적당한 상태변수를 설정하라.

스프링–질량–감쇠기 시스템의 운동방정식은 다음과 같다.

$$
M\ddot{y}(t) + b\dot{y}(t) + k\,y(t) = F(t)
$$

여기서,
- $M$: 질량  
- $b$: 감쇠계수 (damping coefficient)  
- $k$: 스프링 상수 (spring constant)  
- $F(t)$: 외력 (입력)  
- $y(t)$: 질량의 변위 (출력)

적절한 상태변수를 다음과 같이 정의한다.

$$
x_1(t)=y(t), \qquad x_2(t)=\dot{y}(t)
$$

2차 미분 방정식이므로 상태변수를 2개 설정해야한다.

---

## (b) 상태변수로 표현된 1차 미분방정식을 구하라.

운동방정식을 상태변수 형태로 바꾸면 다음과 같다.

$$
\dot{x}_1(t)=x_2(t)
$$

$$
\dot{x}_2(t)= -\frac{k}{M}x_1(t) - \frac{b}{M}x_2(t) + \frac{1}{M}F(t)
$$

**이때 주의할 점으로, 상태변수 x_1(t)와 x_2(t)가 항등식이 되지 않도록 해야한다. 단순히 상수배 한 경우도 안되며, 두 상태변수는 서로 독립적이어야한다.**

---

## (c) 상태미분방정식을 구하라.

상태벡터와 입력/출력은 다음과 같이 둔다.

$$
\mathbf{x}(t)=
\begin{bmatrix}
x_1(t)\\
x_2(t)
\end{bmatrix},
\qquad
u(t)=F(t),
\qquad
y(t)=x_1(t)
$$

그때 상태미분방정식(선형, 시간불변 LTI)은

$$
\dot{\mathbf{x}}(t)=A\,\mathbf{x}(t)+B\,u(t),
\qquad
y(t)=C\,\mathbf{x}(t)+D\,u(t)
$$

여기서 행렬 \(A,B,C,D\) 는

$$
A=
\begin{bmatrix}
0 & 1\\
-\dfrac{k}{M} & -\dfrac{b}{M}
\end{bmatrix},
\qquad
B=
\begin{bmatrix}
0\\[2pt]
\dfrac{1}{M}
\end{bmatrix},
\qquad
C=
\begin{bmatrix}
1 & 0
\end{bmatrix},
\qquad
D=
\begin{bmatrix}
0
\end{bmatrix}.
$$

---

