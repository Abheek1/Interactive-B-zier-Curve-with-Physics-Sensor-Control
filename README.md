# Interactive-B-zier-Curve-with-Physics-Sensor-Control
Implement an **interactive cubic Bézier curve** that behaves like a rope reacting to motion input.  This project tests your understanding of math, graphics programming, and real-time input handling
Abstract

This project presents an interactive simulation of a cubic Bézier curve that responds dynamically to real-time user input. The system models the curve as a flexible rope by combining parametric curve mathematics with a spring-damping motion model. All computations, including Bézier evaluation, tangent derivation, and physics integration, are implemented manually without relying on prebuilt libraries.

Mathematical Model

A cubic Bézier curve is defined using four control points 
𝑃
0
,
𝑃
1
,
𝑃
2
,
𝑃
3
P
0
	​

,P
1
	​

,P
2
	​

,P
3
	​

 and evaluated as:

𝐵
(
𝑡
)
=
(
1
−
𝑡
)
3
𝑃
0
+
3
(
1
−
𝑡
)
2
𝑡
𝑃
1
+
3
(
1
−
𝑡
)
𝑡
2
𝑃
2
+
𝑡
3
𝑃
3
,
𝑡
∈
[
0
,
1
]
B(t)=(1−t)
3
P
0
	​

+3(1−t)
2
tP
1
	​

+3(1−t)t
2
P
2
	​

+t
3
P
3
	​

,t∈[0,1]

The curve is sampled at uniform intervals to generate the rendered path.

The tangent vector at any point on the curve is obtained from the analytical derivative:

𝐵
′
(
𝑡
)
=
3
(
1
−
𝑡
)
2
(
𝑃
1
−
𝑃
0
)
+
6
(
1
−
𝑡
)
𝑡
(
𝑃
2
−
𝑃
1
)
+
3
𝑡
2
(
𝑃
3
−
𝑃
2
)
B
′
(t)=3(1−t)
2
(P
1
	​

−P
0
	​

)+6(1−t)t(P
2
	​

−P
1
	​

)+3t
2
(P
3
	​

−P
2
	​

)

Normalized tangent vectors are visualized to illustrate local curve direction.

Dynamic Control Point Behavior

The endpoints 
𝑃
0
P
0
	​

 and 
𝑃
3
P
3
	​

 remain fixed, while intermediate control points 
𝑃
1
P
1
	​

 and 
𝑃
2
P
2
	​

 respond to user input. Their motion is governed by a spring-damping system:

𝑎
=
−
𝑘
(
𝑥
−
𝑥
𝑡
𝑎
𝑟
𝑔
𝑒
𝑡
)
−
𝑑
⋅
𝑣
a=−k(x−x
target
	​

)−d⋅v

where 
𝑘
k is the stiffness constant, 
𝑑
d is the damping factor, and 
𝑣
v is velocity. This model produces smooth, physically plausible motion with elastic characteristics.

Interaction and Rendering

User interaction is handled through mouse input, which defines target positions for the dynamic control points. Rendering is performed using the HTML Canvas API and updated via requestAnimationFrame to maintain real-time responsiveness at approximately 60 FPS.

Each frame consists of:

Physics integration of control points

Bézier curve evaluation

Tangent vector computation

Rendering of the curve, tangents, and control points

Implementation Constraints

No built-in Bézier, animation, or physics libraries were used

All vector operations, curve evaluation, and motion logic were implemented manually

The system operates in real time with interactive input

Conclusion

This implementation demonstrates the integration of parametric curve mathematics, differential geometry, and basic physics simulation in an interactive graphics context. The project highlights how analytical models can be effectively combined to produce smooth, real-time visual behavior.
