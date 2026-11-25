# Brownian Motion with Drift Conditioned to Have Restricted L²-Norm

**Frank Aurzada, Yuvraj Dutta, and Max Wiegand**

**Status:** arXiv preprint (arXiv:2610.12354)

[**arXiv abstract and preprint**](https://arxiv.org/abs/2610.12354) · [arXiv PDF](https://arxiv.org/pdf/2610.12354) · [Local manuscript copy (PDF)](../bm_withdrift_cond_l2.pdf) *(upload pending)*

## Model and conditioning

Let $(B_t)_{t\geq0}$ be a standard Brownian motion and consider Brownian motion with drift $\mu=\mu(T)$ starting at $x$:

```math
W_t=B_t+\mu t+x,\qquad
Z_T=\int_0^T W_s^2\,ds.
```

For fixed $\theta>0$, we study the long-time conditional path law given the rare event $Z_T\leq\theta T$, allowing the drift to depend on the time horizon $T$.

The quadratic functional has expectation

```math
\mathbb E_x[Z_T]
=\frac{\mu^2T^3}{3}
+\left(\mu x+\frac12\right)T^2+x^2T.
```

By Brownian scaling, the conditioning is equivalent in distribution to a non-centred small-ball problem with a shrinking radius and a time-dependent centre:

```math
\left\lVert B+\mu\sqrt{T}\,(\cdot)+\frac{x}{\sqrt{T}}\right\rVert_{L^2[0,1]}
\leq\sqrt{\frac{\theta}{T}}.
```

## Main results

### Theorem 1 — Ornstein–Uhlenbeck limit under deterministic conditioning

Fix $x\in\mathbb R$ and $\theta>0$. Suppose there exist $M>0$ and $\beta<1/2$ such that, for all sufficiently large $T$,

```math
\mu^2\leq MT^\beta.
```

Then, as $T\to\infty$, the conditional probability measures

```math
\mathbb P_x\big((W_t)_{t\geq0}\in\cdot\mid Z_T\leq\theta T\big)
```

converge weakly on $C([0,\infty))$ to the law of the Ornstein–Uhlenbeck process satisfying

```math
X_0=x,\qquad dX_t=dB_t-\frac{X_t}{2\theta}\,dt,\qquad t\geq0.
```

In particular, the limiting dynamics are independent of the original drift, even when that drift depends on the conditioning horizon.

### Theorem 2 — Sharp small-deviation asymptotics

Fix $\theta>0$. Let $x=x(T)$, $y=y(T)$ and $\mu=\mu(T)$ satisfy

```math
\mu^2+x^2\leq MT^\beta,\qquad
|y-\theta T|\leq KT^\beta
```

for some $M,K>0$, $\beta<1/2$, and all sufficiently large $T$. Then, as $T\to\infty$,

```math
\mathbb P_x(Z_T\leq y)
\sim \frac{4\sqrt y}{\sqrt\pi\,T}
\exp\left(
-\frac{(T+x^2)^2}{8y}
-\frac{\mu^2T}{2}
-\mu x+\frac{\mu^2y}{T}
\right).
```

The approximation includes the exact prefactor and is uniform over the admissible parameter range for fixed $M,K,\beta,\theta$ (Theorem 2′). Although the small-deviation probabilities depend explicitly on the original drift, the limiting conditioned path law in Theorem 1 does not.

### Theorem 3 — Ornstein–Uhlenbeck limit under exponential randomization

Fix $x\in\mathbb R$ and $\gamma>0$. Let $\eta$ be an exponential random variable independent of $W$, with mean $2/\gamma^2$. Suppose

```math
|\mu|e^{-\gamma T}\longrightarrow0.
```

Then, as $T\to\infty$, the conditional probability measures

```math
\mathbb P_x\big((W_t)_{t\geq0}\in\cdot\mid Z_T\leq\eta\big)
```

converge weakly on $C([0,\infty))$ to the law of the Ornstein–Uhlenbeck process

```math
Y_0=x,\qquad dY_t=dB_t-\gamma Y_t\,dt,\qquad t\geq0.
```

This randomized conditioning is equivalent to conditioning on survival up to time $T$ under quadratic killing with rate $\gamma^2 x^2/2$. The limiting dynamics remain independent of the original drift under the stated condition, which even permits certain exponentially growing drifts.

---

For the precise statements, discussion of the drift regimes, and full proofs, see the [arXiv preprint](https://arxiv.org/abs/2610.12354).
