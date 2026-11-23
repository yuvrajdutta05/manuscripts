# Entropic Matching for Filtering and Smoothing of Stochastic Differential Equations

**Yannick Eich, Yuvraj Dutta, and Heinz Koeppl**

[**Read the manuscript (PDF)**](../f%26s_sdes.pdf)

> **Work in progress.** This preprint may be revised as the research and exposition develop. The linked PDF may be updated.

## Model and inference setting

We consider a latent diffusion $X_t\in\mathbb{R}^d$ governed by

```math
dX_t=a(X_t)\,dt+S(X_t)\,dW_t,\qquad B(x)=S(x)S(x)^\top,
```

with observations at discrete times $t_1,\ldots,t_N$, following a general likelihood $p(y_i\mid X_{t_i})$. The goal is to approximate the **filtering** distribution (conditioning on observations up to time $t$) and **smoothing** distribution (conditioning on the full observation sequence).

Exact filtering and smoothing generally require evolving intractable probability densities. We instead represent them by parametric families with time-varying parameters.

## Main contributions

### 1. Entropic-matching filtering and smoothing equations (Section 5.1)

Projecting the evolution of the filtering distribution onto a parametric family $q(x;\theta_t)$ leads to the finite-dimensional parameter equation

```math
\frac{d\theta_t}{dt}
=F(\theta_t)^{-1}\,
\mathbb{E}_{q_t}\!\left[L^\dagger\nabla_{\theta_t}\log q_t(X;\theta_t)\right],
```

where $F$ is the Fisher information matrix and $L^\dagger$ is the diffusion generator. An analogous equation for smoothing parameters uses the backward smoothing operator and is solved with a terminal condition (Eq. 10).

### 2. Lognormal and gamma approximations (Section 5.3)

We derive **filtering and smoothing parameter dynamics** for two non-Gaussian assumed-density families:

- **Multivariate lognormal:** preserves positivity, accommodates skewness, and is well matched to multiplicative-noise systems (Eqs. 11–14).
- **Product gamma:** preserves positivity and is well suited to square-root diffusion models (Eqs. 15–16).

For broad classes of SDEs, including power-law drift and diffusion coefficients, the resulting ordinary differential equations have **closed-form right-hand sides**. The product gamma family does not explicitly capture posterior correlations.

### 3. Non-conjugate observations (Section 5.2)

We incorporate **expectation propagation** to iteratively refine observation updates when the likelihood and approximating family are not conjugate. This extends the approach beyond settings with analytically tractable Bayesian updates.

### 4. Numerical results (Section 6)

We compare the approximations with a **sequential Monte Carlo smoother using 10,000 particles** on benchmark systems from finance and population biology, evaluating posterior-quantile accuracy.

- **Cox–Ingersoll–Ross and logistic Feller models:** the gamma approximation yields lower posterior-quantile errors than the lognormal approximation across the tested observation settings.
- **Constant elasticity of variance (CEV) model:** the lognormal approximation yields lower errors across the tested settings.

The results illustrate how choosing an approximation family aligned with the diffusion structure can improve inference accuracy. The numerical comparison is between the lognormal and gamma methods and the SMC reference; it does not directly benchmark a Gaussian assumed-density smoother.

---

For full assumptions, derivations, numerical settings, and additional experiments, see the [paper](../f%26s_sdes.pdf).
