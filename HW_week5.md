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
M\ddot{y}(t) + b\dot{y}(t) + ky(t) = F(t)
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

**이때 주의할 점으로, 상태변수 $x_1(t)$와 $x_2(t)$가 항등식이 되지 않도록 해야한다. 단순히 상수배 한 경우도 안되며, 두 상태변수는 서로 독립적이어야한다.**

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
\dot{\mathbf{x}}(t)=A\\mathbf{x}(t)+Bu(t)
\qquad
$$

여기서 행렬 \(A,B\) 는

$$
A=
\begin{bmatrix}
0 & 1\\
-\dfrac{k}{M} & -\dfrac{b}{M}
\end{bmatrix}
\qquad
B=
\begin{bmatrix}
0\\
\dfrac{1}{M}
\end{bmatrix}\quad
$$

이때 출력방정식은

$$
\\mathbf{y}(t)=C\\mathbf{x}(t)+Du(t)
\qquad
$$

여기서 행렬 \(C,D\) 는

$$
C=\begin{bmatrix}1 & 0\end{bmatrix}, \qquad D=\begin{bmatrix}0\end{bmatrix}
$$

---

# P3.3
그림 P3.3과 같은 RLC 회로가 주어졌다.  
상태변수를 $x_1(t) = i_L(t)$, $x_2(t) = v_C(t)$
로 설정하고 상태방정식을 구하라.
<img width="639" height="277" alt="image" src="https://github.com/user-attachments/assets/085577a1-314f-402b-9412-5f3974a393b2" />

---

## 회로 관계식

노드 전압 정의

$$
v_A(t)=v_2(t)-x_2(t)
$$

인덕터 KVL

$$
L\\dot x_1 = v_1 - v_A = v_1 - (v_2 - x_2)
$$

즉

$$
\dot x_1 = \frac{1}{L}\\big(x_2 + v_1 - v_2\big)
$$

노드 A의 KCL \(($i_L=i_R+i_C$)\)

$$
i_R=\frac{v_N}{R}=\frac{v_2-x_2}{R}\quad
i_C=C\\frac{d}{dt}(v_N - v_2)=-C\\dot x_2
$$

따라서

$$
x_1=\frac{v_2-x_2}{R}-C\,\dot x_2
\quad\Rightarrow\quad
\dot x_2=\frac{1}{RC}(v_2-x_2)-\frac{1}{C}x_1
$$

---

## 상태방정식 (스칼라)

$$
\dot{x}_1=\frac{1}{L}x_2+\frac{1}{L}v_1-\frac{1}{L}v_2
$$

$$
\dot{x}_2=-\frac{1}{C}x_1-\frac{1}{RC}x_2+\frac{1}{RC}v_2
$$

---

## 상태공간형 (행렬)

입력을 다음과 같이 둔다.

$$
u(t) =
\begin{bmatrix}
v_1(t) \\
v_2(t)
\end{bmatrix}
$$

상태방정식은 다음과 같다.

$$ 
\begin{bmatrix} 
\dot{x}_1 \ \dot{x}_2 
\end{bmatrix} =
\begin{bmatrix}
0 & \frac{1}{L} \\
-\frac{1}{C} & -\frac{1}{RC}
\end{bmatrix}
\begin{bmatrix}
x_1 \\
x_2
\end{bmatrix}
+
\begin{bmatrix}
\frac{1}{L} & -\frac{1}{L} \\
0 & \frac{1}{RC}
\end{bmatrix}
\begin{bmatrix}
v_1 \\
v_2
\end{bmatrix}
$$

---
