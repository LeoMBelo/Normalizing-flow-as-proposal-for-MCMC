# Normalizing flow as proposal for MCMC

This works comes from the final projected of the discipline Statistic Computation from FGV by the professor Luiz Max.

Normalizing flows (NF) offer a principled way to turn a simple latent distribution into an expressive density through a sequence of invertible, differentiable maps. Recent work shows that combining NFs with Markov‑chain Monte‑Carlo (MCMC) can accelerate convergence, especially in multimodal or high‑dimensional targets. We integrate a RealNVP flow with a Metropolis‑within‑Gibbs sampler: the chain evolves in the latent space $\mathcal{Z}$ while the flow transports proposals to the data space $\mathcal{X}$. Empirically, the method yields an order‑of‑magnitude improvement in effective sample size over a random‑walk Metropolis baseline on a ten‑dimensional, tri‑modal Gaussian mixture as done in the experiments, demonstrating that NF‑guided proposals can improve sampling efficiency.
