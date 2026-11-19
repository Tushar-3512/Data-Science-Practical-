# Practical 1 - Revisiting Pandas and NumPy

| | |
|---|---|
| **Submitted By** | Tushar Sinsinbar |
| **Roll No** | GF202453725 |
| **Course** | B.Tech CSE (Data Science) |
| **Semester** | 5th Semester |
| **Subject** | Statistical Foundation of Data Science (CSU1658) |
| **Submitted To** | Anitya Gupta Sir |
| **Due Date** | August 15, 2026 |

---

## 1. Objective

To revisit the basics of **Pandas** and **NumPy** by working on a real dataset. The practical covers:

- Converting raw data into a Pandas DataFrame
- Finding the shape, size and dimension of an array using NumPy
- Performing matrix operations: addition, subtraction, multiplication, product, transpose and inverse

---

## 2. Dataset Used

The analysis uses the **Employee Salary Dataset**, loaded from a zip archive stored on Google Drive.

- **Size:** 35 rows x 5 columns

| Variable | Meaning |
|---|---|
| `ID` | Employee ID |
| `Experience_Years` | Years of work experience |
| `Age` | Age of the employee |
| `Gender` | Male / Female |
| `Salary` | Salary of the employee |

---

## 3. Methodology

1. Extracted the dataset from the zip file and loaded the CSV into a Pandas DataFrame. Checked its shape, columns and data types.
2. Converted the full DataFrame to a NumPy array and found its shape, size and dimension.
3. Selected only the numeric columns (`ID`, `Experience_Years`, `Age`, `Salary`) and converted them to a numeric array.
4. Split the numeric array into two equal parts, A and B (17 rows each), and performed addition, subtraction and element-wise multiplication.
5. Computed the transpose of A.
6. Computed the matrix product of A and the transpose of B.
7. Took a 4 x 4 square matrix from A and computed its inverse.

---

## 4. Tools Used

Python 3, Google Colab notebook, Pandas, NumPy

---

## 5. Key Findings

- **DataFrame:** 35 rows and 5 columns, with one text column (`Gender`) and four integer columns.
- **Full array:** shape (35, 5), size 175 and dimension 2.
- **Numeric array:** shape (35, 4) after dropping the `Gender` column.
- **Split arrays:** A and B both have shape (17, 4), so they can be added, subtracted and multiplied element-wise.
- **Transpose:** A has shape (17, 4) and its transpose has shape (4, 17).
- **Matrix product:** A (17 x 4) multiplied by the transpose of B (4 x 17) gives a (17 x 17) matrix.
- **Inverse:** Computed for a 4 x 4 square matrix taken from A. The inverse values for the `Salary` column are very small (around 10^-6), because salary values are much larger than the other columns.

---

## 6. What I Learned

- **DataFrame vs NumPy array:** A DataFrame keeps labels and mixed data types. A NumPy array is a plain numeric grid for fast calculations.
- **Mixed types:** Converting a DataFrame that contains text (such as `Gender`) gives an array of generic objects. Selecting numeric columns first with `select_dtypes` gives a proper numeric array.
- **shape, size and ndim:** shape is (rows, columns), size is the total number of elements, and ndim is the number of dimensions.
- **Element-wise operations** need both arrays to have the same shape. Element-wise multiplication (`*`) is different from the matrix product (`np.dot`).
- **Matrix product rule:** (m x n) times (n x p) gives (m x p). That is why B had to be transposed before multiplying with A.
- **Inverse:** Only a square matrix can be inverted, so a 4 x 4 block was used. Columns with very different scales (such as salary against age) produce very small or very large values in the result.

---

## 7. Conclusion

This practical covered loading data into Pandas, converting it to NumPy arrays, and performing core matrix operations on a real employee dataset. It builds the base for the data handling needed in the later practicals.
