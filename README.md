# Interactive-B-zier-Curve-with-Physics-Sensor-Control
Implement an **interactive cubic Bézier curve** that behaves like a rope reacting to motion input.  This project tests your understanding of math, graphics programming, and real-time input handling

## Abstract

This project implements an interactive cubic Bézier curve that responds dynamically to real-time user input. The curve is modeled to behave like a flexible rope by combining parametric curve mathematics with a spring-damping motion model. All Bézier computations, tangent derivations, and motion dynamics are implemented manually without relying on built-in animation, physics, or curve libraries.

---

## Mathematical Model

A cubic Bézier curve is defined using four control points `P0`, `P1`, `P2`, and `P3`. The curve is evaluated using the parametric equation:
B(t) = (1 − t)^3 P0 + 3(1 − t)^2 t P1 + 3(1 − t) t^2 P2 + t^3 P3

where `t ∈ [0, 1]`. The curve is sampled at uniform intervals to generate the rendered path.

---

## Tangent Computation

The tangent vector at any point on the curve is obtained from the analytical derivative of the Bézier equation:

B'(t) = 3(1 − t)^2 (P1 − P0)
+ 6(1 − t)t (P2 − P1)
+ 3t^2 (P3 − P2)

The resulting tangent vectors are normalized and visualized at fixed intervals along the curve to illustrate local direction and continuity.

---

## Dynamic Control Point Behavior

The endpoints `P0` and `P3` remain fixed, while the intermediate control points `P1` and `P2` respond to user input. Their motion is governed by a spring-damping system defined as:

a = −k(x − x_target) − d · v

where:
- `k` is the spring stiffness
- `d` is the damping coefficient
- `v` is the current velocity

This model produces smooth, elastic motion and prevents abrupt changes in position.

---

## Interaction and Rendering

User interaction is handled through mouse input, which defines target positions for the dynamic control points. Rendering is performed using the HTML Canvas API and updated via `requestAnimationFrame` to ensure real-time responsiveness at approximately 60 FPS.

Each animation frame consists of:
1. Physics integration for control points  
2. Bézier curve evaluation  
3. Tangent vector computation  
4. Rendering of the curve, tangents, and control points  

---

## Implementation Constraints

- No built-in Bézier, animation, or physics libraries were used  
- All vector operations, curve evaluation, and motion logic were implemented manually  
- The system operates in real time with interactive input  

---

## Conclusion

This project demonstrates the integration of parametric curve mathematics, differential geometry, and basic physics simulation in an interactive graphics context. The implementation highlights how analytical models can be combined to produce smooth, physically plausible real-time visual behavior.


