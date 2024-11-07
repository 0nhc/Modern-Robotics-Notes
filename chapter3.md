# Chapter 3
## 3.1 Introduction to Rigid-Body Motions
We will use **Implicit Representations of Configurations**. 

*"In other words, our representation of a configuration will not use a minimum set of coordinates, and velocities will not be the time derivative of coordinates."*

We will use:
* Right-hand frames for axes.
* RIght-hand rules for roations.

To represent a fixed frame in space, we will use:
* The position of the origin of the body frame, expressed in the space-frame coordinates
* The directions of the coordinate axes of the body frame, expressed in the space-frame coordinates


## 3.2.1 Rotation Matrices
### Part 1
Suppose we have a space frame `{s}`, and another frame `{b}`, whose axes are expressed in `{s}` as
$$
\hat{x_b} =
\begin{bmatrix}
0\\
1\\
0
\end{bmatrix}
\ \
\hat{y_b} = 
\begin{bmatrix}
-1\\
0\\
0
\end{bmatrix}
\ \
\hat{z_b} = 
\begin{bmatrix}
0\\
0\\
1
\end{bmatrix}
\
$$
Thus, 
$$
R_{sb} = [\hat{x_b}\ \ \hat{x_b}\ \ \hat{x_b}] = 
\begin{bmatrix}
0&-1&0\\
1&0&0\\
0&0&1
\end{bmatrix}
= R
$$

$R$ is also known as the **special orthogonal group** $SO(3)$.

### Part 2

Three common uses of a rotation matrix:
* (1) Represent an orientation
* (2) Change reference frame
* (3) Rotate a vector or frame

(1) is obvious.

An example for (2):
$$
p_b = 
\begin{bmatrix}
-1\\
0\\
0
\end{bmatrix}
,\ \ 
p_s = R_{sb}p_b = 
\begin{bmatrix}
0\\
0\\
1
\end{bmatrix}
$$

An example for (3):
$$
R_{sb} = R = Rot(\hat{z}, 90^\degree)
$$


## 3.2.2 Angular Velocities

In 3.1, we've got:

*"In other words, our representation of a configuration will not use a minimum set of coordinates, and velocities will not be the time derivative of coordinates."*

Thus, angular velocity $\ne \dot{R}$.

To represent angular velocity for a roating frame, we use a unit vector $\hat{\omega}_s$ to represent the rotation direction (where the $\ \hat{}\ $ indicates it's a unit vector), and $\dot{\theta}$ to represent its rotational speed:
$$
\omega_s = \hat{\omega}_s\dot{\theta}
$$
Thus, the linear velocity of frame `{b}`'s coordinate axes can be represented as:
$$
\dot{\hat{x_b}} = \omega_s\times\hat{x}_b\\
\dot{\hat{y_b}} = \omega_s\times\hat{y}_b\\
\dot{\hat{z_b}} = \omega_s\times\hat{z}_b\\
$$

Here we use a bracket to represent cross product:
$$
x\times y=[x]y
$$
, where
$$
x =
\begin{bmatrix}
x_1\\
x_2\\
x_3
\end{bmatrix}
\in \R^3,\ [x] = 
\begin{bmatrix}
0&-x_3&x_2\\
x_3&0&-x_1\\
-x_2&x_1&0
\end{bmatrix},\ [x] = [x]^T
$$
The set of all $3\times 3$ skew-symmetric real matrices is called $so(3)$.

Thus,
$$
\dot{R_{sb}} = [\dot{\hat{x_b}}\ \ \dot{\hat{y_b}}\ \ \dot{\hat{z_b}}] = [\omega_s]R_{sb} 
$$

From 3.2.1 (Part 2), we can get:
$$
\omega_b = R_{sb}\omega_s = R_{sb}^{-1}\omega_s = R_{sb}^{T}\omega_s
$$

So, in conclusion:
$$
\omega_b = R^{-1}\omega_s=R^T\omega_s \\
[\omega_b] = R^{-1}\dot{R}=R^T\dot{R} \\
\omega_s = R\omega_b \\
[\omega_s] = \dot{R}R^{-1}=\dot{R}R^T
$$


## 3.2.3 Exponential Coordinates of Rotation
**exponential coordinates for rotation**: $\hat{\omega}\theta$

### Part 1

(Review) ODE:
$$
x\in \R:\ \ \ \dot{x}(t)=ax(t)\ \ \  \rightarrow\ \ \ x(t)=e^{at}x(0)\\
e^{at} = 1+at+\frac{(at)^2}{2!}+\frac{(at)^3}{3!}+\dots\\
$$
SImilar, for a vector, we got:
$$
x\in \R^n:\ \ \ \dot{x}(t) = Ax(t)\ \ \ \rightarrow\ \ \ x(t) = e^{At}x(0)\\
e^{At} = 1+At+\frac{(At)^2}{2!}+\frac{(At)^3}{3!}+\dots\\
$$
Here, $e^{At}$ is also known as **matrix exponential**, and $A$ is the $3\times 3$ skew-symmetric representation of the angular velocity.

### Part 2

Suppoer we have a vector $p$ in a frame. When the frame is rotating along $\hat{\omega}$, the end point of $p$ traces a circle. 

Suppose $\dot{\theta} = 1$, with 3.2.2, we know $\dot{p(t)} = \hat{\omega}\times p(t)$, also known as $\dot{p(t)} = [\hat{\omega}]p(t)$.

With Part 1, we can get $p(t)=e^{[\hat{\omega}]\theta}p(0)$.

**Rodrigues' Formula**:
$$
Rot(\hat{\omega},\theta)=e^{[\hat{\omega}]\theta}=I+sin\theta[\hat{\omega}]+(1-cos\theta)[\hat{\omega}]^2\in SO(3)
$$
Also,
$$
p(t)=e^{[\hat{\omega}]\theta}p(0)=e^{[\hat{\omega}\theta]}p(0)
$$

In conclusion,
$$
exp:\ \ \ [\hat{\omega}]\theta\in so(3)\ \ \ \rightarrow\ \ \ R\in SO(3)\\
log:\ \ \ R\in SO(3)\ \ \ \rightarrow\ \ \ [\hat{\omega}]\theta\in so(3)
$$


## 3.3.1 Homogeneous Transformation Matrices
The **Special Euclidean Group** $SE(3)$:
$$
T = 
\begin{bmatrix}
R&p\\
0&1
\end{bmatrix} = 
\begin{bmatrix}
r_{11}&r_{12}&r_{13}&p_1\\
r_{21}&r_{22}&r_{23}&p_2\\
r_{31}&r_{32}&r_{33}&p_3\\
0&0&0&1
\end{bmatrix}
$$

As for its inverse/transpose:
$$
T^{-1} = 
\begin{bmatrix}
R^T&-R^Tp\\
0&1
\end{bmatrix}
$$

Three common uses of a homogeneous transformation matrix:
* (1) Represent a configuration
* (2) Change a reference frame
* (3) Displace a vector or frame

A $T$ matrix rotates first and then translates.


## 3.3.2 Twists
### Part 1
For a frame, we got configuration = $T$. Similarly we can also know rigid-body velocity $\ne \dot{T}$.

Any rigid-body velocity, which consists of a linear component and an angular component, is equivalent to the instantaneous velocity about some screw axis.

The screw axis is defined by a point $q$ on the axis, a unit vector $\hat{s}$ in the direction of the axis, and the pitch $h$ of the screw, which is $\frac{linear\ speed}{angular\ speed}$

We suppose $h$ is finite for now.

The representation of a screw is a 6D vector:
$$
S = 
\begin{bmatrix}
S_\omega\\
S_v
\end{bmatrix} = 
\begin{bmatrix}
angular\ velocity\ when\ \dot{\theta} = 1 \\
linear\ velocity\ of\ the\ origin\ when\ \dot{\theta}=1
\end{bmatrix}
$$
, where
$$
S_v = \dot{\theta}(\hat{s}h-\hat{s}\times q)
$$

And the full representation of angular and linear velocity is twist:
$$
V = 
\begin{bmatrix}
\omega\\
v
\end{bmatrix} = 
S\dot{\theta}
$$

If $h$ is infinite:
$$
S_\omega = 0, \|S_v\|=1, \dot{\theta} = linear\ speed
$$
If $h$ is finite:
$$
\|S_\omega\|=1, \dot{\theta} = rotational\ speed
$$

If $S$ is defined in `{b}`, $V_b=(\omega_b,v_b)=S\dot{\theta}$ is the **body twist**.

If $S$ is defined in `{s}`, $V_s=(\omega_s,v_s)=S\dot{\theta}$ is the **spatial twist**.

### Part 2
* AdT:

If we want to represent a twist in another frame, we will find $V_a\ne T_{ab}V_b$ due to dimension mismatch:
$$
T_{ab}\in \R^{4\times 4}\\
V_b\in \R^{6\times 6}
$$

Thus we nees the $6\times 6$ **adjoint representation** of a transformation matrix:
$$
T=
\begin{bmatrix}
R&p\\
0&1
\end{bmatrix}\ is\ [Ad_T]=
\begin{bmatrix}
R&0\\
[p]R&R
\end{bmatrix}\in \R^{6\times 6}
$$
Thus,
$$
V_a = [Ad_{T_{ab}}]V_b
$$


* se(3):

According to rotation matrix, we have:
$$
[\omega_b] = R^{-1}\dot{R}\in so(3) \\
[\omega_s] = \dot{R}R^{-1}\in so(3)
$$
Similarly, we also have:
$$
[V_b] = T^{-1}\dot{T}=
\begin{bmatrix}
[\omega_b]&v_b\\
0&0
\end{bmatrix}
\in se(3) \\

[V_s] = \dot{T}T^{-1}=
\begin{bmatrix}
[\omega_s]&v_s\\
0&0
\end{bmatrix}
\in se(3)
$$

## 3.3.3 Exponential Coordinates of Rigid-Body Motion
$$
S=(S_\omega,S_v)\\
exp: se(3)\rightarrow SE(3)
$$

If $S_\omega = 0$, $\|S_v\|=1$:
$$
e^{[S]\theta}=
\begin{bmatrix}
I&S_v\theta\\
0&1
\end{bmatrix}
$$
If $\|S_\omega\|=1$:
$$
e^{[S]\theta}=
\begin{bmatrix}
e^{[S_\omega]\theta}&(I\theta+(1-cos\theta)[S_\omega]+(\theta-sin\theta)[S_\omega]^2)S_v\\
0&1
\end{bmatrix}
$$


## 3.4 Wrenches
For a point $r_b$ in frame `{b}`, we apply a force $f_b$ on $r_b$, then the **moment** is $m_b = r_b\times f_b$.

We can package the moment and the force together in a single 6D vector called the wrench:

$$
F_b = 
\begin{bmatrix}
m_b\\
f_b
\end{bmatrix}
$$

How hsould we get $F_s$?

From the fact:
$$
V_s^TF_s= V_b^TF_b = power
$$

We can infer:
$$
V_s^TF_s = ([AdT_{bs}]V_s)^TF_b\\
V_s^TF_s = V_s^T[AdT_{bs}]^TF_b
$$

Thus:
$$
F_s = [AdT_{bs}]^TF_b\ne[AdT_{sb}]F_b
$$