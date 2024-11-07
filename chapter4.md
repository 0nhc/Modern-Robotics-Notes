# Chapter 4
## 4.1.2 Product of Exponentials Formula in the Space Frame
For a UR5 robotic arm, we define:
* base_link: `{s}`
* ee_link: `{b}`

Forward kinematics is to find $T_{sb}$ given $\theta$. The process of Forward Kinematics:

(1) Denote the zero configuration $T_{sb}(0)$ as $M$

(2) Define screw axes $S_i$ under `{s}` for every link when $\theta=0$.

(3) GIven $\theta$, evaluate the **product of exponentials (PoE)** formula in the space frame:
$$
T_{sb}(\theta) = e^{[S_1]\theta_1}e^{[S_2]\theta_2}\dots e^{S_n}\theta_nM
$$


## 4.1.3 Product of Exponentials Formula in the End-Effector Frame

We can also define screw axes $B_i$ under `{b}`:

(1) Denote the zero configuration $T_{sb}(0)$ as $M$

(2) Define screw axes $B_i$ under `{b}` for every link when $\theta=0$.

(3) GIven $\theta$, evaluate the **product of exponentials (PoE)** formula in the body frame:
$$
T_{sb}(\theta) = Me^{[B_1]\theta_1}e^{[B_2]\theta_2}\dots e^{B_n\theta_n}
$$
