# Statistical Foundation of Data Science: Practicals

Twelve hands-on practicals for **Statistical Foundation of Data Science (CSU1658)**, B.Tech CSE (Data Science), Shoolini University. They build step by step from data handling and descriptive statistics, through hypothesis testing and regression, to machine learning models and Bayesian sampling (MCMC), all implemented in Python.

Each practical is a Google Colab notebook with the problem, code, outputs, and a written interpretation of the results.

---

## Practicals Overview

| # | Topic | What was done | Datasets |
|---|-------|---------------|----------|
| 1 | Pandas & NumPy | Loaded data into DataFrames, checked shape/size/dimension, ran matrix operations (add, subtract, multiply, product, transpose, inverse) | Employee Salary (35 x 5) |
| 2 | Foundations of Stats | Classified data as cross-sectional, computed summary statistics, histogram of beauty scores, chi-square test of tenure vs gender | TeachingRatings (463 x 12) |
| 3 | Descriptive Statistics | Tenure percentages by minority status, mean and std of age by tenure, choosing the right graph, `bar` vs `barh`, median evaluation score | TeachingRatings |
| 4 | Data Visualization | Handled duplicate instructor records, bar chart by course division, scatter plots split by gender and tenure | TeachingRatings |
| 5 | Probability & Two-Tailed Test | Normal-distribution probabilities, two-tailed z-test with null/alternative hypotheses | TeachingRatings + basketball scoring problem |
| 6 | T-Test, ANOVA, Chi-Square, Correlation | Four inferential tests, each answering a different type of question | TeachingRatings |
| 7 | Regression with T-Test & ANOVA | OLS regression with dummy variables, ANOVA tables, R-squared for effect size | TeachingRatings |
| 8 | Decision Trees | Entropy, Information Gain and Gini Index to justify the root node, `max_depth`, tree visualization | Pima Indians Diabetes (768 records) |
| 9 | K-Nearest Neighbors | Feature scaling, confusion matrix, classification report, error rate vs K, decision regions | Iris (150 records) |
| 10 | PCA | Descriptive statistics, boxplots, scatter plots, covariance matrix, scaling, class separation with principal components | Wine |
| 11 | Monte Carlo & MCMC | Modelled sunspot counts with a gamma distribution, MCMC sampling, trace plots, burn-in, posterior histograms | Monthly mean sunspot numbers, 1749 to 2018 |
| 12 | Metropolis Algorithm & Deterministic Model | Implemented a Metropolis sampler, studied step size, recovered logistic growth parameters from noisy data | Simulated |

---

## Highlights

**Statistical testing (Practicals 2 to 7)**
- Tenure status was **not** significantly associated with gender (chi-square p = 0.137).
- Gender significantly affects evaluation scores (Welch t-test p = 0.0012), but the effect is small (R-squared = 0.022). Regression on a gender dummy gives the same result as the t-test.
- Beauty score differs significantly across age groups (ANOVA p < 0.001).
- Evaluation and beauty score have a significant but weak positive correlation (r = 0.19).
- Two-tailed z-test (basketball example): z of about -1.42, p of about 0.156, so the null hypothesis could not be rejected at the 5% level.
- Throughout, significance was checked alongside effect size, since a small p-value does not mean a large effect.

**Data handling (Practical 4)**
- The 463 rows belong to only 94 instructors. Removing duplicates changed the mean age from about 48.4 to 47.6, which shows why duplicate records need handling before computing statistics.

**Machine learning (Practicals 8 and 9)**
- **Decision tree (Pima diabetes):** Entropy/Information Gain and Gini Gain both picked **Insulin** as the root node, matching scikit-learn's own choice. A tree with `max_depth = 3` reached about **85.7%** test accuracy with 0.89 recall on the diabetic class.
- **KNN (Iris):** With scaled features and K = 5, the model reached **93.3%** accuracy. Setosa was separated perfectly, and the only errors were virginica flowers predicted as versicolor. Testing K from 1 to 40 showed how very small K overfits and very large K underfits.

**Bayesian sampling (Practical 12)**
- A Metropolis sampler on a two-peaked target showed the step-size trade-off: a step of 0.1 gave about 97% acceptance but very slow mixing, 2.5 gave a good balance (about 52% acceptance), and 25 got stuck (about 10% acceptance).
- The sampler recovered logistic growth parameters from 16 noisy observations: r of about 0.78 (true 0.8) and K of about 98 (true 100). Both true values fall inside the 95% intervals.

---

## Skills Demonstrated

- **Data handling:** Pandas, NumPy, duplicate handling, filtering, missing-value cleaning, categorical encoding
- **Descriptive statistics and visualization:** summary tables, histograms, bar charts, scatter plots, boxplots, trace plots (Matplotlib, Seaborn)
- **Inferential statistics:** z-test, t-test, ANOVA, chi-square, Pearson correlation, hypothesis testing
- **Regression:** OLS with Statsmodels, dummy variables, interpreting coefficients, p-values and R-squared
- **Machine learning:** Decision Trees and KNN with Scikit-learn, stratified splits, feature scaling, confusion matrix, precision/recall, hyperparameter selection
- **Dimensionality reduction:** PCA and covariance analysis
- **Probabilistic methods:** Monte Carlo simulation, MCMC, Metropolis algorithm, burn-in, autocorrelation, posterior inference

---

## Tech Stack

Python 3, Pandas, NumPy, SciPy, Statsmodels, Scikit-learn, Matplotlib, Seaborn, Google Colab

---

## Repository Structure

```
Data-Science-Practical-/
├── Practical1.ipynb      # Pandas & NumPy
├── Practical_2.ipynb     # Foundations of Stats
├── Practical3.ipynb      # Descriptive Statistics
├── Practical4.ipynb      # Data Visualization
├── Practical5.ipynb      # Probability & Two-Tailed Test
├── Practical6.ipynb      # T-Test, ANOVA, Chi-Square, Correlation
├── Practical_7.ipynb     # Regression with T-Test & ANOVA
├── Practical_8.ipynb     # Decision Trees
├── Practical_9.ipynb     # KNN
├── Practical10.ipynb     # PCA
├── Practical11.ipynb     # Monte Carlo & MCMC
├── Practical12.ipynb     # Metropolis & Deterministic Model
├── LICENSE
└── README.md
```

---

## How to Run

**Google Colab:** open any notebook from GitHub via *File → Open notebook → GitHub*, paste the repo URL, and run all cells.

**Locally:**

```bash
git clone https://github.com/Tushar-3512/Data-Science-Practical-.git
cd Data-Science-Practical-
pip install pandas numpy scipy statsmodels matplotlib seaborn scikit-learn jupyter
jupyter notebook
```

Some notebooks load data from Google Drive (TeachingRatings, Employee Salary, Pima Indians Diabetes from Kaggle). Download the dataset and update the file path in the notebook if needed. Iris and Wine are also available directly through scikit-learn.

---

## License

Released under the MIT License. See [LICENSE](LICENSE) for details.
