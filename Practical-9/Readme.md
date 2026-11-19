# Practical 9 - K-Nearest Neighbors (KNN) and Choosing the Best K

**Building a KNN Classifier on the Iris Dataset**

| | |
|---|---|
| **Submitted By** | Tushar Sinsinbar |
| **Roll No** | GF202453725 |
| **Course** | B.Tech CSE (Data Science) |
| **Semester** | 5th Semester |
| **Subject** | Statistical Foundation of Data Science (CSU1658) |
| **Submitted To** | Anitya Gupta Sir |
| **Submission Date** | October 14, 2026 |

---

## 1. Objective

To build a **K-Nearest Neighbors (KNN)** classifier with Scikit-learn that predicts the species of an iris flower from its measurements. The practical covers:

- Exploring the data
- Scaling the features
- Training the model and evaluating it with the confusion matrix, accuracy score and classification report
- Studying how the value of K affects the error rate and how the best K is chosen
- Visualising the decision regions of the trained model on the test data

---

## 2. Dataset Used

The analysis uses the **Iris** dataset (UCI, downloaded from Kaggle), with **150 flower records** equally divided among three species: Iris-setosa, Iris-versicolor and Iris-virginica (50 each). There are no missing values.

| Type | Variables |
|---|---|
| Independent (features) | SepalLengthCm, SepalWidthCm, PetalLengthCm, PetalWidthCm |
| Dependent (target) | Species |
| Not used | Id (record identifier only) |

---

## 3. Methodology

1. **Exploratory Data Analysis:** inspected the data with `head()`, `describe()` and `groupby()`, and checked for missing values.
2. **Feature selection and split:** used the four measurements as features and `Species` as the target. Split the data 80% training and 20% testing, stratified on species.
3. **Feature scaling:** standardised the features with `StandardScaler`, because KNN is based on distances and features on larger scales would otherwise dominate.
4. **Training:** trained a KNN classifier with K = 5.
5. **Confusion matrix and accuracy:** predicted the test set and checked which species were confused.
6. **Classification report:** generated precision, recall, F1-score and support for each species.
7. **Error rate against K:** trained a separate KNN model for every K from 1 to 40 and recorded the test error rate of each.
8. **Error plot:** plotted the error rate against K to study underfitting and overfitting.
9. **Best K:** chose among the K values with the lowest error, preferring an odd and stable value to avoid voting ties. The selected value was **K = 5**.
10. **Visualisation:** plotted the decision regions on petal length and petal width with the test points on top.

---

## 4. Tools Used

Python 3, Google Colab, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn (`sklearn.neighbors`, `sklearn.preprocessing`, `sklearn.model_selection`, `sklearn.metrics`)

---

## 5. Key Findings

- **Data:** 150 rows and 6 columns, balanced classes (50 per species) and no missing values.
- **Split sizes:** 120 training samples and 30 test samples.
- **KNN with scaled features (K = 5):** accuracy of **93.33%** on the 30 test samples.
- **Confusion matrix:** all 10 setosa and all 10 versicolor flowers were classified correctly. 8 of 10 virginica were correct, and 2 virginica were predicted as versicolor.

| Species | Precision | Recall | F1-score |
|---|---|---|---|
| Iris-setosa | 1.000 | 1.000 | 1.000 |
| Iris-versicolor | 0.833 | 1.000 | 0.909 |
| Iris-virginica | 1.000 | 0.800 | 0.889 |

- **Error rate against K (K = 1 to 40):** This step used the unscaled features. The lowest error rate was 0.0000, reached at K = 3, 4, 5, 9 and 10. K = 1 and 2 were unstable (errors of 0.033 and 0.067). Beyond K = 20 the error rose to about 6 to 10%.
- **Best K:** Among the tied values, the odd values are 3, 5 and 9. K = 5 was chosen as the most stable. The final model with K = 5 scored 100% on the 30 test samples.
- **Decision regions (petal length and width only):** accuracy of 96.67%. Setosa is perfectly separated, while versicolor and virginica overlap near petal length 5 to 5.5, where one virginica point was misclassified.

---

## 6. What I Learned

- **How KNN works:** It classifies a flower by the majority class among its K nearest training samples, using distance between measurements.
- **Why scaling matters:** KNN uses distances, so features with larger numeric ranges would dominate unless all features are put on the same scale. The scaler is fitted on the training data only and then applied to the test data.
- **Effect of K:**
  - A very small K (1 or 2) is unstable, since one noisy neighbour can change the prediction (overfitting).
  - A very large K blurs the boundaries between classes (underfitting).
  - A small odd K (such as 3 or 5) works best here, and an odd K avoids voting ties.
- **Reading a confusion matrix:** Rows are actual species and columns are predicted species. The errors show which classes get confused, here versicolor and virginica.
- **Accuracy vs the full report:** Precision, recall and F1 show how each class performs, not just the overall score.
- **Small test sets:** With only 30 test samples, each wrong prediction changes the error rate by about 3.3%, so small differences between K values are not very meaningful.
- **Decision regions** show where the model draws its boundaries, and why overlapping classes are the ones that get misclassified.

---

## 7. Conclusion

This practical built a KNN classifier on the Iris dataset and showed how the choice of K controls the balance between overfitting and underfitting. A small odd K (K = 5) gave the best results, and the model separates setosa perfectly, while versicolor and virginica are the species most often confused.
