# Practical 12 - Metropolis Algorithm and Fitting a Deterministic Model

| | |
|---|---|
| **Submitted By** | Tushar Sinsinbar |
| **Roll No** | GF202453725 |
| **Course** | B.Tech CSE (Data Science) |
| **Semester** | 5th Semester |
| **Subject** | Statistical Foundation of Data Science (CSU1658) |
| **Submitted To** | Anitya Gupta Sir |

---

## 1. Objective

The practical has two parts:

- **Part A:** Implement the **Metropolis algorithm** and see how its step size affects how well it samples a target distribution.
- **Part B:** Use a **deterministic model** (logistic growth) to generate noisy data, then use the Metropolis algorithm to recover the model's unknown parameters from that data.

---

## 2. Data and Models Used

- **Part A target:** A mixture of two Gaussian (normal) distributions, 30% centred at -2 (standard deviation 0.7) and 70% centred at 3 (standard deviation 1.2). It has two peaks (bimodal).
- **Part B model:** The **logistic growth model**, where a population N grows towards a carrying capacity K at rate r. True values used: r = 0.8, K = 100, starting population N0 = 5.
- **Part B data:** 16 simulated observations of the true curve with Gaussian noise (standard deviation 4).

---

## 3. Methodology

**Part A: Metropolis algorithm**

1. Implemented the Metropolis sampler: propose a new point from a symmetric random step, then accept it with probability min(1, new density / current density). Only density ratios are needed, so the normalising constant does not matter.
2. Ran 50,000 steps (first 5,000 dropped as burn-in) with step size 2.5 and compared the samples with the true density.
3. Tested three step sizes (0.1, 2.5 and 25), comparing trace plots, acceptance rate and autocorrelation.

**Part B: Deterministic model**

4. Simulated the logistic growth equation numerically with `solve_ivp` and compared it with the exact analytic solution. Re-ran it to confirm identical output (determinism). Plotted growth curves for different values of r.
5. Generated 16 noisy observations from the true curve.
6. Used the Metropolis algorithm (40,000 steps, 5,000 burn-in, uniform priors) to estimate r and K from the noisy data.
7. Plotted the traces, the posterior histograms, the joint posterior of r and K, and a posterior predictive band.

---

## 4. Tools Used

Python 3, Google Colab, NumPy, Matplotlib, SciPy (`scipy.integrate.solve_ivp`)

---

## 5. Key Findings

**Part A**

- With step size 2.5 the acceptance rate was about **52.4%**. The sample mean was 1.574 (true value 1.500) and the sample standard deviation 2.527 (true value 2.531). The histogram follows the two-peaked target closely, so the chain visits both modes.
- Effect of step size:

| Step size | Acceptance rate | Lag-1 autocorrelation | Behaviour |
|---|---|---|---|
| 0.1 | about 97% | 0.999 | Accepts almost everything but moves very slowly |
| 2.5 | about 53% | 0.833 | Good balance |
| 25 | about 10% | not reported | Chain gets stuck because most proposals are rejected |

**Part B**

- **Numerical vs analytic solution:** The maximum difference is about 3.3 x 10^-7, and re-running gives identical results (difference 0), which confirms that the model is deterministic.
- **Effect of r:** A larger r makes the population reach the carrying capacity faster, but K itself does not change.
- **Parameter recovery (acceptance rate about 24.8%):**

| Parameter | True value | Posterior mean | 95% interval |
|---|---|---|---|
| r | 0.8 | 0.781 | 0.742 to 0.825 |
| K | 100 | 98.09 | 94.99 to 101.21 |

- **Correlation:** r and K are negatively correlated in the posterior (about -0.47), so a faster growth rate can trade off against a smaller carrying capacity.
- **Posterior predictive:** The fitted curve (r = 0.781, K = 98.1) closely matches the true curve, and about 82% of the true curve lies inside the 95% posterior band.

---

## 6. What I Learned

- **Metropolis algorithm:** It draws samples from a distribution that is hard to sample directly, using only ratios of the density. This is why normalising constants do not matter.
- **Step size matters:**
  - Too small: almost every move is accepted, but the chain moves slowly and successive samples are highly correlated.
  - Too large: most moves are rejected and the chain gets stuck.
  - A moderate step size (acceptance around 20 to 50%) mixes best.
- **Autocorrelation** measures how similar successive samples are. Lower autocorrelation means more useful, independent-like samples.
- **Burn-in:** Early samples still reflect the starting point, so they are dropped.
- **Deterministic model:** Given the same parameters and starting condition, it always produces the same output. Randomness enters only through the noisy measurements.
- **Parameter estimation:** MCMC can recover unknown model parameters from noisy data and gives a full distribution, with uncertainty, rather than a single value.
- **Correlated parameters:** The negative correlation between r and K shows that the data cannot pin down each one separately, only a combination of them.

---

## 7. Conclusion

This practical implemented the Metropolis algorithm, showed how its step size controls the quality of sampling, and used it to recover the parameters of a logistic growth model from noisy data. The estimates (r about 0.78 and K about 98) are close to the true values (0.8 and 100), and both true values lie inside the 95% intervals.
