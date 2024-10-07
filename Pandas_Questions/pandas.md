# LeetCode Pandas Questions

This document contains a collection of DataFrame manipulation tasks solved using Pandas. Each task includes the problem statement, a brief description, and the solution code.

## Table of Contents

1. [Create DataFrame from a 2D list](#create-dataframe-from-a-2d-list)
2. [Calculate the number of rows and columns](#calculate-number-of-rows-and-columns)
3. [Select first 3 rows of a DataFrame](#select-first-3-rows-of-a-dataframe)
4. [Select specific student details](#select-specific-student-details)
5. [Create a new column based on another column](#create-a-new-column-based-on-another-column)
6. [Drop duplicate rows based on a column](#drop-duplicate-rows-based-on-a-column)
7. [Drop rows with missing values](#drop-rows-with-missing-values)
8. [Modify a column by multiplying values](#modify-a-column-by-multiplying-values)
9. [Rename columns](#rename-columns)
10. [Change column data type](#change-column-data-type)
11. [Fill missing values](#fill-missing-values)
12. [Concatenate DataFrames vertically](#concatenate-dataframes-vertically)
13. [Pivot DataFrame](#pivot-dataframe)
14. [Reshape DataFrame from wide to long format](#reshape-dataframe-from-wide-to-long-format)
15. [Filter and sort animals by weight](#filter-and-sort-animals-by-weight)

---

### 1. Create DataFrame from a 2D list

**Question**: Given a 2D list `student_data` containing student IDs and ages, create a DataFrame with columns `student_id` and `age` that maintains the order of the original list.

**Solution**:
```python
import pandas as pd

def createDataframe(student_data: List[List[int]]) -> pd.DataFrame:
    return pd.DataFrame(student_data, columns=['student_id', 'age'])
```

---

### 2. Calculate the number of rows and columns

**Question**: Given a DataFrame `players` with various columns, write a function to return the number of rows and columns as an array `[number of rows, number of columns]`.

**Solution**:
```python
import pandas as pd

def getDataframeSize(players: pd.DataFrame) -> List[int]:
    return [players.shape[0], players.shape[1]]
```

---

### 3. Select the first 3 rows of a DataFrame

**Question**: Given a DataFrame `employees`, write a function to select and display the first 3 rows.

**Solution**:
```python
import pandas as pd

def selectFirstRows(employees: pd.DataFrame) -> pd.DataFrame:
    return employees.head(3)
```

---

### 4. Select specific student details

**Question**: Given a DataFrame `students` with columns `student_id`, `name`, and `age`, write a function to select the name and age of the student with `student_id = 101`.

**Solution**:
```python
import pandas as pd

def selectData(students: pd.DataFrame) -> pd.DataFrame:
    return students.loc[students['student_id'] == 101, ['name', 'age']]
```

---

### 5. Create a new column based on another column

**Question**: Given a DataFrame `employees` with a `salary` column, write a function to create a new column `bonus` with doubled values in the `salary` column.

**Solution**:
```python
import pandas as pd

def createBonusColumn(employees: pd.DataFrame) -> pd.DataFrame:
    employees['bonus'] = employees['salary'] * 2
    return employees
```

---

### 6. Drop duplicate rows based on a column

**Question**: Given a DataFrame `customers` with columns `customer_id`, `name`, and `email`, write a function to remove duplicate rows based on the `email` column, keeping only the first occurrence.

**Solution**:
```python
import pandas as pd

def dropDuplicateEmails(customers: pd.DataFrame) -> pd.DataFrame:
    return customers.drop_duplicates(subset='email', keep='first')
```

---

### 7. Drop rows with missing values

**Question**: Given a DataFrame `students` with columns `student_id`, `name`, and `age`, write a function to remove rows where the `name` column has missing values.

**Solution**:
```python
import pandas as pd

def dropMissingData(students: pd.DataFrame) -> pd.DataFrame:
    return students.dropna(subset=['name'])
```

---

### 8. Modify a column by multiplying values

**Question**: Given a DataFrame `employees` with a `salary` column, write a function to modify the column by multiplying each salary value by 2.

**Solution**:
```python
import pandas as pd

def modifySalaryColumn(employees: pd.DataFrame) -> pd.DataFrame:
    employees['salary'] = employees['salary'] * 2
    return employees
```

---

### 9. Rename columns

**Question**: Given a DataFrame `students` with columns `id`, `first`, `last`, and `age`, write a function to rename these columns as `student_id`, `first_name`, `last_name`, and `age_in_years`.

**Solution**:
```python
import pandas as pd

def renameColumns(students: pd.DataFrame) -> pd.DataFrame:
    return students.rename(columns={
        'id': 'student_id',
        'first': 'first_name',
        'last': 'last_name',
        'age': 'age_in_years'
    })
```

---

### 10. Change column data type

**Question**: Given a DataFrame `students` with a column `grade` stored as floats, write a function to convert the `grade` column to integers.

**Solution**:
```python
import pandas as pd

def changeDatatype(students: pd.DataFrame) -> pd.DataFrame:
    students['grade'] = students['grade'].astype(int)
    return students
```

---

### 11. Fill missing values

**Question**: Given a DataFrame `products` with a column `quantity`, write a function to fill in the missing values as 0 in the `quantity` column.

**Solution**:
```python
import pandas as pd

def fillMissingValues(products: pd.DataFrame) -> pd.DataFrame:
    products['quantity'] = products['quantity'].fillna(0)
    return products
```

---

### 12. Concatenate DataFrames vertically

**Question**: Given two DataFrames `df1` and `df2` with identical columns, write a function to concatenate them vertically into one DataFrame.

**Solution**:
```python
import pandas as pd

def concatenateTables(df1: pd.DataFrame, df2: pd.DataFrame) -> pd.DataFrame:
    return pd.concat([df1, df2], ignore_index=True)
```

---

### 13. Pivot DataFrame

**Question**: Given a DataFrame `weather` with columns `city`, `month`, and `temperature`, write a function to pivot the data so that each row represents a month and each city is a separate column.

**Solution**:
```python
import pandas as pd

def pivotWeatherData(weather: pd.DataFrame) -> pd.DataFrame:
    return weather.pivot(index='month', columns='city', values='temperature')
```

---

### 14. Reshape DataFrame from wide to long format

**Question**: Given a DataFrame `report` with columns representing sales data per quarter for each product, write a function to reshape the data so each row represents sales data for a product in a specific quarter.

**Solution**:
```python
import pandas as pd

def meltTable(report: pd.DataFrame) -> pd.DataFrame:
    return report.melt(id_vars=['product'], var_name='quarter', value_name='sales')
```

---

### 15. Filter and sort animals by weight

**Question**: Given a DataFrame `animals` with columns `name`, `species`, `age`, and `weight`, write a function to list the names of animals that weigh more than 100 kilograms, sorted by weight in descending order.

**Solution**:
```python
import pandas as pd

def filterAndSortAnimals(animals: pd.DataFrame) -> pd.DataFrame:
    return animals[animals['weight'] > 100].sort_values(by='weight', ascending=False)[['name']]
```
