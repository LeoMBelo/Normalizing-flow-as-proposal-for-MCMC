# Normalizing flow as proposal for MCMC

This works comes from the final projected of the discipline Statistic Computation from FGV by the professor Luiz Max.

Normalizing flows (NF) offer a principled way to turn a simple latent distribution into an expressive density through a sequence of invertible, differentiable maps. Recent work shows that combining NFs with Markov‑chain Monte‑Carlo (MCMC) can accelerate convergence, especially in multimodal or high‑dimensional targets. We integrate a RealNVP flow with a Metropolis‑within‑Gibbs sampler: the chain evolves in the latent space $\mathcal{Z}$ while the flow transports proposals to the data space $\mathcal{X}$. Empirically, the method yields an order‑of‑magnitude improvement in effective sample size over a random‑walk Metropolis baseline on a ten‑dimensional, tri‑modal Gaussian mixture as done in the experiments, demonstrating that NF‑guided proposals can improve sampling efficiency.

The method was applied in two datasets: 3 mixture of Gaussian (d = 10, d=20) and Adult Income (d=50).

## Next step
After the necessaries improvements, the next step is **Implement flow-based SMC for a high-dimensional non-linear state-space model**. I tried to target this problem, but i couldn't achieve the desired results. One problem, for example, that I selected was the dynamic $x_t = tanh(A x_{t-1}) + \epsilon_t, y_t = C x_t + \eta_t$.
The algorithm, with better results, that tried was:
X is latent and Y is the observed data
1. Use MCMC adaptative to obtain a candidate for posterior distribution X|Y by the collection of $\{x_t,w_t\}$, i.e., the $x_t$ would be sorted proportional to your $w_t$.
2. Normalizing Flow will train a $T_\theta: Z \to X$ (with $Z \sim N(0,I)$)
3. Use SMC with the transformation of normalizing flow as proposal
In low dimension, the results were good, but in high dimension the problems started.
