---
layout: post
title: "Pandas for Data Manipulation"
date: 2024-03-02
categories: machine learning
---

**What is Pandas?**

* **Python Data Powerhouse:** Pandas is a powerful Python library designed specifically for working with structured data. Think of it as your super-handy toolbox for organizing and manipulating data like you might work with a spreadsheet.
* **Data Structures:**  At its core, Pandas offers two main data structures:
    * **Series:** A one-dimensional array-like structure. Picture it as a single column in a spreadsheet.
    * **DataFrame:** A two-dimensional table-like structure. This is like your whole spreadsheet, with rows and columns.

**Why use Pandas?**

* **Ease of use:** It's built to make working with data intuitive and efficient. 
* **Handles Missing Data:** No more headaches with messy, real-world datasets. Pandas helps you fill in gaps and clean up inconsistencies.
* **Flexibility:** Load data from various formats (CSV, Excel, etc.), reshape it, slice it, dice it, and perform calculations.
* **Plays well with others:** Pandas integrates beautifully with other Python data science libraries like NumPy, Matplotlib, and Scikit-learn.

**Getting Started**

1. **Installation:** If you don't already have Pandas installed, the easiest way is using `pip`:
   ```bash
   pip install pandas
   ```

2. **Import:** In your Python script or notebook, start by importing Pandas:
   ```python
   import pandas as pd 
   ```
   We usually use "pd" as an abbreviation for Pandas.

**Basic Operations**

Let's create a small DataFrame to experiment with:

```python
data = {'Name': ['Alice', 'Bob', 'Charlie'],
        'Age': [25, 30, 28],
        'City': ['New York', 'Seattle', 'Los Angeles']}

df = pd.DataFrame(data)
print(df)
```

* **Explore:**
    * `df.head()`: Shows the first few rows of your DataFrame
    * `df.tail()`: Shows the last few rows
    * `df.info()`: Gives information about data types and any missing data
    * `df.shape`:  Tells you the number of rows and columns 

* **Accessing Data:**
    * `df['Age']`:  Select the 'Age' column as a Series.
    * `df.loc[1]`: Select the second row by its index.

**Next Steps: Master DataFrames and Series**

* **What is a Series?**
    * A one-dimensional array-like structure in Pandas.  Think of it like a single column from a spreadsheet.
    * A Series holds data of a consistent type (e.g., numbers, text, dates).

* **Creating a Series**
    * **From a list:**
        ```python
        import pandas as pd

        numbers = pd.Series([5, 12, -3, 20])
        print(numbers)
        ```
    * **From a dictionary:**
        ```python
        cities = pd.Series({'Berlin': 'Germany', 'Paris': 'France', 'Madrid': 'Spain'})
        print(cities)
        ```
        * Note: The keys of the dictionary become the index of the Series.

* **Selecting Data from a Series**
    * **By Index (Label):**
        ```python
        print(cities['Madrid'])  # Output: Spain
        ```
    * **By Position (`iloc`)**
        ```python
        print(numbers.iloc[2])  # Output: -3 (third element)
        ```

* **Basic Operations**
    * Series support calculations like you would with numbers:
        ```python
        squared = numbers * numbers
        print(squared)
        ```
    * You can change values within a Series:
        ```python
        cities['Paris'] = 'FRANCE'  # Changes the value
        ```

**II. DataFrames: The Heart of Pandas**

* **What is a DataFrame?**
    * Table-like data structure with rows and columns.
    * Each column is effectively a Series, but columns can be of different data types.

* **Creating DataFrames**
    * **From a dictionary of lists:**
        ```python
        data = {
            'Country': ['Japan', 'Italy', 'Brazil'],
            'Capital': ['Tokyo', 'Rome', 'Brasilia'],
            'Population (millions)': [126, 60, 212]
        }
        countries_df = pd.DataFrame(data)
        print(countries_df)
        ```

* **Selecting Data**
    * **Selecting a Column:**
        ```python
        capitals = countries_df['Capital']
        print(capitals)
        ```
    * **Selecting Rows:**
        * By Label (`loc`):
            ```python
            japan_data = countries_df.loc[0]  # Get the row with index label 0
            print(japan_data)
            ```
        * By Position (`iloc`):
            ```python
            second_row = countries_df.iloc[1]
            print(second_row)
            ```

* **Manipulating DataFrames** 
    * **Adding new columns:**
        ```python
        countries_df['Continent'] = ['Asia', 'Europe', 'South America']
        ```
   * **Performing calculations:**
        ```python
        gdp = countries_df['Population (millions)'] * 10000  # Let's imagine GDP calculation
        countries_df['GDP (hypothetical)'] = gdp
        print(countries_df)
        ```

**Data loading from files (CSV, Excel, etc.)**

**I. CSV Files: The Common Workhorse**

* **Understanding CSV:**
    * CSV stands for Comma-Separated Values.
    * It's a simple text format for representing table-like data. Each row is a line, and values within a row are separated by commas.

* **Loading with `pd.read_csv()`**

```python
import pandas as pd

# Assuming you have a file named 'weather_data.csv'
df = pd.read_csv('weather_data.csv')
print(df)
```

**Important Notes:**

* **Delimiter:** If your files use a separator other than a comma (like a semicolon), specify it in the `read_csv` function:
   ```python
   df = pd.read_csv('data.csv', delimiter=';')
   ```

* **Headers:** If your CSV file has the first row as column names, that's the default behavior. If not, use the `header=None` parameter.

* **Specifying Data Types:** For efficient analysis, you might want to force certain columns to be of specific data types:
   ```python
   df = pd.read_csv('data.csv', dtype={'Temperature': float, 'City': str})
   ```

**II. Excel Files: Spreadsheets Galore**

* **Loading with `pd.read_excel()`**

```python
df = pd.read_excel('sales_report.xlsx')
print(df)
```

**Things to Consider**

* **Sheet Name:** If your Excel file has multiple sheets:
   ```python
   df = pd.read_excel('sales_report.xlsx', sheet_name='2023-Q1')
   ```
* **Header Row:**  You can specify which row to use as headers:
    ```python
    df = pd.read_excel('data.xlsx', header=2)  # Use the third row as the header
    ```

**III. Other Supported Formats**

Pandas has excellent support for various formats. A few  examples:

* **JSON (`pd.read_json()`):** Read data from JSON files.
* **SQL Databases (`pd.read_sql()`):** Connect to databases and load tables.

**Practical Tips**

* **Finding Your Filepath:** If you're unsure of the correct file path, use Python's `os` module to help list files in a directory.
* **Documentation:** Always refer to the official Pandas documentation for the latest options and detailed explanations on `read_csv`, `read_excel`, and other loading functions. [https://pandas.pydata.org/docs/reference/io.html](https://pandas.pydata.org/docs/reference/io.html)

**Example: Loading a Real-World CSV**

Let's imagine you have a CSV dataset of soccer matches. Here's how you could load and start exploring:

```python
import pandas as pd

match_data = pd.read_csv('football_matches.csv')

# Initial peek at the data
print(match_data.head())

# Basic information about the DataFrame
print(match_data.info())
```

**I. Mastering Conditions**

Filtering means selecting rows of a DataFrame that meet specific criteria. Here's how we build conditions in Pandas:

* **Comparison Operators:**
    * `>` (greater than)
    * `<` (less than)
    * `>=` (greater than or equal to)
    * `<=` (less than or equal to)
    * `==` (equal to)
    * `!=` (not equal to)

* **Logical Operators**
    * `&` (and) - Combine multiple conditions. Both must be true.
    * `|` (or) - At least one of the combined conditions must be true.
    * `~` (not) - Invert a condition 

**II. Methods for Filtering**

1. **Boolean Indexing**

   * **How It Works**
      * You place a Series of True/False values next to the DataFrame.
      * Rows where the Series is 'True' are kept, and the rest are excluded.

   * **Example: Find all soccer matches where the home team scored more than 3 goals**
      ```python
      import pandas as pd

      # ... (Load your soccer dataset)

      high_scoring_games = df[df['Home Team Goals'] > 3]
      print(high_scoring_games)
      ```

2. **Using the `.query()` Method**

   * **Syntax:**  `df.query('your_condition_here')`
   * **Benefits:** Often more readable for complex conditions. It uses strings to build your conditions.

   * **Example: Find matches played on a weekend in the Premier League**
      ```python
      weekend_premier_league = df.query("Day == 'Saturday' or Day == 'Sunday' and League == 'Premier League'") 
      ```

**III.  Advanced Filtering Techniques**

* **Filtering by Multiple Columns:**
    ```python
    df[(df['Attendance'] > 50000 ) & (df['League'] == 'Bundesliga')]
    ```

* **Using String Methods**
    * **`.str.contains()`:** Find rows where a text column contains a substring.
       ```python
       df[df['Home Team'].str.contains('United')]  # Teams with "United" in their name
       ```

**Example: Soccer Filtering**

Let's use our soccer dataset from before and find:

* **Games with high attendance (over 60000):**
   ```python
   high_attendance_games = df[df['Attendance'] > 60000]
   ```

* **Premier League games played in London:**
   ```python
   london_derbies = df.query("League == 'Premier League' and (Home Team City == 'London' or Away Team City == 'London')")
   ```

**Important Notes**

* **Modifying the DataFrame:**  Filtering usually creates a _copy_ of your data. If you want to modify the original DataFrame, you'll often need to assign the result back to it.
   ```python
   df =  df[df['Attendance'] > 50000]  # Updates the original df 
   ```

**I. The Essence of `groupby()`**

1. **Split-Apply-Combine:**  The core principles behind grouped calculations are:
    * **Split:** `groupby()` divides your DataFrame into groups based on a column (e.g., 'Continent').
    * **Apply:** You apply a function (like `mean()`, `sum()`, etc.) to _each_ group.
    * **Combine:** Results from each group are combined back into a structured result.

2. **Syntax:**

   ```python
   grouped_data = df.groupby('Column_to_group_by')
   ```

   This creates a 'GroupBy' object – you haven't done any calculations yet!

**II. Applying Aggregation Functions**

Common aggregations to calculate statistics per group:

* `.mean()`: Get the average (mean) of a numeric column for each group.
* `.sum()`: Calculate the sum of a numeric column for each group.
* `.count()`: Count the number of rows within each group.
* `.min()`: Find the minimum value within each group.
* `.max()`: Find the maximum value within each group.

**Example: Average Population per Continent**

Let's use our 'countries_df' DataFrame from earlier:

```python
import pandas as pd

data = {
    'Country': ['Japan', 'Italy', 'Brazil', 'Germany', 'Canada'],
    'Capital': ['Tokyo', 'Rome', 'Brasilia', 'Berlin', 'Ottawa'],
    'Population (millions)': [126, 60, 212, 83, 38],
    'Continent': ['Asia', 'Europe', 'South America', 'Europe', 'North America']
}
countries_df = pd.DataFrame(data)

avg_pop_per_continent = countries_df.groupby('Continent')['Population (millions)'].mean()
print(avg_pop_per_continent)
```

**III. More Power with `groupby()`**

* **Multiple Columns:** Group by multiple columns for hierarchical breakdowns (e.g., average population per continent and then per year within each continent).

* **Custom Functions:** Use `apply()` and write your own functions to perform complex aggregations beyond what's built-in.  

**Example: Multiple Tasks with Countries**

```python
results = countries_df.groupby('Continent').agg(
              average_population = ('Population (millions)', 'mean'),
              total_countries = ('Country', 'count')
          )
print(results)
```

**Important Note:** Grouped calculations often lead to new structures. In our example, we get a Series where the index is the Continent and the values are the average populations.

**Important Note:** While Pandas has some built-in plotting functions,  Matplotlib is the powerhouse behind the scenes. You'll often see Matplotlib imported for more customization.

**I. Basic Plotting from DataFrames**

Pandas DataFrames have convenient `.plot()` methods that provide quick visualiztions. Here are some common plot types:

* **Line Plot (`kind='line'`)** 
   * Great for data over time.
   * Example:
      ```python
      import pandas as pd
      import matplotlib.pyplot as plt

      sales_data = pd.DataFrame({'Month': [1, 2, 3, 4], 'Sales': [50, 80, 60, 95]})
      sales_data.plot(x='Month', y='Sales', kind='line')
      plt.show()
      ```

* **Bar Plot (`kind='bar'`)**
   * Good for comparing categorical data.
   * Example:
      ```python
      attendance_per_team = df.groupby('Home Team')['Attendance'].mean()
      attendance_per_team.plot(kind='bar')
      plt.show()
      ```

* **Histogram (`kind='hist'`)**
   * Shows distribution of numerical data.
   * Example:
      ```python
      df['Home Team Goals'].plot(kind='hist')
      plt.show()
      ```

**II. Matplotlib for Customization**

For more control over your plots, here's how you directly leverage Matplotlib:

```python
import matplotlib.pyplot as plt

# ... Your DataFrame manipulations ...

# Create a figure and axis object
fig, ax = plt.subplots() 

# Plotting – Use the 'ax' object for bar, scatter, etc. plots
ax.bar(df['League'], df['Average Attendance']) 

# Customize the plot 
ax.set_xlabel('League')  
ax.set_ylabel('Average Attendance')
ax.set_title('Attendance Comparison across Leagues')

plt.show()
```

**III. Popular Plot Types**

* **Scatter Plots:** Explore relationships between two numerical columns.
* **Box Plots:** Visualize distributions and spot outliers.
* **Pie Charts:** Show proportions of a whole (use with caution, there are often better alternatives).

**Let's visualize your soccer data! Here are a few ideas:**

* Distribution of goals scored per match (histogram)
* Scatter plot of attendance vs. home team goals (is there a relationship?)
* Box plot to compare goal distributions across different leagues 

**Key Points**

* **Experiment:**  The best way to learn is by trying different plots.
* **Documentation:** Matplotlib's documentation is your friend for endless customization options: [https://matplotlib.org/](https://matplotlib.org/) 


**Resources:**

* **Pandas Documentation:** [https://pandas.pydata.org/docs/](https://pandas.pydata.org/docs/)
* **Interactive Tutorials:**  
    * [https://www.datacamp.com/courses/data-manipulation-with-pandas](https://www.datacamp.com/courses/data-manipulation-with-pandas) 
    * [https://www.analyticsvidhya.com/blog/2021/06/how-to-manipulate-data-using-pandas/](https://www.analyticsvidhya.com/blog/2021/06/how-to-manipulate-data-using-pandas/)

