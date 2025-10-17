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

**KVL 사용**

$$
v_A(t)=v_2(t)-v_c(t)
v_A(t)=v_1(t)-L\\dot x_1
$$

즉

$$
\dot x_1 = \frac{1}{L}\\big(x_2 + v_1 - v_2\big)
$$

**KCL 사용**

$$
i_R=\frac{v_N}{R}=\frac{v_2-x_2}{R}\quad
i_C=C\\frac{d}{dt}(v_N - v_2)=-C\\dot x_2
$$

따라서

$$
x_1=\frac{v_2-x_2}{R}-C\\dot x_2
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
\dot{\mathbf{x}}(t)=
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

# P3.5
그림 P3.5에 폐루프 제어시스템이 주어져 있다.
(a) 폐루프 전달함수 $T(s)=Y(s)/R(s)$를 구하라.
(b) 상태변수 모델을 구하고 위상변수형 블록선도를 작성하라.(이번 과제에선 블록선도 없이 **phase variable form**으로 답을 구한다.)
<img width="890" height="261" alt="image" src="https://github.com/user-attachments/assets/af109f29-9f52-4172-9026-ddb1476b581a" />

---

## (a) 폐루프 전달함수 $T(s)=Y(s)/R(s)$를 구하라.

주어진 시스템의 구성요소는 다음과 같다.

$$
G_c(s) = \frac{s+2}{s+8}, \qquad 
G_p(s) = \frac{1}{s(s-3)}, \qquad 
H(s) = 1
$$

주어진 블록선도를 등가변환 하면 다음과 같다.

$$
R(s) \rightarrow \frac{s+2}{s+8} *\frac{1}{s-3} *\frac{1}{s} \rightarrow Y(s)
$$

$$
R(s) \rightarrow 
 \frac{s + 2}{(s + 8)(s - 3)s} 
= \frac{s + 2}{s^3 + 5s^2 - 24s} 
\rightarrow Y(s)
$$

따라서, 전달함수는 다음과 같다.

$$
T(s) = \frac{ \frac{s + 2}{s^3 + 5s^2 - 24s}}{1+ \frac{s + 2}{s^3 + 5s^2 - 24s}} = \frac{s+2}{s^3 + 5s^2 - 23s + 2}
$$

---

## (b) 상태변수 모델을 구하고 위상변수형 블록선도를 작성하라.

위에서 구한 전달함수 $T(s)$는 다음과 같이 표현할 수 있다.

$$
T(s) = \frac{Y(s)}{R(s)} =\frac{s+2}{s^3 + 5s^2 - 23s + 2} \cdot \frac{Z(s)}{Z(s)}
$$

따라서 다음과 같이 볼 수 있다.

$$
Y(s) = (s + 2) Z(s)
$$

$$
R(s) = (s^3 + 5s^2 - 23s + 2) Z(s)
$$

이를 라플라스 역변환하면,

$$
Y(t) = \ddot{z}(t) + 2\dot{z}(t)
$$

$$
R(t) = \dddot{z}(t) + 5\ddot{z}(t) - 23\dot{z}(t) + 2z(t)
$$

따라서 다음과 같이 표현할 수 있다.

$$
\mathbf{x}(t) =
\begin{bmatrix}
x_1(t)\\
x_2(t)\\
x_3(t)
\end{bmatrix}
=\begin{bmatrix}
z(t)\\
\dot{x}(t)\\
\ddot{x}(t)
\end{bmatrix}
=\begin{bmatrix}
z(t)\\
\dot{z}(t)\\
\ddot{z}(t)
\end{bmatrix}
$$

---

이때,  

$$
\dot{x}_3(t) = \dddot{z}(t)
$$

$$
\dddot{z}(t) = -5\ddot{z}(t) + 23\dot{z}(t) - 2z(t) + r(t)
$$  

이므로,

---

출력방정식은 다음과 같다.

$$
y(t) = 2x_1(t) + x_2(t)
$$

---

상태방정식은 다음과 같다.

$$
\dot{\mathbf{x}}(t) =
\begin{bmatrix}
0 & 1 & 0\\
0 & 0 & 1\\
-2 & 23 & -5
\end{bmatrix}
\begin{bmatrix}
x_1(t)\\
x_2(t)\\
x_3(t)
\end{bmatrix}
+
\begin{bmatrix}
0\\
0\\
1
\end{bmatrix}r(t)
$$

---

# P3.12
전달함수가

$$
\frac{Y(s)}{R(s)} = T(s) = \frac{8(s + 5)}{s^3 + 12s^2 + 44s + 48}
$$

인 시스템에서,  
(a) 상태공간모델을 구하라.  
(b) 상태천이행렬 $\Phi(t)\$를 구하라.

---

## (a) 상태공간모델을 구하라.

전달함수 $T(s)$는 다음과 같이 표현할 수 있다.

$$
T(s) \= \frac{Y(s)}{R(s)} \= \frac{8(s + 5)}{s^3 + 12s^2 + 44s + 48} \cdot \frac{Z(s)}{Z(s)}  
\= \frac{8s + 40}{s^3 + 12s^2 + 44s + 48} \cdot \frac{Z(s)}{Z(s)}
$$

따라서 다음과 같이 볼 수 있다.

$$
Y(s) = (8s + 40) Z(s)
$$

$$
R(s) = (s^3 + 12s^2 + 44s + 48) Z(s)
$$

이를 라플라스 역변환하면,

$$
Y(t) = 8\dot{z}(t) + 40z(t)
$$

$$
R(t) = \dddot{z}(t) + 12\ddot{z}(t) + 44\dot{z}(t) + 48z(t)
$$

따라서 다음과 같이 표현할 수 있다.

$$
\mathbf{x}(t) =
\begin{bmatrix}
x_1(t)\\
x_2(t)\\
x_3(t)
\end{bmatrix}
=\begin{bmatrix}
z(t)\\
\dot{x}(t)\\
\ddot{x}(t)
\end{bmatrix}
=\begin{bmatrix}
z(t)\\
\dot{z}(t)\\
\ddot{z}(t)
\end{bmatrix}
$$  

---

이때,

$$
\dot{x}_3(t) = \dddot{z}(t)
$$

$$
\dddot{z}(t) = -48z(t) - 44\dot{z}(t) -12\ddot{z}(t) + r(t)
$$  

이므로,  

---

출력방정식은 다음과 같다.

$$
y(t) = 40x_1(t) + 8x_2(t)
$$

---

상태방정식은 다음과 같다.

$$
\dot{\mathbf{x}}(t) =
\begin{bmatrix}
0 & 1 & 0\\
0 & 0 & 1\\
-48 & -44 & -12
\end{bmatrix}
\begin{bmatrix}
x_1(t)\\
x_2(t)\\
x_3(t)
\end{bmatrix}
+
\begin{bmatrix}
0\\
0\\
1
\end{bmatrix}r(t)
$$

---

## (b) 상태천이행렬 $\Phi(t)\$를 구하라.

$$
A = \begin{bmatrix}
0 & 1 & 0\\
0 & 0 & 1\\
-48 & -44 & -12
\end{bmatrix}, 
B = \begin{bmatrix}
0\\
0\\
1
\end{bmatrix}
$$  

라고 하면,  

$$
\dot{\mathbf{x}}(t) = Ax(t) + Br(t)
$$  

이 상태공간방정식을 라플라스 변환 하면,  

$$
sX(s) = AX(s) + BR(s)
$$  

$$
\Rightarrow [sI-A]X(s) = BR(s)
$$  

따라서,  

$$
X(s) = [sI - A]^{-1} BR(s) \text{ 에서, } \Phi(s) = [sI - A]^{-1}
$$  

$$
[sI - A] =
\begin{bmatrix}
s & 0 & 0 \\
0 & s & 0 \\
0 & 0 & s
\end{bmatrix} -
\begin{bmatrix}
0 & 1 & 0 \\
0 & 0 & 1 \\
-48 & -44 & -12
\end{bmatrix} =
\begin{bmatrix}
s & -1 & 0 \\
0 & s & -1 \\
48 & 44 & s + 12
\end{bmatrix}
$$  

이므로,

$$
\Phi(s)\ = \begin{bmatrix}
s & -1 & 0 \\
0 & s & -1 \\
48 & 44 & s+12
\end{bmatrix}^{-1} =
\begin{bmatrix}
\dfrac{s^2 + 12s + 44}{s^3 + 12s^2 + 44s + 48} &
\dfrac{s + 12}{s^3 + 12s^2 + 44s + 48} &
\dfrac{1}{s^3 + 12s^2 + 44s + 48} \\
\dfrac{-48}{s^3 + 12s^2 + 44s + 48} &
\dfrac{s^2 + 12s}{s^3 + 12s^2 + 44s + 48} &
\dfrac{s}{s^3 + 12s^2 + 44s + 48} \\
\dfrac{-48s}{s^3 + 12s^2 + 44s + 48} &
\dfrac{-44s - 48}{s^3 + 12s^2 + 44s + 48} &
\dfrac{s^2}{s^3 + 12s^2 + 44s + 48} \\
\end{bmatrix}
$$  

이를 라플라스 역변환 하면,

$$
\Phi(t)\ = \begin{bmatrix}
3e^{-2t} - 3e^{-4t} + e^{-6t} &
\frac{5}{4}e^{-2t} - 2e^{-4t} + \frac{3}{4}e^{-6t} &
\frac{1}{8}e^{-2t} - \frac{1}{4}e^{-4t} + \frac{1}{8}e^{-6t} \\
-6e^{-2t} + 12e^{-4t} - 6e^{-6t} &
-\frac{5}{2}e^{-2t} + 8e^{-4t} - \frac{9}{2}e^{-6t} &
-\frac{1}{4}e^{-2t} + e^{-4t} - \frac{3}{4}e^{-6t} \\
12e^{-2t} - 48e^{-4t} + 36e^{-6t} &
5e^{-2t} - 32e^{-4t} + 27e^{-6t} &
\frac{1}{2}e^{-2t} - 4e^{-4t} + \frac{9}{2}e^{-6t}
\end{bmatrix}
$$

---

# P3.17
다음과 같은 상태변수 방정식으로 표현된 시스템이 있다.

$$
\dot{x}(t) =
\begin{bmatrix}
1 & 1 & -1 \\
4 & 3 & 0 \\
-2 & 1 & 10
\end{bmatrix}
x(t) +
\begin{bmatrix}
0 \\
0 \\
4
\end{bmatrix}
u(t),
$$

$$
y(t) =
\begin{bmatrix}
1 & 0 & 0
\end{bmatrix}
x(t)
$$

$G(s) = \dfrac{Y(s)}{U(s)}$를 구하라.

---

$$
A = \begin{bmatrix}
0 & 1 & 0\\
0 & 0 & 1\\
-48 & -44 & -12
\end{bmatrix}, 
B = \begin{bmatrix}
0\\
0\\
1
\end{bmatrix}  
C = \begin{bmatrix}
0 & 1 & 0
\end{bmatrix},
D = 0
$$  

라고 하자.  

$$
\dot{x}(t) = Ax(t) + Bu(t)
$$

$$
y(t) = Cx(t)
$$  

이를 라플라스 역변환하면,

$$
sX(s) = AX(s) + BU(s)
$$  

$$
Y(s) = CX(s)
$$

$$
[sI-A]X(s) = BU(s)
$$  

따라서,  

$$
X(s) = [sI - A]^{-1} BU(s) \text{ 에서, } \Phi(s) = [sI - A]^{-1}
$$  

$$
\Phi(s) = 
\begin{bmatrix}
s-1 & -1 & 1 \\
-4 & s-3 & 0 \\
2 & -1 & s-10
\end{bmatrix}^{-1} =
\begin{bmatrix}
\dfrac{s^2 - 13s + 30}{s^3 - 14s^2 + 37s + 20} &
\dfrac{s - 11}{s^3 - 14s^2 + 37s + 20} &
\dfrac{-s + 3}{s^3 - 14s^2 + 37s + 20} \\
\dfrac{4s - 40}{s^3 - 14s^2 + 37s + 20} &
\dfrac{s^2 - 11s + 8}{s^3 - 14s^2 + 37s + 20} &
\dfrac{-4}{s^3 - 14s^2 + 37s + 20} \\
\dfrac{-2s + 10}{s^3 - 14s^2 + 37s + 20} &
\dfrac{s - 3}{s^3 - 14s^2 + 37s + 20} &
\dfrac{s^2 - 4s - 1}{s^3 - 14s^2 + 37s + 20}
\end{bmatrix}
$$

$$
X(s) = \Phi(s) BU(s)  
Y(s) = C \Phi(s) BU(s)
$$  

$$
G(s) = \dfrac{Y(s)}{U(s)} = C\Phi(s) B = 
\begin{bmatrix}
\dfrac{- 4s + 12}{s^3 - 14s^2 + 37s + 20}
\end{bmatrix}
$$
