# Entropic Matching for Filtering and Smoothing of Stochastic Differential Equations

**Yannick Eich, Yuvraj Dutta, and Heinz Koeppl**

[**Read the manuscript (PDF)**](../f%26s_sdes.pdf)

> **Work in progress.** This preprint is subject to revision; the manuscript and the results presented here may be updated.

## 1. Model and observation process

Let $(X_t)_{t\in[0,T]}$ be a latent diffusion in $\mathbb{R}^d$ satisfying

```math
dX_t=a(X_t)\,dt+S(X_t)\,dW_t,\qquad B(x)=S(x)S(x)^\top,
```

where $a:\mathbb{R}^d\to\mathbb{R}^d$ is the drift, $S:\mathbb{R}^d\to\mathbb{R}^{d\times m}$ is the diffusion coefficient, and $W_t$ is an $m$-dimensional Wiener process. The initial state has density $p_0$.

The state is observed indirectly at times $0<t_1<\cdots<t_N\leq T$ through conditionally independent observations with likelihood

```math
Y_i\mid X_{t_i}=x\sim p(y_i\mid x),\qquad
p(y_{1:N}\mid x_{1:N})=\prod_{i=1}^N p(y_i\mid x_i).
```

The likelihood need not be Gaussian or conjugate to the approximating distribution.

## 2. Filtering and smoothing

For $y_{[0,t]}=\{y_i:t_i\leq t\}$, **filtering** estimates the latent state using observations available *up to time* $t$, while **smoothing** uses the *entire* observation sequence:

```math
\pi_t(x)=p(X_t=x\mid y_{[0,t]}),\qquad
\widetilde\pi_t(x)=p(X_t=x\mid y_{1:N}).
```

These denote conditional **densities**. Between observation times, $\pi_t$ evolves according to the Fokker–Planck equation, and at observation time $t_i$ it undergoes the Bayesian update

```math
\partial_t\pi_t=L\pi_t,\qquad
\pi_{t_i}(x)\propto p(y_i\mid x)\,\pi_{t_i^-}(x).
```

Smoothing additionally incorporates future observations via a backward evolution with terminal condition $\widetilde\pi_T=\pi_T$. These density-valued evolutions are generally intractable for nonlinear SDEs.

**Existing framework (not a new result of this paper).** Entropic matching projects these density dynamics onto a finite-dimensional parametric family $q(x;\theta)$ by minimizing a local Kullback–Leibler divergence. The resulting filtering equation (Eq. 9) is

```math
\frac{d\theta_t}{dt}
=F(\theta_t)^{-1}\mathbb E_{q_t}
\left[L^\dagger\nabla_{\theta_t}\log q(X;\theta_t)\right],
```

with $F$ the Fisher information matrix and $L^\dagger$ the diffusion generator; the corresponding existing smoothing projection is given in Eq. 10. Our contribution is to **instantiate and extend this framework for positive-support, non-Gaussian approximating families**, with tractable equations and non-conjugate observation updates.

## 3. Main contributions and results

### Lognormal filtering and smoothing (Eqs. 11–14)

We derive parameter dynamics for multivariate lognormal approximate marginals,

```math
q_t=\mathrm{Lognorm}(\mu_t,\Sigma_t),\qquad
\widetilde q_t=\mathrm{Lognorm}(\widetilde\mu_t,\widetilde\Sigma_t).
```

Writing $\widehat a_i(x)=a_i(x)/x_i-B_{ii}(x)/(2x_i^2)$ and $\widehat B_{ij}(x)=B_{ij}(x)/(x_i x_j)$, the filtering equations are

```math
\frac{d\mu_t}{dt}=\mathbb E_{q_t}[\widehat a(X)],
```

\frac{d\Sigma_t}{dt}
=\mathbb E_{q_t}\!\left[
\mathrm{sym}\!\left(\widehat a(X)(\log X-\mu_t)^\top\right)
+\widehat B(X)\right],
```

where $\mathrm{sym}(M)=M+M^\top$. We also obtain the corresponding backward smoothing equations for $(\widetilde\mu_t,\widetilde\Sigma_t)$ (Eqs. 13–14), expressed in terms of the filtering parameters and the diffusion coefficients.

### Gamma filtering and smoothing (Eqs. 15–16)

For the positive-support product family

```math
q_t(x)=\prod_{i=1}^d\mathrm{Gam}(x_i;\alpha_{t,i},\beta_{t,i}),
```

we derive coupled parameter ODEs for filtering and smoothing. In particular, for $\theta_{t,i}=(\alpha_{t,i},\beta_{t,i})^\top$, the filtering dynamics are

```math
\frac{d\theta_{t,i}}{dt}
=F(\theta_{t,i})^{-1}\mathbb E_{q_t}
\begin{bmatrix}
a_i(X)/X_i-B_{ii}(X)/(2X_i^2)\\
-a_i(X)
\end{bmatrix}.
```

The corresponding smoothing dynamics are given in Eq. 16. For broad classes of SDEs, including models with power-law drift and diffusion, the expectations yield closed-form ODE right-hand sides. The gamma product approximation does not directly represent posterior cross-correlations.

### Non-conjugate observations (Section 5.2)

We combine the derived non-Gaussian filters and smoothers with **expectation propagation (EP)** to update observation-site approximations when $p(y_i\mid x)$ is non-conjugate. EP itself is an established method; its use here enables the proposed lognormal and gamma SDE approximations to handle more general observation models.

### Numerical findings (Section 6)

We compare the lognormal and gamma smoothers with a sequential Monte Carlo reference using $10^4$ particles. Performance is measured by mean squared error in posterior quantiles across benchmark SDEs and Gaussian, Poisson, and lognormal observation models.

- **Cox–Ingersoll–Ross and logistic Feller:** gamma achieves lower posterior-quantile errors in the reported configurations.
- **Constant elasticity of variance (CEV):** lognormal achieves lower errors in the reported configurations.

These results indicate that choosing the approximation family to reflect the diffusion structure can improve posterior inference. The experiments do not include a direct Gaussian assumed-density smoothing baseline.

---

Full derivations, assumptions, and numerical results appear in the [manuscript](../f%26s_sdes.pdf).
