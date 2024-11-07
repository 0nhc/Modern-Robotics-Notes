# Chapter 5
## Introduction
In this chapter we study the relationship between joint velocities and the end-effector velocity.

We can denote forward kinematics as $x(t) = f(\theta(t))$, so what we do in this chapter is to find
$$
\frac{d}{dt}x(t)=\frac{d}{dt}f(\theta(t))
$$
Apply chain rule:
$$
\\dot(x) = \frac{\partial f}{\partial\theta}(\theta)\dot{\theta}
$$

The  $\frac{\partial f}{\partial\theta}$ is called the **Jacobian**, denoting as $J(\theta)$.

Let $\tau = vector\ of\ joint\ torques\ or\ forces$, then we have $power = \dot{\theta}^T\tau = V^TF$, thus:
$$
\dot(\theta)^T\tau = (J(\theta)\dot{\theta})^TF\\
\dot(\theta)^T\tau =\dot{\theta}^TJ^T(\theta)F\\
\tau = J^T(\theta)F
$$

In conclusion

$$
V = J(\theta)\dot{\theta}\\
\tau = J^T(\theta)F
$$

## 5.1.1 Space Jacobian
For `{s}` screws, the **space Jacobian** $J_s(\theta)$ is defined by:

$$
J_{s}(\theta) = [J_{s1}(\theta)\ J_{s2}(\theta)\ \dots J_{sn}(\theta)]\in \R^{6\times n}\\
J_{s1}(\theta) = S_1(\theta)\\
J_{si}(\theta) = [Ad_{e^{[S_1]\theta_1}\ e^{[S_2]\theta_2}\ \dots \ e^{[S_{i-1}]\theta_{i-1}}}]S_i
$$


## 5.1.2 - 5.1.4 Body Jacobian
For `{b}` screws, the **body Jacobian** $J_b(\theta)$ is defined by:

$$
J_{b}(\theta) = [J_{b1}(\theta)\ J_{b2}(\theta)\ \dots J_{bn}(\theta)]\in \R^{6\times n}\\
J_{bn}(\theta) = B_n(\theta)\\
J_{bi}(\theta) = [Ad_{e^{-[B_n]\theta_n}\ e^{-[B_{n-1}]\theta_{n-1}}\ \dots \ e^{-[S_{i+1}]\theta_{i+1}}}]S_i
$$

Also

$$
J_b(\theta)=[Ad_{T_{bs}}]J_s(\theta)\\
J_s(\theta)=[Ad_{T_{sb}}]J_b(\theta)
$$


## 5.2 Statics of Open Chains
When a $F_b$ is applied on `{b}`, the arm has to generate an axtra $\tau$ to resist this disturbance.

$$
\tau^T\dot{\theta}=F_b^TV_b=power\ at\ hand\\
\tau^T\dot{\theta}=F_b^TJ_b(\theta)\dot{\theta}\\
\tau^T=F_b^TJ_b(\theta)\\
\tau = J_b^T(\theta)F_b
$$


## 5.3 Singularities
For a robot having $n$ joints,
$$
J(\theta)\in \R^{6\times n}\\
rank\ \ \ J(\theta) \le min(6,n)\\
full\ rank\ if\ \ \ rank\ J(\theta) = min(6, n)\\
singular\ at\ \theta^* if\ rank\ J(\theta^*) \lt \underset{\theta}{max}\ rank\ J(\theta)
$$

If $n\lt 6$, the $J(\theta)$ is tall, and we call such robots **kinematically deficient**.

If $n=6$, we call such robots **square**.

If $n\gt6$, the $J(\theta)$ is fat, we call such robots **redundant**.


# 5.4 Manipulability
For end effector twist V,
$$
V=J(\theta)\dot{\theta}\\
V\in \R^m,\dot{\theta}\in\R^n,J(\theta)\in\R^{m\times n}\\
\dot{\theta}^T\dot{\theta}=1\\
\ \\
V^TA^{-1}V=1\\
A=JJ^T\in\R^{m\times m}
$$

Thus it's the same for any vector x:

$$
x^TA^{-1}x =1\\
A\in\R^{m\times m}(symmetric,\ positive\ definite)\\
eigen\ values\ of\ A = \lambda_1,\dots \lambda_m\\
eigen\ vectors\ of\ A =v_1,\dots v_m
$$

If $A=JJ^T$, then $x=V$, this is called the **manipulability ellipsoid**.

If $A=(JJ^T)^{-1}$, then $x=F$, this is called the **force ellipsoid**.

Manipulability measurements:

(1) ratio of longest and shortest axes.
$$
\mu_1(A)=\frac{\sqrt{\lambda_{max}(A)}}{\sqrt{\lambda_{min}(A)}}=\sqrt{\frac{\lambda_{max}(A)}{\lambda_{min}(A)}}\ge1\ (=1:\ isotropic))
$$

(2) condition number of A.
$$
\mu_2(A)=\frac{\lambda_{max}(A)}{\lambda_{min}(A)}\ge 1
$$

(3) Proportional to volume of ellipsoid
$$
\mu_3(A)=\sqrt{\lambda_1\lambda_2\dots}=\sqrt{det(A)}
$$

For any configuration of the robot,
$$
J_b(\theta)=
\begin{bmatrix}
J_{bw}(\theta)\\
J_{bv}(\theta)
\end{bmatrix} \in \R^{6\times 6}\\
J_{bw}(\theta)\in \R^{3\times n}\ \rightarrow angular\ velocity/moment\ ellipsoids\\
J_{bv}(\theta)\in \R^{3\times n}\ \rightarrow linear\ velocity/force\ ellipsoids\\

$$