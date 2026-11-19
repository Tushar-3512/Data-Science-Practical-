# Practical 8 - Decision Trees and its Maxdepth

**Building a Decision Tree Classifier on the Pima Indians Diabetes Dataset**

| | |
|---|---|
| **Submitted By** | Tushar Sinsinbar |
| **Roll No** | GF202453725 |
| **Course** | B.Tech CSE (Data Science) |
| **Semester** | 5th Semester |
| **Subject** | Statistical Foundation of Data Science (CSU1658) |
| **Submitted To** | Anitya Gupta Sir |
| **Submission Date** | October 7, 2026 |

---

## 1. Objective

To build a **decision tree classifier** with Scikit-learn that predicts whether a patient has diabetes. The practical covers:

- Dividing the columns into dependent (target) and independent (feature) variables
- Splitting the data into training and testing sets
- Using **Entropy**, **Information Gain** and the **Gini Index** to justify why a feature is chosen as the root node
- Building and visualising the tree
- Studying how the `max_depth` parameter controls the size of the tree

---

## 2. Dataset Used

The analysis uses the **Pima Indians Diabetes** dataset from Kaggle, with **768 patient records**.

| Type | Variables |
|---|---|
| Independent (features) | Pregnancies, Glucose, BloodPressure, SkinThickness, Insulin, BMI, DiabetesPedigreeFunction, Age |
| Dependent (target) | Outcome (0 = no diabetes, 1 = diabetes) |

Class balance: 500 patients without diabetes and 268 with diabetes.

---

## 3. Methodology

1. Loaded the dataset from Google Drive and checked its shape (768 rows, 9 columns).
2. **Cleaned the data:** treated impossible zero values (for example a glucose or blood pressure of 0) as missing and filled them with the column median.
3. **Feature selection:** separated the eight measurement columns as features and `Outcome` as the target.
4. **Train/test split:** 70% training and 30% testing, stratified on `Outcome` so both parts keep the same proportion of diabetic patients.
5. **Entropy, Information Gain and Gini Index:** wrote functions to measure impurity, then found the best split for every feature and compared them to choose the root node.
6. **Built the tree:** a `DecisionTreeClassifier` with the entropy criterion and `max_depth = 3`, so the tree stays readable and does not overfit.
7. **Evaluated the tree** using accuracy, the confusion matrix and the classification report on the test set.
8. **Visualised the tree** with `plot_tree` and plotted a feature importance chart.

---

## 4. Tools Used

Python 3, Google Colab, Pandas, NumPy, Matplotlib, Scikit-learn (`sklearn.tree`, `sklearn.model_selection`, `sklearn.metrics`)

---

## 5. Key Findings

- **Split sizes:** 537 training records and 231 testing records.
- **Impurity before any split:** Entropy is about 0.9325 and Gini is about 0.4539 on the training data. A good split must push these numbers down.
- **Choosing the root node:** Both Information Gain and Gini Gain pick **Insulin** as the best root.

| Feature | Information Gain | Gini Gain |
|---|---|---|
| Insulin | 0.3395 | 0.1960 |
| SkinThickness | 0.1525 | 0.0949 |
| Glucose | 0.1400 | 0.0876 |
| Age | 0.0911 | 0.0549 |
| BMI | 0.0682 | 0.0406 |
| Pregnancies | 0.0407 | 0.0266 |
| BloodPressure | 0.0278 | 0.0170 |
| DiabetesPedigreeFunction | 0.0237 | 0.0151 |

- **sklearn agrees:** The tree chose `Insulin <= 109` as the root, matching the manual calculation.
- **Accuracy:** About **85.7%** on the 231 unseen test patients.
- **Confusion matrix:** 126 true negatives, 24 false positives, 9 false negatives and 72 true positives.
- **Class 1 (diabetes):** precision 0.75, recall 0.89. The tree catches most diabetic patients (high recall) but also flags some healthy ones.
- **Feature importance:** Insulin is the most important feature (about 0.755) and is also the root node.

---

## 6. What I Learned

- **Dependent vs independent variables:** The target is what we want to predict (`Outcome`). The features are the clues used to predict it.
- **Entropy** measures how mixed the classes are: `H = -sum(p x log2(p))`. **Gini** measures the same thing differently: `G = 1 - sum(p^2)`. Both are 0 for a perfectly pure group.
- **Information Gain** is the impurity before a split minus the weighted impurity after it. The feature with the highest gain becomes the root.
- **Two measures, same answer:** Entropy and Gini usually lead to similar trees, and here both chose Insulin.
- **`max_depth`** limits how many levels the tree can grow. A shallow tree (depth 3) is easy to read and less likely to memorise the training data (overfitting). An unlimited tree can fit the training data perfectly but do worse on new data.
- **Stratified splitting** keeps the class ratio equal in training and testing sets.
- **Accuracy alone is not enough:** The confusion matrix and the precision/recall in the classification report show which kind of mistakes the model makes, which matters in medical problems.
- **Data cleaning affects the tree:** Filling missing values with the median is a simple choice, but it can influence which feature looks best for the first split.
- **Feature importance** adds up the impurity reduction from every split a feature makes, so it can differ from the root node.

---

## 7. Conclusion

This practical built a decision tree on the Pima Indians Diabetes data and showed, with Entropy, Information Gain and Gini Index, why Insulin is the best root node. The tree with `max_depth = 3` reached about 85.7% test accuracy while staying easy to read.
