```python
import pandas as pd
```

### Series

Series is 1-dimensional


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



### DataFrames

Dataframes are 2-dimesnional


```python
dataframes = pd.DataFrame({ "color": colors, "car": cars })
```


```python
dataframes
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



### CSVs


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




```python

```
