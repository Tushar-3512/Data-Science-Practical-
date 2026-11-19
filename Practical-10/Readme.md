# Practical 10 - Exploratory Data Analysis and PCA on the Wine Quality Dataset

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

To explore a real dataset, understand how its features relate to the output classes, and use **Principal Component Analysis (PCA)** to get a clearer picture of class separation. The practical covers:

- Basic statistics with `describe()`
- Boxplots of every feature by output class
- A scatterplot of two variables
- The covariance matrix
- Feature scaling
- Class separation using principal components

---

## 2. Dataset Used

The analysis uses the **Wine Quality** dataset (`WineQT.csv`, from Kaggle), with **1143 wine samples** and 12 columns.

| Type | Variables |
|---|---|
| Independent (features) | fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, density, pH, sulphates, alcohol |
| Dependent (target / class) | quality (score from 3 to 8) |

---

## 3. Methodology

1. **Basic statistics:** loaded the data and used `describe()` to get the count, mean, standard deviation, quartiles, minimum and maximum of every column.
2. **Boxplots by class:** drew one boxplot per feature against the quality score to see which features separate the quality classes.
3. **Scatterplot:** plotted alcohol against volatile acidity, coloured by quality.
4. **Covariance matrix:** computed and plotted the covariance matrix of the 11 features as a heatmap.
5. **Data scaling:** standardised the features with `StandardScaler` (mean 0, standard deviation 1).
6. **PCA:** reduced the scaled data to two principal components and plotted the wines coloured by quality.

---

## 4. Tools Used

Python 3, Google Colab, KaggleHub, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn (`StandardScaler`, `PCA`)

---

## 5. Key Findings

- **Statistics:** The features are on very different scales. Total sulfur dioxide goes up to 289, while chlorides are below 1. Residual sugar and chlorides are right-skewed (mean above median). The average quality is about 5.66.
- **Boxplots by quality:**

| Separation | Features |
|---|---|
| Strong | Volatile acidity (median falls as quality rises), alcohol (median rises steadily, the clearest trend of all) |
| Good or moderate | Sulphates (rises with quality), citric acid (tends to rise), total sulfur dioxide (higher for middle qualities) |
| Weak | Fixed acidity, residual sugar, chlorides, free sulfur dioxide, density, pH |

- **Scatterplot:** High-quality wines tend to have higher alcohol and lower volatile acidity, and low-quality wines the opposite. The classes still overlap a lot, so two features alone cannot separate them.
- **Covariance matrix:** Total sulfur dioxide dominates the variance simply because it has the largest scale, which is why scaling is needed.
- **Scaling:** After standardising, every feature has a mean of about 0 and a standard deviation of 1.
- **PCA:** The first two components capture about **28.7%** and **17.1%** of the variance, **45.8%** in total. The plot shows wines of different quality starting to spread toward different regions, but the classes still overlap.

---

## 6. What I Learned

- **`describe()`** gives a quick summary of every column, shows missing values through the count, and comparing mean with median hints at skewness.
- **Boxplots by class** show which features actually differ between classes. A feature whose median moves steadily with the class (alcohol, volatile acidity) is a useful predictor, while one whose boxes overlap heavily is not.
- **Covariance depends on units:** Features with large scales look more important than they are, so covariance should be read after scaling.
- **Standardisation** (`z = (x - mean) / std`) puts all features on the same scale. It is essential before PCA, because PCA follows directions of maximum variance and would otherwise just follow the biggest-scale feature.
- **PCA** combines correlated features into new uncorrelated axes called principal components. Component 1 captures the most variance, and component 2 captures the most of what is left.
- **Explained variance ratio** tells how much information is kept. Two components keep only about 46%, so some information is lost.
- **Overlap in PCA is expected:** Wine quality is a subtle human rating, so even a good 2D view cannot separate the classes perfectly.

---

## 7. Conclusion

This practical showed how to explore a dataset with statistics and plots and why scaling is needed before PCA. Alcohol and volatile acidity are the features that best separate wine quality, and PCA gives a clearer 2D view of the classes, although they still overlap.
