[Practice NoteBook](https://github.com/ShuLaPy/ml-ds-learning/blob/main/pandas/Pandas%20Introduction.ipynb)

[Exercise NoteBook](https://github.com/ShuLaPy/ml-ds-learning/blob/main/pandas/pandas-exercises.ipynb)

Pandas is an open-source Python Library providing high-performance data manipulation and analysis tool using its powerful data structures.

This tool is essentially your data’s home. Through pandas, you get acquainted with your data by cleaning, transforming, and analyzing it.

For example, say you want to explore a dataset stored in a CSV on your computer. Pandas will extract the data from that CSV into a DataFrame — a table, basically — then let you do things like:

-   Calculate statistics and answer questions about the data, like
    -   What's the average, median, max, or min of each column?
    -   Does column A correlate with column B?
    -   What does the distribution of data in column C look like?
-   Clean the data by doing things like removing missing values and filtering rows or columns by some criteria
-   Visualize the data with help from Matplotlib. Plot bars, lines, histograms, bubbles, and more.
-   Store the cleaned, transformed data back into a CSV, other file or database


Import Pandas

```python
import pandas as pd
```


## Core components of pandas: Series and DataFrames

The primary two components of pandas are the `Series` and `DataFrame`.

A `Series` is essentially a column, and a `DataFrame` is a multi-dimensional table made up of a collection of Series.

![[serieas_dataframe.png]]

DataFrames and Series are quite similar in that many operations that you can do with one you can do with the other, such as filling in null values and calculating the mean.

### Series

Series is a one-dimensional labeled array capable of holding data of any type (integer, string, float, python objects, etc.). The axis labels are collectively called index.

`pandas.Series( data, index, dtype, copy)`

**data** - data takes various forms like ndarray, list, constants
**index** - Index values must be unique and hashable, same length as data. Default **np.arrange(n)** if no index is passed.
**dtype** - dtype is for data type. If None, data type will be inferred
**copy** - Copy data. Default False

[Series Explanation](https://www.tutorialspoint.com/python_pandas/python_pandas_series.htm)

```python
colors = pd.Series(["Red", "Green", "Blue"])
```

```python
colors
```

    0      Red
    1    Green
    2     Blue
    dtype: object

```python
cars = pd.Series(["Audi", "Ferrai", "BMW"])
cars
```

    0      Audi
    1    Ferrai
    2       BMW
    dtype: object

```python
import numpy as np
data = np.array(['a','b','c','d'])
s = pd.Series(data,index=[100,101,102,103])
```

	100  a
	101  b
	102  c
	103  d
	dtype: object

```python
data = {'a' : 0., 'b' : 1., 'c' : 2.}
s = pd.Series(data)
```

	a 0.0
	b 1.0
	c 2.0
	dtype: float64

```python
s = pd.Series(5, index=[0, 1, 2, 3])
print s
```

	0  5
	1  5
	2  5
	3  5
	dtype: int64

```python
#retrieve the first element
s[0]

#retrieve the first three element
s[:3]

#retrieve the last three element
s[-3:]

#Retrieve a single element using index label value.
s['a']

#Retrieve multiple elements using a list of index label values.
s[['a','c','d']]
```

### DataFrames

A Data frame is a two-dimensional data structure, i.e., data is aligned in a tabular fashion in rows and columns.

`pandas.DataFrame( data, index, columns, dtype, copy)`

**data** - data takes various forms like ndarray, series, map, lists, dict, constants and also another DataFrame.
**index**- For the row labels, the Index to be used for the resulting frame is Optional Default np.arange(n) if no index is passed.
**columns** - For column labels, the optional default syntax is - np.arange(n). This is only true if no index is passed.
**dtype** - Data type of each column.
**copy** - This command (or whatever it is) is used for copying of data, if the default is False.

[DataFrames Explanation](https://www.tutorialspoint.com/python_pandas/python_pandas_dataframe.htm)

![[pandas-anatomy-of-a-dataframe.png]]

A pandas DataFrame can be created using various inputs like −

-   Lists
-   dict
-   Series
-   Numpy ndarrays
-   Another DataFrame

```python
dataframes = pd.DataFrame({ "color": colors, "car": cars })
dataframes
```

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>color</th>
      <th>car</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Red</td>
      <td>Audi</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Green</td>
      <td>Ferrai</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Blue</td>
      <td>BMW</td>
    </tr>
  </tbody>
</table>
</div>

```python
data = {'Name':['Tom', 'Jack', 'Steve', 'Ricky'],'Age':[28,34,29,42]}
df = pd.DataFrame(data, index=['rank1','rank2','rank3','rank4'])
df
```

	         Age    Name
	rank1    28      Tom
	rank2    34     Jack
	rank3    29    Steve
	rank4    42    Ricky

```python
data = [{'a': 1, 'b': 2},{'a': 5, 'b': 10, 'c': 20}]
df = pd.DataFrame(data)
print df
```

	    a    b      c
	0   1   2     NaN
	1   5   10   20.0

**Column Operations**

```python
# select column
df['one']

# delete column
del df['one']
df.pop('two')

# add column
df['three']=pd.Series([10,20,30],index=['a','b','c'])
df['four']=df['one']+df['three']
```

**Row Operations**

```python
# select row
df.loc['b'] # Selection by Label
df.iloc[2]  # Selection by integer location

# Slice Rows
df[2:4]

# Addition of Rows
df = df.append(df2)

# Drop rows with label 0
df.drop(0)
```


### CSVs

Load CSV data

```python
# import data
car_sales = pd.read_csv("car-sales.csv")
```

```python
car_sales
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Make</th>
      <th>Colour</th>
      <th>Odometer (KM)</th>
      <th>Doors</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Toyota</td>
      <td>White</td>
      <td>150043</td>
      <td>4</td>
      <td>$4,000.00</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Honda</td>
      <td>Red</td>
      <td>87899</td>
      <td>4</td>
      <td>$5,000.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Toyota</td>
      <td>Blue</td>
      <td>32549</td>
      <td>3</td>
      <td>$7,000.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>BMW</td>
      <td>Black</td>
      <td>11179</td>
      <td>5</td>
      <td>$22,000.00</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Nissan</td>
      <td>White</td>
      <td>213095</td>
      <td>4</td>
      <td>$3,500.00</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Toyota</td>
      <td>Green</td>
      <td>99213</td>
      <td>4</td>
      <td>$4,500.00</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Honda</td>
      <td>Blue</td>
      <td>45698</td>
      <td>4</td>
      <td>$7,500.00</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Honda</td>
      <td>Blue</td>
      <td>54738</td>
      <td>4</td>
      <td>$7,000.00</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Toyota</td>
      <td>White</td>
      <td>60000</td>
      <td>4</td>
      <td>$6,250.00</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Nissan</td>
      <td>White</td>
      <td>31600</td>
      <td>4</td>
      <td>$9,700.00</td>
    </tr>
  </tbody>
</table>
</div>


### Describe Data

```python
# Attributes
car_sales.dtypes
```

	Make             object
	Colour           object
	Odometer (KM)     int64
	Doors             int64
	Price            object
	dtype: object

```python
car_sales.columns
# Index(['Make', 'Colour', 'Odometer (KM)', 'Doors', 'Price'], dtype='object')

car_sales.index
# RangeIndex(start=0, stop=10, step=1)

car_sales["Doors"].mean()
# 4.0

car_sales["Doors"].sum()
# 40

len(car_sales)
# 10

car_sales.info()
#  #   Column         Non-Null Count  Dtype
# ---  ------         --------------  -----
# dtypes: int64(2), object(3)
# memory usage: 528.0+ bytes
```

```python
# Functions
car_sales.describe() # give min max mean and other info of numerical data
```


### Selecting and Viewing data

```python
car_sales.head(5) # gives small snapshot of top 5 lines of the data
car_sales.tail(5) # gives small snapshot of bottom 5 lines of the data
```

```python
animals = pd.Series(["cat", "dog", "bird", "panda", "snake"], [0, 3, 9, 8, 5])
# 0      cat
# 3      dog
# 9     bird
# 8    panda
# 5    snake

animals.loc[3] # loc refers to the value of index
# 'dog'
animals.iloc[3] # iloc refers to the position of index
# panda
```

```python
car_sales[car_sales["Make"] == "Toyota"]
car_sales[car_sales["Odometer (KM)"] > 100000]
```


### Exernal Resources
---
- [Detailed NoteBook](https://github.com/mrdbourke/zero-to-mastery-ml/blob/master/section-2-data-science-and-ml-tools/introduction-to-pandas.ipynb)
- [10 minutes to pandas](https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html)
- [Essential basic functionality](https://pandas.pydata.org/pandas-docs/stable/user_guide/basics.html)
- [Pandas CheetSheet](https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf)

