# P3.1
그림 P3.1에 스프링–질량–감쇠기 시스템이 주어져 있다.  
(a) 적당한 상태변수를 설정하라.  
(b) 상태변수로 표현된 1차 미분방정식을 구하라.  
(c) 상태미분방정식을 행렬 형태로 구하라.

<img width="599" height="292" alt="image" src="https://github.com/user-attachments/assets/e9bc0cb0-4f3d-49ca-8004-41af73e6f041" />

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

**2차 미분 방정식이므로 상태변수를 2개 설정해야한다.**

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
$$

여기서 행렬 \(A,B\) 는

$$
A=
\begin{bmatrix}
0 & 1\\
-\dfrac{k}{M} & -\dfrac{b}{M}
\end{bmatrix},
\qquad
B=
\begin{bmatrix}
0\\
\dfrac{1}{M}
\end{bmatrix},\quad
$$

---

# P3.3
그림 P3.3과 같은 RLC 회로가 주어졌다.  
상태변수를 \[
x_1(t) = i_L(t), \quad x_2(t) = v_C(t)
\]
로 설정하고 상태방정식을 구하라.

---

## 회로 설명

- 입력: \( v_i(t) \)
- 출력: \( v_o(t) = v_C(t) \)
- 인덕터 전류: \( i_L(t) \)
- 커패시터 전압: \( v_C(t) \)

회로 구성은 직렬 R–L–C 구조이며,  
전압방정식(KVL)은 다음과 같다.

$$
v_i(t) = L\frac{di_L(t)}{dt} + R i_L(t) + v_C(t)
$$

커패시터의 전류관계는

$$
i_C(t) = C\frac{dv_C(t)}{dt}
$$

이며, 인덕터 전류와 커패시터 전류의 관계는

$$
i_L(t) = i_C(t)
$$

---

## 상태변수로 표현된 1차 미분방정식

위 식들을 상태변수 \(x_1 = i_L(t)\), \(x_2 = v_C(t)\) 로 바꾸면,

1️. 인덕터 전류 미분식  
$$
L\frac{dx_1(t)}{dt} = v_i(t) - R x_1(t) - x_2(t)
$$
$$
\Rightarrow \dot{x}_1(t) = -\frac{R}{L}x_1(t) - \frac{1}{L}x_2(t) + \frac{1}{L}v_i(t)
$$

2️. 커패시터 전압 미분식  
$$
i_C(t) = C\frac{dx_2(t)}{dt} = i_L(t)
$$
$$
\Rightarrow \dot{x}_2(t) = \frac{1}{C}x_1(t)
$$

---

## 상태미분방정식 (State–Space Form)

이를 행렬 형태로 정리하면 다음과 같다.

$$
\begin{bmatrix}
\dot{x}_1(t)\\
\dot{x}_2(t)
\end{bmatrix}
=
\begin{bmatrix}
-\dfrac{R}{L} & -\dfrac{1}{L}\\[6pt]
\dfrac{1}{C} & 0
\end{bmatrix}
\begin{bmatrix}
x_1(t)\\
x_2(t)
\end{bmatrix}
+
\begin{bmatrix}
\dfrac{1}{L}\\[6pt]
0
\end{bmatrix}
v_i(t)
$$

출력 방정식은 \(y(t)=v_C(t)=x_2(t)\) 이므로,

$$
y(t)=
\begin{bmatrix}
0 & 1
\end{bmatrix}
\begin{bmatrix}
x_1(t)\\
x_2(t)
\end{bmatrix}
+ [0]v_i(t)
$$

---

## 상태공간 행렬 요약

$$
A=
\begin{bmatrix}
-\dfrac{R}{L} & -\dfrac{1}{L}\\[6pt]
\dfrac{1}{C} & 0
\end{bmatrix},
\quad
B=
\begin{bmatrix}
\dfrac{1}{L}\\[6pt]
0
\end{bmatrix},
\quad
C=
\begin{bmatrix}
0 & 1
\end{bmatrix},
\quad
D=
\begin{bmatrix}
0
\end{bmatrix}.
$$

---
