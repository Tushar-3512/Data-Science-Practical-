# Practical 6 - Hypothesis Testing and Correlation using the Teaching Ratings Dataset

| | |
|---|---|
| **Submitted By** | Tushar Sinsinbar |
| **Roll No** | GF202453725 |
| **Course** | B.Tech CSE (Data Science) |
| **Semester** | 5th Semester |
| **Subject** | Statistical Foundation of Data Science (CSU1658) |
| **Submitted To** | Anitya Gupta Sir |
| **Submission Date** | September 13, 2026 |

---

## 1. Objective

To apply four core inferential statistics techniques to the teachers' rating dataset, each answering a different type of question:

- **t-test:** compare means across two groups
- **ANOVA:** compare means across more than two groups
- **Chi-square test:** test association between two categorical variables
- **Pearson correlation:** measure the strength of a linear relationship between two numeric variables

---

## 2. Dataset Used

The analysis uses the **TeachingRatings** dataset, which contains 463 course evaluation records with attributes including instructor gender, age, minority status, beauty score, evaluation score (`eval`), tenure status, native-English status, division and student enrolment figures.

---

## 3. Methodology

1. Ran an independent samples t-test (Welch) to check whether gender affects teaching evaluation scores.
2. Grouped instructors into four age brackets (35 or under, 36 to 45, 46 to 55, 56 and above) and ran a one-way ANOVA to test whether beauty score differs by age group.
3. Built a contingency table of tenure against gender and applied a chi-square test of independence.
4. Computed the Pearson correlation between evaluation score and beauty score.
5. Interpreted each result at the 5% significance level (alpha = 0.05) to reject or fail to reject the null hypothesis.

---

## 4. Tools Used

Python 3, Google Colab notebook, Pandas, SciPy (`scipy.stats`)

---

## 5. Key Findings

| Test | Question | Result | Decision at 5% |
|---|---|---|---|
| t-test | Does gender affect evaluation score? | Male mean 4.07, female mean 3.90, t = 3.27, p = 0.0012 | Significant: gender affects evaluation scores |
| ANOVA | Does beauty score differ by age group? | F = 13.72, p = 1.4 x 10^-8 | Significant: beauty score differs by age group |
| Chi-square | Is tenure associated with gender? | Chi-square = 2.21, p = 0.137 | Not significant: no evidence of association |
| Pearson correlation | Is evaluation correlated with beauty? | r = 0.189, p = 4.2 x 10^-5 | Significant, but weak positive correlation |

- Beauty score falls steadily with age group, from a mean of about 0.45 for ages 35 and under to about -0.27 for ages 56 and above.

---

## 6. What I Learned

- **Choosing the right test:** t-test for two group means, ANOVA for three or more group means, chi-square for two categorical variables, Pearson correlation for two numeric variables.
- **p-value rule:** If p is below 0.05, reject the null hypothesis. Otherwise, fail to reject it.
- **Statistical vs practical significance:** The correlation between evaluation and beauty is significant (p is tiny), but r = 0.19 is weak. A significant result does not always mean a strong effect.
- **ANOVA** tells us that at least one group differs, but not which one. A follow-up test is needed to find out.
- **Welch's t-test** does not assume equal variances in the two groups, so it is a safer default.
- **Correlation is not causation:** A relationship between two variables does not show that one causes the other.

---

## 7. Conclusion

This practical used four standard tests to answer four different kinds of questions on the same dataset. Gender and age group showed significant differences, evaluation and beauty showed a weak positive correlation, and tenure was not significantly associated with gender.
