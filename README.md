# FLAM_Research_and_development
Assignment for Research and Development / AI

1. Problem Overview

We are given the following parametric equations describing a curve:

x = t · cos(θ) − e^(M|t|) · sin(0.3t) · sin(θ) + X
y = 42 + t · sin(θ) + e^(M|t|) · sin(0.3t) · cos(θ)

Unknown parameters to determine:

θ : Angle in degrees (0° < θ < 50°)

M : Exponential growth or decay rate (−0.05 < M < 0.05)

X : X-offset (0 < X < 100)

Given data:

xy_data.csv file containing (x, y) points

Corresponding t values are uniformly spaced within 6 < t < 60

Goal:
Find θ, M, and X so that the predicted curve best matches the observed data with the smallest L1 error (sum of absolute differences).

2. Intuitive Understanding of the Curve

The curve behaves like a slightly oscillating or spiraling line extending from a base point.

The main component, t·(cosθ, sinθ), defines a straight line in direction θ, starting from (X, 42).

The oscillation term, sin(0.3t), creates a gentle periodic wiggle along this path.

The exponential term, e^(M|t|), causes the wiggle to either grow or shrink as t increases.

M > 0 : outward spiral (amplitude increases)

M < 0 : inward spiral (amplitude decreases)

3. Step-by-Step Solution Approach

Step 1 – Identify the Main Direction
For large t, the oscillation is small, so:
x ≈ t · cosθ + X
y − 42 ≈ t · sinθ
Plotting (x, y−42) should give an almost straight line.
From this line:

Slope gives tanθ → estimate θ.

X-intercept gives approximate X.

Step 2 – Estimate the Parameter t
Using the estimated θ:
t ≈ (y − 42) / sin(θ)
This gives a rough t value for each point.
Since t values are uniformly spaced, the range [t_min, t_max] can be used to define a uniform grid.

Step 3 – Refine Parameters
Compute predicted (x, y) using full equations for each candidate θ, M, X.
Then calculate the L1 error as the sum of absolute differences between observed and predicted coordinates.
A bounded optimization algorithm adjusts θ, M, and X until L1 is minimized.

4. Final Results

θ = 24.873°
M = 0.003214
X = 59.982
L1 Error = 182.4
<img width="1217" height="738" alt="image" src="https://github.com/user-attachments/assets/078c7e5c-a04a-4cde-ae6c-44740fe1e3ca" />

