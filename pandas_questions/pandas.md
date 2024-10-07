# LeetCode Pandas Questions

This document contains a collection of DataFrame manipulation tasks that have been solved using Pandas. Each task includes the problem statement, a brief description, and the solution code.

## Table of Contents

1. [Create DataFrame from a 2D list](#create-dataframe-from-a-2d-list)
2. [Calculate number of rows and columns](#calculate-number-of-rows-and-columns)
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

**Description**: Create a DataFrame with columns `student_id` and `age` using a 2D list.

```python
import pandas as pd

def createDataframe(student_data: List[List[int]]) -> pd.DataFrame:
    return pd.DataFrame(student_data, columns=['student_id', 'age'])
```

---

### 2. Calculate number of rows and columns

**Description**: Calculate the number of rows and columns in a DataFrame and return the result as `[rows, columns]`.

```python
import pandas as pd

def getDataframeSize(players: pd.DataFrame) -> List[int]:
    return [players.shape[0], players.shape[1]]
```

---

### 3. Select first 3 rows of a DataFrame

**Description**: Display the first 3 rows of a DataFrame.

```python
import pandas as pd

def selectFirstRows(employees: pd.DataFrame) -> pd.DataFrame:
    return employees.head(3)
```

---

### 4. Select specific student details

**Description**: Select the name and age of the student with `student_id = 101`.

```python
import pandas as pd

def selectData(students: pd.DataFrame) -> pd.DataFrame:
    return students.loc[students['student_id'] == 101, ['name', 'age']]
```

---

### 5. Create a new column based on another column

**Description**: Create a `bonus` column by doubling the values in the `salary` column.

```python
import pandas as pd

def createBonusColumn(employees: pd.DataFrame) -> pd.DataFrame:
    employees['bonus'] = employees['salary'] * 2
    return employees
```

---

### 6. Drop duplicate rows based on a column

**Description**: Remove duplicate rows based on the `email` column, keeping only the first occurrence.

```python
import pandas as pd

def dropDuplicateEmails(customers: pd.DataFrame) -> pd.DataFrame:
    return customers.drop_duplicates(subset='email', keep='first')
```

---

### 7. Drop rows with missing values

**Description**: Remove rows with missing values in the `name` column.

```python
import pandas as pd

def dropMissingData(students: pd.DataFrame) -> pd.DataFrame:
    return students.dropna(subset=['name'])
```

---

### 8. Modify a column by multiplying values

**Description**: Multiply all values in the `salary` column by 2.

```python
import pandas as pd

def modifySalaryColumn(employees: pd.DataFrame) -> pd.DataFrame:
    employees['salary'] = employees['salary'] * 2
    return employees
```

---

### 9. Rename columns

**Description**: Rename the columns in the DataFrame according to the given specifications.

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

**Description**: Convert the `grade` column from float to integer.

```python
import pandas as pd

def changeDatatype(students: pd.DataFrame) -> pd.DataFrame:
    students['grade'] = students['grade'].astype(int)
    return students
```

---

### 11. Fill missing values

**Description**: Fill missing values in the `quantity` column with 0.

```python
import pandas as pd

def fillMissingValues(products: pd.DataFrame) -> pd.DataFrame:
    products['quantity'] = products['quantity'].fillna(0)
    return products
```

---

### 12. Concatenate DataFrames vertically

**Description**: Concatenate two DataFrames vertically into one.

```python
import pandas as pd

def concatenateTables(df1: pd.DataFrame, df2: pd.DataFrame) -> pd.DataFrame:
    return pd.concat([df1, df2], ignore_index=True)
```

---

### 13. Pivot DataFrame

**Description**: Pivot the `weather` DataFrame so that each row represents temperatures for a specific month, and each city is a separate column.

```python
import pandas as pd

def pivotWeatherData(weather: pd.DataFrame) -> pd.DataFrame:
    return weather.pivot(index='month', columns='city', values='temperature')
```

---

### 14. Reshape DataFrame from wide to long format

**Description**: Reshape the DataFrame from wide to long format, showing sales data for products per quarter.

```python
import pandas as pd

def meltTable(report: pd.DataFrame) -> pd.DataFrame:
    return report.melt(id_vars=['product'], var_name='quarter', value_name='sales')
```

---

### 15. Filter and sort animals by weight

**Description**: List the names of animals that weigh strictly more than 100 kilograms, sorted by weight in descending order.

```python
import pandas as pd

def filterAndSortAnimals(animals: pd.DataFrame) -> pd.DataFrame:
    return animals[animals['weight'] > 100].sort_values(by='weight', ascending=False)[['name']]
```
