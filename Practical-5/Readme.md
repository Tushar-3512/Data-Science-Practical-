# Practical 5 - Probability and Hypothesis Testing using the Ratings Dataset

| | |
|---|---|
| **Submitted By** | Tushar Sinsinbar |
| **Roll No** | GF202453725 |
| **Course** | B.Tech CSE (Data Science) |
| **Semester** | 5th Semester |
| **Subject** | Statistical Foundation of Data Science (CSU1658) |
| **Submitted To** | Anitya Gupta Sir |
| **Submission Date** | September 11, 2026 |

---

## 1. Objective

To apply probability theory and hypothesis testing to real data. The normal distribution is used to estimate the probability of professors receiving evaluation scores in given ranges. A two-tailed z-test is then used on a basketball scoring example to decide whether a sample mean differs significantly from a known population mean.

---

## 2. Dataset Used

The analysis uses the **TeachingRatings** dataset (463 records). The `eval` column (student evaluation score from 1 to 5) is used to estimate probabilities. The hypothesis test uses a separate basketball scoring example given in the question.

---

## 3. Methodology

1. Computed the mean and standard deviation of `eval` to model it as a normal distribution.
2. Calculated P(eval > 4.5) using the normal cumulative distribution function.
3. Calculated P(3.5 < eval < 4.2) as the area between two points under the normal curve.
4. Stated the null and alternative hypotheses for a two-tailed test comparing the regional players' mean score with the professional players' historic mean.
5. Computed the z-statistic and two-tailed p-value, then compared the p-value with the significance level of 0.05 to decide whether to reject the null hypothesis.

---

## 4. Tools Used

Python 3, Google Colab notebook, Pandas, NumPy, Matplotlib, SciPy (`scipy.stats`)

---

## 5. Key Findings

- **Evaluation score distribution:** Mean about 3.998 and standard deviation about 0.555.
- **P(eval > 4.5):** About 0.183, so roughly 18.3% of evaluations would exceed 4.5.
- **P(3.5 < eval < 4.2):** About 0.457, so roughly 45.7% of evaluations fall between 3.5 and 4.2.
- **Hypothesis test (basketball):** Professional players have a historic mean of 12 points per game (standard deviation 5.5). A sample of 36 regional players averaged 10.7 points. The z-score is about -1.42 and the two-tailed p-value is about 0.156.
- **Decision:** The p-value is above 0.05, so we **fail to reject the null hypothesis**. There is not enough evidence that the regional players' mean differs from the historic mean.

---

## 6. What I Learned

- **Normal distribution probabilities:** A probability is the area under the normal curve. `P(X > a) = 1 - CDF(a)` and `P(a < X < b) = CDF(b) - CDF(a)`.
- **Z-score:** `z = (x̄ - μ) / (σ / √n)` measures how many standard errors a sample mean is from the population mean.
- **Two-tailed test:** Used when we only ask whether the mean is *different* (higher or lower). The p-value is `2 x P(Z > |z|)`.
- **Decision rule:** If p is below the significance level (0.05), reject the null hypothesis. Otherwise, fail to reject it.
- **"Fail to reject" is not "accept":** It only means the data does not give enough evidence against the null hypothesis.
- **Modelling assumption:** Treating `eval` as normal is an approximation. A histogram of the scores helps check how reasonable it is.

---

## 7. Conclusion

This practical applied the normal distribution to estimate probabilities from real ratings and used a two-tailed z-test to make a decision about a population mean. For the basketball example, the data does not show a significant difference at the 5% level.
