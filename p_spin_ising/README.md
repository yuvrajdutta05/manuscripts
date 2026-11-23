# Fluctuations in p-spin Ising Model

**Yuvraj Dutta and Sumit Mukherjee**

[Read the manuscript (PDF)](../p_spin_ising.pdf)

## Main results

We study the global magnetization of p-spin Ising models (`p >= 3`) with general symmetric, nonnegative interaction tensors and an external magnetic field, in a Dobrushin-type high-temperature regime. Let `t` be the unique solution of `t = tanh(β t^(p−1) + h)`, and let `α_N` quantify the pair marginal's mean-field and regularity errors, as defined in the paper.

1. **Gaussian fluctuations and Berry–Esseen bound (Theorem 1.2).** We obtain an explicit Kolmogorov-distance bound for `√N (m_N − t)` in terms of the interaction tensor's pair marginal. Under the paper's regularity conditions, the magnetization has the same limiting Gaussian law as the p-spin Curie–Weiss model, with variance
   `(1 − t²) / [1 − β(p−1)t^(p−2)(1−t²)]`.
   The optimal Curie–Weiss rate `O(N^(−1/2))` is recovered when the corresponding error terms are bounded.

2. **Concentration and law of large numbers (Theorem 1.1).** We prove the concentration bound
   `log P(|m_N − t| ≥ ε) ≤ C(1 + α_N) − N ε²/(4C)`.
   In particular, `α_N = o(N)` implies convergence of the magnetization to `t` in probability and in every fixed absolute moment.

3. **Comparison with a product measure (Theorem 1.3).** For an explicit product measure `Q` with spin mean `t`, we bound probabilities under the Gibbs measure in terms of probabilities under `Q`, with an additive `O(α_N)` error on the logarithmic scale.

4. **Mean-field free energy (Theorem 1.4).** For the explicit mean-field prediction `M_N` defined in the manuscript, we establish
   `0 ≤ log Z_N − M_N ≤ C α_N`.

All statements above are under the respective assumptions of the cited theorems; see the PDF for precise conditions and constants.
