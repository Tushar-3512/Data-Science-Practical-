# Practical 2 - Understanding Foundation of Stats using Rating Dataset

| | |
|---|---|
| **Submitted By** | Tushar Sinsinbar |
| **Roll No** | GF202453725 |
| **Course** | B.Tech CSE (Data Science) |
| **Semester** | 5th Semester |
| **Subject** | Statistical Foundation of Data Science (CSU1658) |
| **Submitted To** | Anitya Gupta Sir |
| **Submission Date** | August 23, 2026 |

---

## 1. Objective

To build a foundational understanding of **descriptive statistics** by analysing a real-world dataset of professor teaching ratings. The practical covers:

- Identifying the nature of the data (time series or cross-sectional)
- Computing summary statistics (mean, median, minimum, maximum)
- Producing a descriptive statistics table
- Visualising a distribution with a histogram and interpreting its shape
- Drawing comparative conclusions across groups such as gender and tenure status

---

## 2. Dataset Used

The analysis uses the **TeachingRatings** dataset (Hamermesh and Parker), which contains student evaluation scores and related attributes for professors at the University of Texas at Austin.

- **Size:** 463 rows x 12 columns

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

---

## 3. Methodology

The dataset was loaded and examined in a notebook using Python. The following steps were carried out:

1. Determined whether the dataset is time series or cross-sectional data from its structure.
2. Calculated the mean, median, minimum and maximum of the `students` variable.
3. Generated a descriptive statistics table for all numerical variables.
4. Plotted a histogram of the `beauty` variable and interpreted its distribution.
5. Compared average beauty scores of male and female instructors using group-wise means and standard deviations.
6. Calculated the percentage of male and female instructors who are tenured and tested whether tenure status differs by gender using a chi-square test of independence.

---

## 4. Tools Used

Python 3, Google Colab notebook, Pandas, NumPy, Matplotlib, SciPy

---

## 5. Key Findings

- **Type of data:** Cross-sectional. It covers many different instructors at one point in time, with no time sequence.
- **Class size (`students`):** The mean (about 36.6) is much higher than the median (23), with a range of 5 to 380. A few very large classes pull the mean up, so the data is right-skewed.
- **Beauty score:** Centred near 0 (standard deviation about 0.79) and slightly right-skewed, not a perfect bell curve.
- **Beauty by gender:** Female instructors average about 0.116 and male instructors about -0.084, with a similar spread.
- **Tenure by gender:** About 74.4% of female and 80.6% of male instructors are tenured. The chi-square test gives p = 0.137, which is above 0.05, so the difference is **not statistically significant**.

---

## 6. What I Learned

- **Cross-sectional vs time series:** Cross-sectional data observes many subjects at one time. Time series data tracks the same subject over time.
- **Mean vs median:** When the mean is far from the median, the data is skewed or has outliers, and the median is the better "typical" value.
- **`describe()`** summarises every numeric column in one step (count, mean, standard deviation, quartiles) and also reveals missing values.
- **Histograms** show the centre, spread and skewness of a variable, which summary numbers alone cannot show.
- **Group comparisons** with means and standard deviations show whether groups look different, but a statistical test is needed to say whether the difference is real.
- **Chi-square test of independence** checks whether two categorical variables (gender and tenure) are related. A p-value above 0.05 means we cannot claim a real relationship.
- Columns like `rownames` and `prof` are only identifiers, so their statistics carry no meaning.

---

## 7. Conclusion

This practical showed how to describe a dataset using summary statistics and visualisation, and why a difference in sample percentages must be tested before it is called significant. In this dataset, gender does not significantly affect tenure status.
