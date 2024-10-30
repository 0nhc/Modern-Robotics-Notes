# Chapter 2
## 2.1 Degrees of Freedom of a Rigid Body
* C-space: The space of all configurations.
* Degrees of freedom (DoF): The dimension of the C-space.

In a n-dimensional space, there are $n$ translational degrees of freedom, and $\frac{n(n-1)}{2}$ rotational degrees.


## 2.2 Degrees of Freedom of a Robot
Some common types of joints:
* Revolute (R) Joint
    * Constraints: 5
    * Freedoms: 1
* Prismatic (P) Joint
    * Constraints: 5
    * Freedoms: 1
* Universal (U) Joint
    * Constraints: 4
    * Freedoms: 2
* Spherical (S) Joint
    * Constraints: 3
    * Freedoms: 3

Now we define:
* $N$ = number of bodies, including ground
* $J$ = number of joints
* $m$ = 6 for spatial bodies, 3 for planar

So we have Grubler's Formula:
$$
DoF = m(N-1-J)+\sum_{i=1}^Jf_i\\
f_i\ denotes\ joint\ freedoms
$$


## 2.3.1 Configuration Space Topology
* Space: $\R^2$
* Sphere: $S^2$
* 2R robot arm: $S^1\times S^1$
* Sliding rotation knob: $\R^1\times S^1$

Note that $S^2 \ne S^1\times S^1$ in topology. Instead, $T^2 = S^1\times S^1$.

The C-space of a rigid-body in 3D space is $\R^3\times S^2\times S^1$.


## 2.3.2 Configuration Space Representation
For a sphere:
* Explicit parametrization: minimum number of coordinates e.g. latitude, longitude.
* Implicit representation: a surface embedded in ahigher-dimensional space e.g. ($x$, $y$, $z$) such that $x^2+y^2+z^2=1$

The explicit representation is poor at the polar point of the sphere (singularity), thus the implicit representation is better.

An explicit parametrization uses fewer numbers to represent a configuration than an implicit representation because it directly captures the minimal set of independent parameters needed to uniquely define the configuration, eliminating any redundant information and constraints.


## 2.4 Configuration and Velocity Constraints
* Holonomic constraints: constraints on configuration
* Nonholonomic constraints: constraints on velocity
* Pfaffian constraints: $A(\theta)\dot{\theta} = 0$, will discuss whether it's holonomic or nonholonomic in Chapter 13


## 2.5 Task Space and Workspace
* Task Space: The space in which the robot's task is naturally expressed.
* Workspace: A specification of the reachable configurations of the end-effector.
