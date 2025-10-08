# P3.1
그림 P3.1에 스프링–질량–감쇠기 시스템이 주어져 있다.  
(a) 적당한 상태변수를 설정하라.  
(b) 상태변수로 표현된 1차 미분방정식을 구하라.  
(c) 상태미분방정식을 행렬 형태로 구하라.

---

## (a) 상태변수 설정

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

---

## (b) 상태변수로 표현된 1차 미분방정식

운동방정식을 상태변수 형태로 바꾸면 다음과 같다.

$$
\dot{x}_1(t)=x_2(t)
$$

$$
\dot{x}_2(t)= -\frac{k}{M}x_1(t) - \frac{b}{M}x_2(t) + \frac{1}{M}F(t)
$$

---

## (c) 상태미분방정식 (State-Space Form)

행렬 형태로 표현하면 다음과 같다.

$$
\begin{bmatrix}
\dot{x}_1(t)\\
\dot{x}_2(t)
\end{bmatrix}
=
\begin{bmatrix}
0 & 1\\
-\dfrac{k}{M} & -\dfrac{b}{M}
\end{bmatrix}
\begin{bmatrix}
x_1(t)\\
x_2(t)
\end{bmatrix}
+
\begin{bmatrix}
0\\[2pt]
\dfrac{1}{M}
\end{bmatrix}
\,F(t)
$$

출력 방정식은 다음과 같다.

$$
y(t)=
\begin{bmatrix}
1 & 0
\end{bmatrix}
\begin{bmatrix}
x_1(t)\\
x_2(t)
\end{bmatrix}
+\,0\cdot F(t)
$$


---

## 상태공간 모델 요약

$$
\dot{x}(t)=A\,x(t)+B\,u(t), \qquad
y(t)=C\,x(t)+D\,u(t)
$$

여기서,

$$
A=
\begin{bmatrix}
0 & 1\\
-\dfrac{k}{M} & -\dfrac{b}{M}
\end{bmatrix},\quad
B=
\begin{bmatrix}
0\\[2pt]
\dfrac{1}{M}
\end{bmatrix},\quad
C=
\begin{bmatrix}
1 & 0
\end{bmatrix},\quad
D=
\begin{bmatrix}
0
\end{bmatrix}.
$$


---

## 요약
| 구분 | 식 | 의미 |
|------|----|------|
| 운동방정식 | \(M\ddot{y} + b\dot{y} + ky = F(t)\) | 시스템의 동적 특성 |
| 상태변수 | \(x_1 = y, \; x_2 = \dot{y}\) | 변위, 속도 |
| 상태방정식 | \(\dot{x}_1 = x_2,\; \dot{x}_2 = -\frac{k}{M}x_1 - \frac{b}{M}x_2 + \frac{1}{M}F(t)\) | 1차 미분형 |
| 행렬 형태 | \(A, B, C, D\) | 상태공간 모델 |

--- 
