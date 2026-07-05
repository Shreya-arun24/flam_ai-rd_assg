# flam_ai-rd_assg

Had to find theta, M and X for the curve equation given, using the xy_data.csv points.

## How I did it

I noticed the equations are basically just a rotation. If you take t and R(t) = e^(M|t|)*sin(0.3t) as a point, then x and y are just that point rotated by theta and shifted by X and 42.

So I did the opposite - rotated the given x,y points backwards by theta and subtracted X, 42. If theta and X are correct, this should give back t and R(t) exactly.

Used this to write a small least squares fit in MATLAB to find theta, M, X that make this work for all the points.

## Answer

theta = 0.523599 rad (30 deg)
M = 0.03
X = 55

Checked it by putting these back into the original equations and comparing to the csv data, error was basically 0 (~1e-5).

## Files

- flam_assg.mlx - the matlab live script
- xy_data.csv - given data

Run fit_curve.m with xy_data.csv in the same folder, it prints the theta, M, X values.

## Desmos

\left(t*\cos(0.523599)-e^{0.03\left|t\right|}\cdot\sin(0.3t)\sin(0.523599)+55,42+t*\sin(0.523599)+e^{0.03\left|t\right|}\cdot\sin(0.3t)\cos(0.523599)\right)

domain: 6 <= t <= 60

link for desmos: https://www.desmos.com/calculator/mhxxqeqgw0
