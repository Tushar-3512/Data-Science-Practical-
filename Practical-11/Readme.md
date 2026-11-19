# Practical 11 - Gamma Distribution and MCMC on the Sunspots Dataset

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

To model a real-world phenomenon, the sunspot cycle, with a **gamma distribution** and estimate its parameters using **Markov Chain Monte Carlo (MCMC)**. The practical covers:

- Plotting the data over the years
- Modelling the cycle with a gamma distribution that resets every 12 years
- Drawing the histogram of sunspot counts
- Running MCMC from a starting guess (a = 4, b = 10) and watching how the chain moves
- Studying the traces, burn-in and posterior distributions
- Predicting the cycle using the estimated parameters

---

## 2. Dataset Used

The analysis uses the **monthly mean total sunspot number** from SILSO (the World Data Center for sunspot observations), from January 1749 to November 2018, giving **3239 monthly values**.

---

## 3. Methodology

1. **Plot the data:** drew the series over the years and located the cycle peaks.
2. **Gamma model:** modelled one cycle as a gamma curve that repeats every 12 years (144 months), with parameters a, b, a height S and a noise level sigma.
3. **Histogram:** plotted the histogram of sunspot counts and fitted a gamma distribution to it.
4. **MCMC:** ran a Metropolis sampler for 30,000 iterations starting from a = 4 and b = 10. Plotted the path of the chain for the first 50 samples, all samples and the last 50 samples.
5. **Traces and burn-in:** plotted the traces of a and b, dropped the first 5,000 samples as burn-in, and plotted the posterior histograms with 95% intervals.
6. **Prediction:** used the posterior samples to predict the average cycle with a 95% band and forecast beyond November 2018.

---

## 4. Tools Used

Python 3, Google Colab, Pandas, NumPy, Matplotlib, SciPy (`scipy.stats`, `scipy.signal`, `scipy.special`)

---

## 5. Key Findings

- **The data:** The series rises and falls repeatedly, with 25 clear cycle peaks and an average gap of about **11.0 years**, close to the known 11-year solar cycle. The highest monthly value is 398 (in 1778) and the overall mean is 82.4. Peak heights differ a lot between cycles.
- **Initial guess (a = 4, b = 10):** The curve puts the peak 3.6 years into each cycle. It has a correlation of only 0.19 with the data, so it is a rough starting point.
- **Histogram:** The distribution is right-skewed (skewness 0.92), with the mean (82.4) above the median (68.3). A gamma fit gives shape of about 0.98 and scale of about 84.2.
- **MCMC:** The acceptance rate was about 9.1%. The chain moved from the starting point (a = 4, b = 10) and settled near a = 1.21 and b = 1.19. In the last 50 samples the spread is very small, so the chain has settled.
- **Posterior after burn-in:**

| Parameter | Mean | Std | 95% interval |
|---|---|---|---|
| a | 1.205 | 0.037 | 1.14 to 1.29 |
| b | 1.110 | 0.127 | 0.88 to 1.38 |

- **Correlation:** a and b are strongly correlated (about 0.91), so the posterior cloud stretches along a ridge.
- **Prediction:** The average cycle peaks about **2.2 years** after it starts, at roughly 100 sunspots, with a fast rise and a slow decline.
- **Fit quality:** The model explains only about **4.0%** of the variance. It is limited because real cycles last about 11 years (between 9 and 14) while the model resets every 12 years, and every cycle gets the same height.

---

## 6. What I Learned

- **Gamma distribution:** It suits data that is never negative and is right-skewed, which is true of sunspot counts. Its shape (a) and rate (b) control where the peak sits and how fast it rises and falls.
- **MCMC:** When a parameter cannot be solved directly, MCMC explores the posterior distribution by proposing new values and accepting or rejecting them. It starts from a guess and gradually moves to the region of high probability.
- **Burn-in:** The early samples still reflect the starting point, so they are dropped before computing results.
- **Traces and posteriors:** A stable trace after burn-in shows the chain has settled. The histogram of the samples shows the posterior distribution, and the 95% interval shows the uncertainty of each parameter.
- **Correlated parameters** (here a and b) make the posterior stretch along a ridge, which makes sampling harder.
- **Acceptance rate:** A low acceptance rate (about 9%) means many proposals were rejected, so the step sizes may be worth tuning.
- **A model is only as good as its assumptions:** A repeating 12-year curve captures the average cycle shape but cannot match the changing cycle lengths and heights, so its forecast describes a typical cycle and not exact future peaks.

---

## 7. Conclusion

This practical modelled the sunspot cycle with a gamma curve and estimated its parameters with MCMC (a is about 1.21 and b is about 1.11). The method works well for finding parameters and their uncertainty, but the simple repeating model explains only a small part of the variation in sunspot activity.
