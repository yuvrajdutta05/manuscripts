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

**Entropic-matching framework.** Entropic matching projects these density dynamics onto a finite-dimensional parametric family $q(x;\theta)$ by minimizing a local Kullback–Leibler divergence. The resulting filtering equation (Eq. 9) is

```math
\frac{d\theta_t}{dt}
=F(\theta_t)^{-1}\mathbb E_{q_t}
\left[L^\dagger\nabla_{\theta_t}\log q(X;\theta_t)\right],
```

Here $F(\theta_t)$ is the Fisher information matrix and $L^\dagger$ is the infinitesimal generator of the diffusion. The corresponding **smoothing entropic-matching equation** (Eq. 10) is

```math
\frac{d\widetilde{\theta}_t}{dt}
=F(\widetilde{\theta}_t)^{-1}
\mathbb{E}_{\widetilde{q}_t}
\left[
\widetilde{L}_t^\dagger
\nabla_{\widetilde{\theta}_t}
\log\widetilde{q}_t(X;\widetilde{\theta}_t)
\right],
```

with terminal condition

```math
\widetilde{\theta}_T=\theta_T.
```

Here $\widetilde{L}_t^\dagger$ denotes the adjoint of the backward smoothing operator, which depends on the filtering distribution. These general entropic-matching equations provide the starting point for our **lognormal and gamma filtering and smoothing approximations**, and for incorporating non-conjugate observation updates.

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

```math
\frac{d\Sigma_t}{dt}
=\mathbb E_{q_t}\!\left[
\mathrm{sym}\!\left(\widehat a(X)(\log X-\mu_t)^\top\right)
+\widehat B(X)\right],
```

where $\mathrm{sym}(M)=M+M^\top$. For smoothing, define

```math
\overline B_n(x)=-\widehat B_{nn}(x)
+\sum_{m=1}^d\frac{1}{x_n}\frac{\partial B_{nm}(x)}{\partial x_m}
-\sum_{m=1}^d\widehat B_{nm}(x).
```

The corresponding **backward smoothing equations** (Eqs. 13–14) are

```math
\frac{d\widetilde\mu_t}{dt}
=\mathbb E_{\widetilde q_t}
\left[\widehat a(X)-\overline B(X)
+\widehat B(X)\Sigma_t^{-1}(\log X-\mu_t)\right],
```

and

```math
\frac{d\widetilde\Sigma_t}{dt}
=\mathbb E_{\widetilde q_t}\left[
\mathrm{sym}\left(
\left(\widehat a(X)-\overline B(X)
+\widehat B(X)\Sigma_t^{-1}(\log X-\mu_t)\right)
(\log X-\widetilde\mu_t)^\top
\right)-\widehat B(X)\right].
```

These smoothing dynamics depend on the filtering parameters and are integrated backward in time with terminal conditions

```math
\widetilde{\mu}_T=\mu_T,\qquad \widetilde{\Sigma}_T=\Sigma_T.
```

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

For the **gamma smoothing equations** (Eq. 16), write

```math
\widetilde q_t(x)=\prod_{i=1}^d
\mathrm{Gam}(x_i;\widetilde\alpha_{t,i},\widetilde\beta_{t,i}),
\qquad
\widetilde\theta_{t,i}=
(\widetilde\alpha_{t,i},\widetilde\beta_{t,i})^\top,
```

and define the filtering score

```math
s_{t,m}(x)=\frac{\alpha_{t,m}-1}{x_m}-\beta_{t,m}.
```

The backward evolution of each smoothing parameter block is

```math
\frac{d\widetilde\theta_{t,i}}{dt}
=F(\widetilde\theta_{t,i})^{-1}
\mathbb E_{\widetilde q_t}
\begin{bmatrix}
g_{t,i}^{(1)}(X)\\
g_{t,i}^{(2)}(X)
\end{bmatrix},
```

where

```math
g_{t,i}^{(1)}(x)
=\frac{a_i(x)}{x_i}+\frac{B_{ii}(x)}{2x_i^2}
-\sum_{m=1}^d\frac{1}{x_i}
\frac{\partial B_{im}(x)}{\partial x_m}
-\sum_{m=1}^d\frac{B_{im}(x)}{x_i}s_{t,m}(x),
```

and

```math
g_{t,i}^{(2)}(x)
=-a_i(x)+\sum_{m=1}^d
\frac{\partial B_{im}(x)}{\partial x_m}
+\sum_{m=1}^d B_{im}(x)s_{t,m}(x).
```

Here $F$ is the gamma-family Fisher information matrix and the terminal condition is $\widetilde\theta_{T,i}=\theta_{T,i}$. For broad classes of SDEs, including models with power-law drift and diffusion, the expectations yield closed-form ODE right-hand sides. The gamma product approximation does not directly represent posterior cross-correlations.

### Non-conjugate observations (Section 5.2)

We combine the derived non-Gaussian filters and smoothers with **expectation propagation (EP)** to update observation-site approximations when $p(y_i\mid x)$ is non-conjugate. EP itself is an established method; its use here enables the proposed lognormal and gamma SDE approximations to handle more general observation models.

### Numerical findings (Section 6)

We compare the lognormal and gamma smoothers with a sequential Monte Carlo reference using $10^4$ particles. Performance is measured by mean squared error in posterior quantiles across benchmark SDEs and Gaussian, Poisson, and lognormal observation models.

- **Cox–Ingersoll–Ross and logistic Feller:** gamma achieves lower posterior-quantile errors in the reported configurations.
- **Constant elasticity of variance (CEV):** lognormal achieves lower errors in the reported configurations.

These results indicate that choosing the approximation family to reflect the diffusion structure can improve posterior inference. The experiments do not include a direct Gaussian assumed-density smoothing baseline.

---

Full derivations, assumptions, and numerical results appear in the [manuscript](../f%26s_sdes.pdf).
