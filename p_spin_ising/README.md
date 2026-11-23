# Fluctuations in p-spin Ising Model

**Yuvraj Dutta and Sumit Mukherjee**

[**Read the manuscript (PDF)**](../p_spin_ising.pdf)

> **Work in progress.** This manuscript is an evolving research draft and will be updated regularly as the results and exposition develop.

## Model

For $p\geq 3$, consider the $p$-spin Ising model on $\{-1,1\}^N$ given by

```math
\mathbb P_{\beta,h,p}(\boldsymbol\sigma)
=\frac{1}{Z_N(\beta,h,p)}
\exp\left\{
\frac{\beta}{p}\sum_{i_1,\ldots,i_p=1}^{N}
A_{i_1\cdots i_p}\sigma_{i_1}\cdots\sigma_{i_p}
+h\sum_{i=1}^{N}\sigma_i
\right\}.
```

Here $\boldsymbol A_N=(A_{i_1\cdots i_p})$ is a symmetric, entrywise nonnegative $p$-tensor whose entries vanish whenever two indices coincide, $\beta>0$ is the inverse temperature, and $h\in\mathbb R$ is the external magnetic field. We study the **global magnetization**

```math
\bar\sigma=\frac1N\sum_{i=1}^{N}\sigma_i.
```

Its mean-field centering $t\in(-1,1)$ is the unique solution to

```math
t=\tanh(\beta t^{p-1}+h)
```

in the parameter regime below.

## Assumptions and parameter regime

Let $\boldsymbol R=(R_{ij})$ be the pair marginal matrix of $\boldsymbol A_N$, and let $R_i$ denote its row sums:

```math
R_{ij}=\sum_{i_3,\ldots,i_p=1}^{N}A_{ij i_3\cdots i_p},
\qquad
R_i=\sum_{j=1}^N R_{ij}.
```

**Assumption (1.5).** There exists $\gamma\geq1$, independent of $N$, such that

```math
\sup_{N\geq1}\|\boldsymbol R_N\|_{\mathrm{op}}\leq\gamma.
```

**Parameter range (Definition 1.3).** The results hold in the Dobrushin-type high-temperature regime

```math
\Theta_p=\left\{(\beta,h):0<\beta<\frac{1}{(p-1)\gamma},\quad h\in\mathbb R\right\}.
```

Define the error functional (1.6)

```math
\alpha_N=\lVert\boldsymbol R\rVert_{\mathrm F}^2+
t^{2(p-2)}\sum_{i=1}^{N}(R_i-1)^2.
```

We use $a_N\lesssim b_N$ to mean $a_N\leq Cb_N$ for some constant $C$ independent of $N$, and $d_{\mathrm{KS}}$ denotes Kolmogorov–Smirnov distance.

## Main results

### Theorem 1.1 — Exponential concentration and law of large numbers

Suppose $(\beta,h)\in\Theta_p$ and $\boldsymbol A_N$ satisfies (1.5).

**(a)** There exists a constant $C>0$, free of $N$, such that for every $\varepsilon>0$,

```math
\log\mathbb P_{\beta,h,p}\bigl(|\bar\sigma-t|\geq\varepsilon\bigr)
\leq C(1+\alpha_N)-\frac{N\varepsilon^2}{4C}.
```

**(b)** For every $k\geq1$,

```math
\mathbb E|\bar\sigma-t|^k
\lesssim\left(\frac{1+\alpha_N}{N}\right)^{k/2},
```

where the implicit constant depends on $k$ but not on $N$. In particular, if $\alpha_N=o(N)$, then $\mathbb E|\bar\sigma-t|^k\to0$ for every $k\geq1$. Consequently, for every $\varepsilon>0$,

```math
\mathbb P_{\beta,h,p}(|\bar\sigma-t|>\varepsilon)\longrightarrow0
\quad\text{as }N\to\infty.
```

**Remark 1.1.** Theorem 1.1 requires only $\alpha_N=o(N)$, which is much weaker than the condition $\alpha_N+|t|^{p-1}\left|\sum_i(R_i-1)\right|=o(\sqrt N)$ under which Theorem 1.2 yields a central limit theorem. In particular, the bias term $\sum_i(R_i-1)$ plays no role at the level of the law of large numbers.

### Theorem 1.2 — Berry–Esseen bound and Gaussian fluctuations

Let $p\geq3$. Suppose $(\beta,h)\in\Theta_p$ and the interaction tensors $\boldsymbol A_N$ satisfy (1.5). If $\boldsymbol\sigma$ is a random vector from the $p$-spin Ising model, then

```math
d_{\mathrm{KS}}\left(\sqrt N(\bar\sigma-t),Z_N\right)
\lesssim\frac1{\sqrt N}
\left(
1+\alpha_N+|t|^{p-1}\left|\sum_{i=1}^{N}(R_i-1)\right|
\right)
```

where

```math
Z_N\sim\mathcal N\left(
0,\frac{1-t^2}{1-\beta(p-1)t^{p-2}(1-t^2)}
\right).
```

**Remark 1.2.** We make a few comments on Theorem 1.2.

**(i)** The right-hand side of (1.7) is explicit in terms of $\boldsymbol R$. In particular, $\sqrt N(\bar\sigma-t)$ converges in distribution to $\mathcal N(0,s^2)$, with

```math
s^2=\frac{1-t^2}{1-\beta(p-1)t^{p-2}(1-t^2)},
```

as soon as

```math
\lVert\boldsymbol R\rVert_{\mathrm F}^2+
t^{2(p-2)}\sum_{i=1}^{N}(R_i-1)^2+
|t|^{p-1}\left|\sum_{i=1}^{N}(R_i-1)\right|
=o(\sqrt N),
```

and the rate of convergence is $N^{-1/2}$ whenever the left-hand side is bounded. This is the same rate as in the Curie–Weiss model (Lemma 1.2).

**(ii)** The term $\lVert\boldsymbol R\rVert_{\mathrm F}^2$ quantifies how far the interaction is from being of mean-field type, while the terms involving $R_i-1$ quantify the deviation of $\boldsymbol A_N$ from regularity. If $\boldsymbol A_N$ is exactly regular, i.e. $R_i=1$ for all $i$, or there is no external magnetic field, i.e. $h=0$, only $\lVert\boldsymbol R\rVert_{\mathrm F}^2$ remains.

**(iii)** When $h=0$, the Gaussian variance appearing in Theorem 1.2 equals $1$ for $p\geq3$. Consequently, whenever the conditions ensuring convergence in Theorem 1.2 hold, the limiting variance agrees with that of independent symmetric spins. This contrasts with the case $p=2$, where the corresponding variance is $1/(1-\beta)$, reflecting the pairwise correlations.

**(iv)** For $p=2$, the analogous result was proved in [1, Theorem 1.1] throughout the uniqueness regime, which matches our regime $\Theta_p$ when $\gamma=1$.

### Theorem 1.3 — Comparison with a product measure

Let $\mathbb{Q}$ denote the product measure under which $\sigma_1,\ldots,\sigma_N$ are i.i.d. $\{-1,1\}$-valued random variables with mean $t$. Suppose $\boldsymbol A_N$ satisfies (1.5) and $(\beta,h)\in\Theta_p$. Fix $\theta\in(1,\Lambda)$, where

```math
\Lambda=\frac1{\beta\gamma(p-1)}.
```

Then there exists $C_\theta>0$, independent of $N$, such that for every nonempty event $\Omega_N\subseteq\{-1,1\}^N$,

```math
\log\mathbb P_{\beta,h,p}(\Omega_N)
\leq\left(1-\frac1\theta\right)\log \mathbb{Q}(\Omega_N)
+C_\theta\alpha_N.
```

Theorem 1.3 states that an event which is exponentially unlikely under the product measure $\mathbb{Q}$ remains exponentially unlikely under $\mathbb P_{\beta,h,p}$, up to an additive error of order $\alpha_N$ on the logarithmic scale. It is the $p$-spin analogue of [1, Theorem 1.6], and it follows from Lemma 2.1 by taking $f(\boldsymbol\sigma)=\mathbf1_{\Omega_N}$. Results of this type are useful for transferring concentration inequalities from product measures to the Gibbs measure.

### Theorem 1.4 — Mean-field approximation to the log-partition function

Define

```math
I(x)=\frac{1+x}{2}\log\left(\frac{1+x}{2}\right)
+\frac{1-x}{2}\log\left(\frac{1-x}{2}\right)
```

and the mean-field prediction (1.9)

```math
M_N(\beta,h,p)
=N\left[\frac{\beta}{p}t^p+ht-I(t)\right]
+\frac{\beta}{p}t^p\sum_{i=1}^N(R_i-1).
```

Suppose $\boldsymbol A_N$ satisfies (1.5) and $(\beta,h)\in\Theta_p$. Then

```math
0\leq\log Z_N(\beta,h,p)-M_N(\beta,h,p)\lesssim\alpha_N.
```

**Remark 1.3.** For $p=3$, the cubic tensor model of [4] with Rademacher base measure is equivalent to (1.1), since the Hamiltonian is

```math
\frac{\beta}{3}\sum_{i,j,k} A_{ijk}\sigma_i\sigma_j\sigma_k+h\sum_i\sigma_i
```

in both cases. For cubic models, [4, (9)] gives a quantitative bound on the log partition function in terms of the mean-field prediction formula, similar to Theorem 1.4. They prove it in [4, Theorem 1.10] under Assumption 1.2 and the mean-field condition (4). Below we demonstrate that barring the high temperature assumption, our conditions are weaker than [4] for mean-field prediction, for regular tensors.

**(i) Boundedness:** Assumption 1.2 requires

```math
\max_i\sum_{j,k} A_{ijk}\leq\gamma,
```

which implies

```math
\lVert\boldsymbol R\rVert_{\mathrm{op}}\leq\max_iR_i\leq\gamma.
```

Hence it implies our assumption (1.5), which only bounds the operator norm of $\boldsymbol R$. Our boundedness condition is therefore weaker.

**(ii) Mean-field condition:** Condition (4) requires

```math
\left\lVert\sum_i\boldsymbol A_i^2\right\rVert_{\mathrm{op}}=o(1/\log N),
```

where $\boldsymbol A_i=((A_{ijk}))_{j,k\in[N]}$. By [4, Lemma 3.4(a)], we get

```math
\operatorname{Tr}(\boldsymbol R^2)\leq N\left\lVert\sum_i\boldsymbol A_i^2\right\rVert_{\mathrm{op}},
```

so (4) implies that

```math
\lVert\boldsymbol R\rVert_{\mathrm F}^2=\operatorname{Tr}(\boldsymbol R^2)=o(N/\log N).
```

Theorem 1.4 yields an $o(N)$ approximation error whenever $\lVert\boldsymbol R\rVert_{\mathrm F}^2=o(N)$, so our condition is weaker. In general, only the one-sided inequality

```math
\operatorname{Tr}(\boldsymbol R^2)\leq N\left\lVert\sum_i\boldsymbol A_i^2\right\rVert_{\mathrm{op}}
```

is true. The two sides are known to be of the same order under the strong pseudo-regularity and non-degeneracy conditions (6)–(7) of [4]. We do not require (6)–(7). Even when they match, our condition is weaker by a logarithmic factor. When they fail,

```math
N\left\lVert\sum_i\boldsymbol A_i^2\right\rVert_{\mathrm{op}}
```

may be much larger in order than $\operatorname{Tr}(\boldsymbol R^2)$, so our condition can be significantly weaker than (4), not just by a logarithmic factor.

**(iii) Order of the tensor:** The results of [4] are specific to cubic interactions ($p=3$), whereas Theorem 1.4 holds for non-negative symmetric tensors of every order $p\geq3$.

**(iv) High temperature assumption:** Theorem 1.4 is proved for $(\beta,h)\in\Theta_p$. This regime is the contracting regime of Lemma 1.1 if $\gamma=1$ or otherwise, is contained within it. The bound [4, (9)] has no such restriction on $\beta$, and in this respect their result is more general. In our regime, the fixed-point equation admits a unique solution $t$, which provides an explicit homogeneous trial point for the variational problem. This yields the closed-form mean-field prediction $M_N$, whose approximation error is controlled by Theorem 1.4.

---

The labels and references above follow the [manuscript](../p_spin_ising.pdf); see its bibliography for references [1] and [4].
