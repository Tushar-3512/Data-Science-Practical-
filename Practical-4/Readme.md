# Practical 4 - Exploring Duplicates, Comparative and Relational Visualization using Rating Dataset

| | |
|---|---|
| **Submitted By** | Tushar Sinsinbar |
| **Roll No** | GF202453725 |
| **Course** | B.Tech CSE (Data Science) |
| **Semester** | 5th Semester |
| **Subject** | Statistical Foundation of Data Science (CSU1658) |
| **Submitted To** | Anitya Gupta Sir |
| **Submission Date** | August 30, 2026 |

---

## 1. Objective

To extend the descriptive-statistics foundation from Practical 3 by:

- Handling duplicate records correctly
- Comparing teaching evaluations across course levels using bar charts
- Exploring the relationship between age and teaching evaluation using scatter plots, including views split by gender and by tenure status

---

## 2. Dataset Used

The analysis uses the **TeachingRatings** dataset (463 records, 94 unique instructors), which contains student evaluation scores and attributes such as tenure status, age, gender, minority status and course level (lower or upper division). Each instructor can appear several times, once per course evaluated, so the data contains duplicate instructor records.

---

## 3. Methodology

1. Identified duplicate cases using the professor identifier (`prof`). Computed the mean and standard deviation of age using all observations, then repeated it after keeping one observation per instructor (94 observations).
2. Used a bar chart to check whether instructors teaching lower-division courses receive higher average evaluations than those teaching upper-division courses.
3. Plotted age against evaluation score as a scatter plot and measured the correlation.
4. Created gender-differentiated scatter plots of age against evaluation score.
5. Created a scatter plot of age against evaluation score differentiated by both gender and tenure status (four groups).

---

## 4. Tools Used

Python 3, Google Colab notebook, Pandas, Matplotlib

---

## 5. Key Findings

- **Duplicates:** The 463 rows belong to only 94 instructors. Using all rows, age has a mean of about 48.37 and a standard deviation of about 9.80. After keeping one row per instructor, the mean is about 47.55 and the standard deviation about 10.26.
- **Division:** Lower-division courses have a higher average evaluation (about 4.09) than upper-division courses (about 3.95).
- **Age and evaluation:** The scatter plot shows no clear pattern. The correlation is about -0.05, which is essentially no linear relationship.
- **By gender:** Male instructors average about 4.07 and female instructors about 3.90.
- **By gender and tenure:** Gender shows the more visible pattern, with male points sitting slightly higher. Tenure status does not create an obvious visual split. Untenured male instructors have the highest average evaluation (about 4.40).

---

## 6. What I Learned

- **Duplicates change results:** When one subject appears many times, statistics computed on all rows are weighted toward subjects with more rows. Use `drop_duplicates` on the ID column to get one row per subject.
- **Bar charts for comparing groups:** A bar of group means is a quick way to compare averages across categories.
- **Scatter plots show relationships** between two numeric variables, and the correlation coefficient puts a number on it. A value near 0 means no linear relationship.
- **Splitting a scatter plot by colour or marker** (gender, tenure) reveals patterns that a single combined plot hides.
- A visual pattern in a sample is not proof of a real effect. Group differences should be confirmed with a statistical test.

---

## 7. Conclusion

This practical showed why duplicate records must be handled before computing statistics, and how bar charts and scatter plots reveal differences and relationships. In this dataset, age has almost no relationship with evaluation score, while gender and course division show visible differences.
