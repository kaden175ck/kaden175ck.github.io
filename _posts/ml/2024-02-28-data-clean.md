---
layout: post
title: "Data Cleaning"
date: 2024-02-28
categories: machine learning
permalink: "/ML/DataCleaning"
---
**Understanding Data Cleaning**

* **Why it matters:** Real-world datasets are often messy. Data cleaning is the process of identifying and fixing issues to make your dataset ready for analysis and modeling. This includes handling missing values, correcting errors,  and ensuring data consistency.
* **Benefits:** Clean data leads to more reliable insights and improves the accuracy of your machine learning models.

**Step-by-Step Guide**

1. **Load Your Data:**
   * **Choose your tool:**  Python with libraries like Pandas is excellent for data cleaning. You could also consider tools like  Excel or OpenRefine for smaller datasets or visual exploration.
   * **Load dataset:** Use functions like `pd.read_csv()` (Pandas)  to load your dataset from Kaggle. 

2. **Initial Exploration:**
    * **`.head()`:** Use  this Pandas function to view the first few rows of your dataset and get a sense of its structure.
    * **`.shape`:** Check the dimensions (rows, columns) of your dataset.
    * **`.info()`:** Get information about columns, data types, and any missing values.
    * **`.describe()`** : Obtain basic descriptive statistics (count, mean, standard deviation, etc.) for numerical columns.

3. **Handling Missing Values:**
    * **Identify:** Use `df.isnull().sum()` to count missing values in each column.
    * **Strategies:**
        * **Drop rows or columns:** If very few values are missing or columns are unimportant.
        * **Imputation:** Fill in missing values with techniques like: 
            * Mean/median imputation (numerical data)
            * Mode imputation (categorical data)
            * Predictive modeling to fill gaps more intelligently

4. **Correcting Errors:**
    * **Data type errors:** Use functions like `df['column'].astype('new_data_type')` to adjust data types if needed.
    * **Inconsistent formatting:** Find and fix inconsistent date formats, capitalization issues, typos or extra spaces that can cause problems for analysis. Regular expressions can be helpful here.
    * **Outliers:** Use box plots or statistical methods (e.g., z-scores) to identify potential outliers. Decide whether to remove them, transform them, or keep them if they are legitimate values.

5. **Feature Engineering (Optional):**
   * **Create new features:**  Derive new features from existing ones (e.g., calculating the age based on birthdate).
   * **Feature transformation:**  Apply scaling or normalization to numeric features for better performance of some machine learning models.
   * **Feature encoding:**   Convert categorical features into numeric format suitable for machine learning (e.g., one-hot encoding).

**Important Considerations**

* **Document Your Process** :  Keep notes on the changes you make to ensure reproducibility.
* **Iterative Process:** Data cleaning is rarely done in one pass. Expect to go back and forth as you discover more issues.
* **Context Matters:** Data cleaning techniques should be chosen with consideration of the dataset and your analysis goals. 

**Example with Pandas (Python)**

```python
import pandas as pd

# Load your dataset
df = pd.read_csv("your_dataset.csv") 

# Check for missing values
df.isnull().sum()

# Impute missing values (example)
df['column_with_missing'].fillna(df['column_with_missing'].mean(), inplace=True)

# Correct data type
df['column'] = df['column'].astype('int64') 
```

**Resources**

* **Kaggle's Data Cleaning Course:** [https://www.kaggle.com/learn/data-cleaning](https://www.kaggle.com/learn/data-cleaning)
* **Pandas Documentation:**  [https://pandas.pydata.org/](https://pandas.pydata.org/)


---
---
---
<br>
<br>
<br>
**Frequent asked interview questions**

**1. Handling Missing Values**

* **Why interviewers ask:** Dealing with missing data is a fundamental part of preparing a dataset, and your approach can significantly impact analysis outcomes.
* **Explanation:**
    * **Types of missing data:**
        * **Missing Completely at Random (MCAR):** No pattern to the missingness.
        * **Missing at Random (MAR):** Missingness depends on observed data (e.g., older individuals might be less likely to report income).
        * **Missing Not at Random (MNAR):** Missingness is related to the missing value itself (e.g., people with high income less likely to disclose it).
    * **Techniques:**
        * **Dropping:** Removing rows/columns with missing values (use cautiously)
        * **Imputation:** Filling in missing values with:
            * Mean/median/mode
            * Predictive models (e.g., KNN imputation)

**Code Example (Python - Imputation):**

```python
import pandas as pd
from sklearn.impute import SimpleImputer

df = pd.DataFrame({'Age': [25, None, 40], 'Income': [50000, 35000, None]})

imputer = SimpleImputer(strategy='mean')  # Use mean imputation
df_imputed = pd.DataFrame(imputer.fit_transform(df), columns=df.columns)
print(df_imputed)
```

**2. Outlier Detection & Treatment**

* **Why interviewers ask:** Outliers can skew results and need careful consideration before removal or modification.
* **Explanation:**
    * **Detection Methods:**
        * **Box plots:** Visualize distribution, outliers fall outside the box and whiskers.
        * **Z-scores:** Measure standard deviations from the mean. Points beyond a threshold (e.g., 3 standard deviations) might be outliers.
    * **Treatment:**
        * **Removal:** If outliers are due to errors.
        * **Capping/Winsorizing:** Replace outlier values with a percentile value.
        * **Transformation:**  Apply log transformation or similar.
        * **Keep:** If outliers are real data points, consider separate analysis or robust modeling techniques.

**3. Data Type Errors**

* **Why interviewers ask:** Correct data types are crucial for calculations, visualizations, and applying models.
* **Explanation:**
    *  Check data types using `df.info()` in Pandas.
    * **Examples of mismatches:**
        * Numeric values stored as strings.
        * Incorrect date formats.
* **Fixing errors:**
    * Use `.astype()` in Pandas to change data types.
    *  Use functions like `pd.to_datetime()` for date conversion.

**Code Example (Python - Correcting data type):**

```python
import pandas as pd

df = pd.DataFrame({'Price': ['10.50', '25', 'N/A'], 'Year': ['2022-12-20', '2021', 2023]})

df['Price'] = pd.to_numeric(df['Price'])  # Convert Price to numeric
df['Year'] = pd.to_datetime(df['Year'])   # Convert Year to datetime
```

**4. Data Inconsistency**

* **Why interviewers ask:** Consistent formatting and standardization are important for accurate analysis and merging datasets.
* **Explanation:** 
    * **Examples:**
        * Different units of measurement (feet vs. meters)
        * Inconsistent capitalization ("New York", "new york")
        * Variations in date formats
    * **Techniques:**
        * String methods (`.lower()`, `.upper()`)
        * Regular expressions for complex fixes
        * Datetime functions for date standardizations

