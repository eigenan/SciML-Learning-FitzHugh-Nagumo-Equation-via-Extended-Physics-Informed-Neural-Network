# Learning FitzHugh Nagumo Equation via Extended Physics Informed Neural Network (XPINN)

This notebook solves the Fitzhugh-Nagumo equations and compares a Extended Physics-Informed Neural Network (XPINN) solution to a traditional Finite Difference Method (FDM) solution.

$$
\begin{aligned}
\frac{dv}{dt} &= v - \frac{v^3}{3} - w + I_{ext} \\
\frac{dw}{dt} &= \frac{1}{\tau} (v + a - b w)
\end{aligned}
$$

This equation has two time scales (fast/slow) that hinders the training of ordinary PINN because the model needs higher "resolution" near the fast time scale. To address the issue of different time scales (stiffness) in the Fitzhugh-Nagumo equations, we can use a **time-marching** or **domain decomposition** approach. Instead of using a single neural network for the entire time domain, we divide the domain into smaller, sequential windows.

A separate, smaller PINN is trained for each window. The initial condition for each window is the final state predicted by the PINN from the previous window. This allows each network to focus on learning the dynamics over a shorter, simpler time horizon, which can significantly improve accuracy for stiff ODEs.

Inspired by the paper: [Extended Physics-Informed Neural Networks (XPINNs): A Generalized Space-Time Domain Decomposition Based Deep Learning Framework for Nonlinear Partial Differential Equations](https://doi.org/10.4208/cicp.OA-2020-0164)

<img width="1012" height="547" alt="fn_output1" src="https://github.com/user-attachments/assets/66fedfac-cec6-496e-9ed9-4ab1d4bb4a1c" />

<img width="1021" height="547" alt="fn_output2" src="https://github.com/user-attachments/assets/bc446e1b-51a6-4e6e-91bd-249dc558a942" />

<img width="714" height="701" alt="fn_output3" src="https://github.com/user-attachments/assets/15e61c83-6349-40e8-8ba0-578ad5d0a6b8" />

<img width="1012" height="547" alt="fn_output4" src="https://github.com/user-attachments/assets/c02a90fb-f71f-444a-9739-e9e12c7ac131" />

<img width="1012" height="547" alt="fn_output5" src="https://github.com/user-attachments/assets/2e8cc427-c0ce-40f7-bd4f-d44025ef40dd" />
