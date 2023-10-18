## Developments in Kalman Filtering with Applications in Finance}

1. Wencheng Bao, Graduate student, Department of Applied Math and Applied Physics, Columbia University, email{wb2395@columbia.edu}
2. Kaiwen Zhang, Undergraduate student, Department of Applied Math and Applied Physics, Columbia University, email{kz2387@columbia.edu} 
3. David Feng, Graduate student, Department of Applied Math and Applied Physics, Columbia University, email{sf3164@columbia.edu}

### Research Problem

In financial markets, certain traits, like the partial randomness of stock prices, deviate from pure Brownian motion. Influenced by various factors, stock prices can sometimes display overarching trends, a phenomenon termed as 'financial inertia'. We can attribute the randomness in financial sequences to measurement noise. By integrating pertinent financial models, we can employ Kalman filtering to discern the underlying price trend amidst the noise.

This article delves into the diverse applications of Kalman filtering techniques to address random volatility. By leveraging various Kalman filter forms, we aim to enhance the estimation and smoothing of parameters within classic stochastic volatility models. Our analysis will be underpinned by data from the S&P 500, spanning from January 1, 2022, to January 1, 2023

### Basic Technique for Kalman Filtering

The Kalman Filter (KF) is primarily employed in linear stochastic systems to optimally estimate the system state from measured outputs tainted with random noise. This optimization is defined in terms of minimizing the mean squared errors (MSE). With its wide-ranging applications, the KF offers real-time optimal state estimation for finite-dimensional stochastic systems. Its primary utilities lie in state estimation and the performance analysis of estimation systems.

While the traditional KF is designed primarily for linear systems, there are adaptations for nonlinear systems, such as the Extended Kalman Filter (EKF). The EKF has become the standard for nonlinear system state estimation once the state transition equation is established. It tackles nonlinearities by utilizing Taylor expansion to compute the Jacobian matrix of the nonlinear functions. In the context of KF, nonlinear challenges typically arise in both prediction and observation processes, and the Jacobian matrix is computed separately for each, serving as the prediction and observation matrices.

Alternatively, we might try to simulate with an Unscented Kalman Filter(UKF). The UKF offers a solution to nonlinear Kalman filtering by employing the Unscented Transform. Unlike the EKF, which necessitates Jacobian matrix calculations, the UKF delivers superior accuracy in nonlinear processing while maintaining a comparable computational complexity.

### Basic Model for Finance

The Heston model is a popular mathematical model used to describe the evolution of volatility in financial markets. Heston model assumes that $S_t$, the price of the asset, is determined by a stochastic process
$
d S_t=\mu S_t d t+\sqrt{\nu_t} S_t d W_t^S
$
where $\nu_t$, the instantaneous variance, is given by a Feller square-root or CIR process,
$
d \nu_t=\kappa\left(\theta-\nu_t\right) d t+\xi \sqrt{\nu_t} d W_t^\nu
$
and $W_t^S, W_t^\nu$ are Wiener processes with correlation $\rho$.
The model has five parameters:
- $\nu_0$, the initial variance.
- $\theta$, the long variance, or long-run average variance of the price; as $t$ tends to infinity, the expected value of $v_t$ tends to $\theta$.
- $\rho$, the correlation of the two Wiener processes.
- $\kappa$, the rate at which $v_t$ reverts to $\theta$.
- $\xi$, the volatility of the volatility, or 'vol of vol', which determines the variance of $\mathrm{v}_t$.\\
If the parameters obey the following condition (known as the Feller condition) then the process $\nu_t$ is strictly positive $2 \kappa \theta>\xi^2 \text {. }$
If time allows,  We are trying to combine the Heston-Nandi with relative Kalman Filtering under GARCH(1,1):
$
\begin{aligned}
& \log (\mathrm{S}(\mathrm{t}))=\log (\mathrm{S}(\mathrm{t}-\Delta))+\mathrm{r}+\lambda \mathrm{h}(\mathrm{t})+\sqrt{\mathrm{h}(\mathrm{t})} \mathrm{z}(\mathrm{t}) 
& \mathrm{h}(\mathrm{t})=\omega+\sum_{\mathrm{i}=1}^{\mathrm{p}} \beta_{\mathrm{i}} \mathrm{h}(\mathrm{t}-\mathrm{i} \Delta)+\sum_{\mathrm{i}=1}^{\mathrm{q}} \alpha_{\mathrm{i}}\left(\mathrm{z}(\mathrm{t}-\mathrm{i} \Delta)-\gamma_{\mathrm{i}} \sqrt{\mathrm{h}(\mathrm{t}-\mathrm{i} \Delta)}\right)^2,
\end{aligned}
$

