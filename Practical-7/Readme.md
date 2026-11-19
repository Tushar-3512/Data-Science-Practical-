# Practical 7 - Regression, ANOVA and Correlation using Rating Dataset

| | |
|---|---|
| **Submitted By** | Tushar Sinsinbar |
| **Roll No** | GF202453725 |
| **Course** | B.Tech CSE (Data Science) |
| **Semester** | 5th Semester |
| **Subject** | Statistical Foundation of Data Science (CSU1658) |
| **Submitted To** | Anitya Gupta Sir |
| **Submission Date** | November 19, 2026 |

---

## 1. Objective

To apply **regression-based hypothesis testing** on a real-world dataset of professor teaching ratings. The practical covers:

- Testing whether gender affects teaching evaluation using regression with a t-test
- Testing whether beauty score differs across age groups using regression with ANOVA
- Testing whether teaching evaluation is correlated with beauty score
- Interpreting coefficients, p-values and R-squared to judge both significance and effect size

---

## 2. Dataset Used

The analysis uses the **TeachingRatings** dataset (Hamermesh and Parker), which contains student evaluation scores and related attributes for professors at the University of Texas at Austin.

- **Size:** 463 rows x 13 columns (12 original columns plus the derived `female` dummy variable)

| Variable | Meaning |
|---|---|
| `minority` | Whether the instructor is from a minority group (yes/no) |
| `age` | Age of the instructor |
| `gender` | Male / female |
| `credits` | Single-credit or multi-credit course |
| `beauty` | Standardised beauty rating (mean is about 0) |
| `eval` | Teaching evaluation score (1 to 5) |
| `division` | Lower or upper division course |
| `native` | Native English speaker (yes/no) |
| `tenure` | Whether the instructor is a tenured professor (yes/no) |
| `students` | Number of students who filled in the evaluation |
| `allstudents` | Number of students enrolled in the course |
| `prof` | Professor ID |
| `female` | Derived dummy variable: 1 if female, 0 if male |

---

## 3. Methodology

The dataset was loaded from Google Drive and analysed in a notebook using Python. The following steps were carried out:

1. Loaded the data, checked the column names and confirmed the unique values of `gender`.
2. Created a dummy variable `female` (1 = female, 0 = male) from the `gender` column.
3. **Q1 (Regression with t-test):** Fitted `eval ~ female` using OLS and read the t-test on the `female` coefficient.
4. **Q2 (Regression with ANOVA):** Grouped instructors into three age groups, fitted `beauty ~ age_group` using OLS and produced an ANOVA table with `anova_lm`.
5. **Q3 (Correlation):** Fitted `eval ~ beauty` using OLS and also computed Pearson's correlation coefficient.
6. Added a printed summary after each computation to record what was learned.

---

## 4. Tools Used

Python 3, Google Colab notebook, Pandas, Statsmodels, SciPy

---

## 5. Key Findings

- **Q1 - Gender vs evaluation:** The model is `eval = 4.069 - 0.168 x female`. Male instructors average about 4.07 and female instructors about 3.90. The t-test gives t = -3.25 and p = 0.001, which is below 0.05, so gender has a **statistically significant** effect on evaluation. R-squared is only 0.022, so the effect is small.
- **Q2 - Beauty vs age group:** The ANOVA gives F = 17.60 with p = 4.32e-08 (df = 2), far below 0.05. At least one age group has a **different mean beauty score**. ANOVA does not say which group differs, so a post-hoc test (such as Tukey HSD) would be needed.
- **Q3 - Evaluation vs beauty:** The model is `eval = 3.998 + 0.133 x beauty`. The slope has t = 4.133 and p < 0.001, so the relationship is **significant**. R-squared is 0.036, so r is about 0.19, which is a **weak positive correlation**.

---

## 6. What I Learned

- **Dummy variables:** With a single 0/1 variable, the intercept is the mean of the 0 group and the slope is the difference between the group means.
- **Regression and t-test are the same thing:** A regression on one dummy variable gives the same result as a two-sample t-test.
- **Baseline category:** `C(gender)` picks `female` as the baseline (alphabetical order), so the output shows a `male` coefficient of +0.168. Using the `female` dummy instead flips the sign to -0.168. Both describe the same model.
- **ANOVA** compares the means of three or more groups at once, where a t-test can only handle two. It is a regression with dummy variables, and F tests whether all group coefficients are jointly zero.
- **Significance is not size:** A small p-value shows the effect is real, not that it is large. R-squared shows the size. Q1 and Q3 are both significant but explain only 2% and 3.6% of the variation.
- **F and t are linked:** In simple regression, F = t squared (3.25 squared is about 10.56), and the slope p-value equals the overall F p-value.
- **Correlation is not causation:** Students may rate attractive instructors higher, but other factors could also be involved.
- The `typ=2` option in `anova_lm` gives the standard ANOVA table.

---

## 7. Conclusion

This practical showed how regression can be used to test hypotheses about group differences and relationships between variables. Gender and beauty score both have a statistically significant but small relationship with teaching evaluation, and beauty score differs significantly across age groups. In all three cases, checking R-squared alongside the p-value is important to judge how meaningful the result really is.
