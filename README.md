# Interactive Bézier Curve with Physics & Sensor Control

## Objective
The goal of this assignment is to implement an **interactive cubic Bézier curve** that behaves like a **springy rope** and responds to real-time input. The project demonstrates understanding of **Bézier mathematics, vector calculus, spring-damping physics, and real-time rendering**.

This implementation is done **from scratch**, without using any built-in Bézier, animation, or physics libraries.

---

## Features Implemented
- Manual cubic Bézier curve computation
- Spring-damped control point motion
- Real-time mouse interaction
- Tangent vector visualization
- 60 FPS canvas rendering
- Clean separation of math, physics, input, and rendering logic

---

## Bézier Curve Mathematics

A **cubic Bézier curve** is defined using four control points:

- **P₀, P₃** → fixed endpoints  
- **P₁, P₂** → dynamic control points

The curve equation is:

\[
B(t) = (1 - t)^3 P_0 + 3(1 - t)^2 t P_1 + 3(1 - t)t^2 P_2 + t^3 P_3
\]

- `t ∈ [0, 1]`
- The curve is sampled at intervals of `0.01` to produce a smooth path.

---

## Tangent Computation

Tangents are calculated using the derivative of the cubic Bézier curve:

\[
B'(t) = 3(1 - t)^2(P_1 - P_0) + 6(1 - t)t(P_2 - P_1) + 3t^2(P_3 - P_2)
\]

- Tangents are **normalized**
- Short line segments are drawn at regular intervals along the curve
- This visualizes the direction and flow of the curve

---

## Spring Physics Model

To simulate rope-like behavior, control points **P₁ and P₂** follow a target position using a **spring-damping system**:

\[
\text{acceleration} = -k(x - x_{target}) - d \cdot v
\]

Where:
- `k` = spring stiffness
- `d` = damping coefficient
- `v` = velocity

This model ensures:
- Smooth motion
- Natural lag
- No sudden jumps or jitter

---

## Interaction Model (Web)

- Mouse movement controls the target positions of **P₁ and P₂**
- Endpoints **P₀ and P₃** remain fixed
- The curve responds smoothly in real time

---

## Rendering

The following elements are rendered on an HTML Canvas:
- Bézier curve path
- Control points (small circles)
- Tangent vectors along the curve

Rendering is done using `requestAnimationFrame` to maintain **~60 FPS**.

---

## Constraints Followed

- No Bézier utilities (`UIBezierPath`, `D3.js`, etc.)
- No physics or animation libraries
- All math and physics implemented manually
- Real-time interactivity required

---

## How to Run

1. Save the source file as `index.html`
2. Open it in any modern web browser
3. Move the mouse to interact with the curve

---

## Deliverables

- `index.html` — full source code
- `README.md` — explanation of math, physics, and design
- Screen recording (≤ 30 seconds) demonstrating interaction

---

## Author Notes

This project focuses on clarity, correctness, and real-time performance.  
The spring-based Bézier control system effectively simulates a rope-like response while remaining computationally lightweight.

---
