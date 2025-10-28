# 5주차 강의 정리: State-Space Representation

---

## 1️.State Variable Model

### 🧩 시스템 내의 State 정의
- 시스템의 **상태(state)** 란 시스템 내부의 동적 정보를 나타내는 변수이다.  
- 상태는 **입력(input)** 및 **시스템의 특성(자체 dynamics)** 에 의해 결정된다.  
- 상태 방정식을 중심으로 시스템을 기술하면, 미분방정식의 해석이 용이해진다.

---

### Spring–Mass–Damper System

$$
M \frac{d^2 y(t)}{dt^2} + b \frac{dy(t)}{dt} + k y(t) = r(t)
$$

- 2차 미분방정식이므로 **state 2개**를 선택해야 함.
  - $$x_1(t) = y(t)$$ → 변위(displacement)  
  - $$x_2(t) = \dot{y}(t)$$ → 속도(velocity)

따라서,

$$
\begin{cases}
\dot{x}_1(t) = x_2(t) \\
\dot{x}_2(t) = -\frac{b}{M}x_2(t) - \frac{k}{M}x_1(t) + \frac{1}{M}r(t)
\end{cases}
$$

$$
y(t) = x_1(t)
$$

- $$x_1(t)$$와 $$x_2(t)$$는 **독립적인 상태변수**로 선택해야 한다.  
- 서로 종속되지 않고 시스템의 전체 동작을 기술할 수 있어야 한다.  

---

## 2️.State Space Equation

### 기본형

$$
\dot{x}(t) = A x(t) + B u(t)
$$

$$
y(t) = C x(t) + D u(t)
$$

여기서  
- $$x(t)$$: 상태벡터 (state vector)  
- $$u(t)$$: 입력벡터 (input)  
- $$y(t)$$: 출력벡터 (output)  
- $$A, B, C, D$$: 시스템 행렬들

---

### 상태공간 해 (State Transition)

Laplace domain에서,

$$
(sI - A)X(s) = X(0) + BU(s)
$$

따라서 시간영역에서,

$$
x(t) = e^{At}x(0) + \int_0^t e^{A(t-\tau)}Bu(\tau)d\tau
$$

- 첫 번째 항: **초기 상태의 영향 (Transition from initial state)**  
- 두 번째 항: **입력의 영향 (Effect of input)**

---

## 3️.State Transition Matrix

- 1차 시스템의 경우:  

$$
x(t) = e^{at}x(0) + \int_0^t e^{a(t-\tau)}bu(\tau)d\tau
$$

- n차 시스템의 경우:  

$$
x(t) = e^{At}x(0) + \int_0^t e^{A(t-\tau)}Bu(\tau)d\tau
$$

---

## 4️.Summary

- **State = 시스템 내부 상태**  
- **State를 통해 시스템의 동특성을 수학적으로 표현할 수 있다.**  
- **n차 미분방정식 → 1차 연립 미분방정식으로 변환**

즉,  

$$
\text{고차 미분방정식} \Rightarrow \text{State Space Equation}
$$

---

## 5️.State 선정 방법

### 🔸 Phase Variable Canonical Form
전달함수(Transfer Function)를 **State-Space Form**으로 변환하는 표준 방법.

$$
G(s) = \frac{Y(s)}{U(s)} = \frac{b_3 s^3 + b_2 s^2 + b_1 s + b_0}{s^4 + a_3 s^3 + a_2 s^2 + a_1 s + a_0}
$$

---

### 상태변수 설정

$$
x_1(t) = z(t), \quad x_2(t) = \dot{z}(t), \quad x_3(t) = \ddot{z}(t), \quad x_4(t) = \dddot{z}(t)
$$

따라서,

$$
\dot{x}(t) =
\begin{bmatrix}
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
-a_0 & -a_1 & -a_2 & -a_3
\end{bmatrix}
x(t) +
\begin{bmatrix}
0 \\ 0 \\ 0 \\ 1
\end{bmatrix}u(t)
$$

$$
y(t) = [b_0 \quad b_1 \quad b_2 \quad b_3]x(t)
$$

$$
(D = 0)
$$

즉,

$$
y(t) = Cx(t) + D u(t)
$$

---

## 정리 요약

| 구분 | 의미 |
|------|------|
| **State Variable** | 시스템의 내부 동적 상태 |
| **State Equation** | $$\dot{x}(t) = A x(t) + B u(t)$$ |
| **Output Equation** | $$y(t) = C x(t) + D u(t)$$ |
| **Transition Matrix** | $$e^{At}$$ |
| **목적** | 고차 미분방정식을 1차 연립방정식으로 단순화 |

---

