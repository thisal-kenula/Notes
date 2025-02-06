# Pandas

<aside>
💡

Learn From: [Non-null](https://www.w3schools.com/python/pandas/pandas_analyzing.asp#:~:text=Null%20Values)

</aside>

## Install

`pip install pandas`

## Series
- A series is like a column in a table

```python
import pandas as pd

a = [9, 7, 2]
myVar = pd.Series(a)

print(myVar)
'''
0    9
1    7
2    2
dtype: int64
'''
```

### Labels
- `Labels` are like indices for rows
- By default, labels are 0, 1, 2, …

```python
a = [9, 7, 2]
myVar = pd.Series(a)
print(myVar[0]) # 9
```

- Create labels
    
    ```python
    a = [9, 7, 2]
    myVar = pd.Series(a, index=['x', 'y', 'z'])
    print(myVar)
    '''
    x    9
    y    7
    z    2
    dtype: int64
    '''
    
    print(myVar['y']) # 7
    ```
    
    - Create using Key/value pairs
        - Keys become labels
        
        ```python
        calories = {'day1': 420, 'day2': 380, 'day3': 390}
        
        myvar = pd.Series(calories)
        
        print(myvar)
        '''
        day1    420
        day2    380
        day3    390
        dtype: int64
        '''
        ```
        
        - Select only some of the items
            
            ```python
            calories = {'day1': 420, 'day2': 380, 'day3': 390}
            
            myvar = pd.Series(calories, index = ['day2', 'day3'])
            
            print(myvar)
            '''
            day2    380
            day3    390
            dtype: int64
            '''
            ```
            
## DataFrames
- Series = column; DataFrame = table

```python
data = {
    "calories": [420, 380, 390],
    "duration": [50, 40, 45]
}

df = pd.DataFrame(data)

print(df)
'''
    calories  duration
0       420        50
1       380        40
2       390        45
'''
```

### Named indexes

```python
data = {
    "calories": [420, 380, 390],
    "duration": [50, 40, 45]
}

df = pd.DataFrame(data, index=['day1', 'day2', 'day3'])

print(df)
'''
        calories  duration
day1       420        50
day2       380        40
day3       390        45
'''
```

### Locate row

```python
# 0 = Row index
print(type(df.loc[0])) # Rertuns a series
'''
calories    420
duration     50
'''
```

- Multiple rows
    
    ```python
    # [0, 1] = Rows
    print(df.loc[[0, 1]]) # Rertuns a **DataFrame**
    '''
        calories  duration
    0       420        50
    1       380        40
    '''
    ```
    
- Locate named indexes
    
    ```python
    print(df.loc['day2'])
    '''
    calories    380
    duration     40
    '''
    ```
    
## Read CSV files
- `CSV`: Comma Separated Values

```python
df = pd.read_csv('data.csv')

print(df) # Print first and last five rows
```

### Full file path

```python
df = pd.read_csv('/Users/thisalkenula/Desktop/data.csv')
```

- Otherwise the file should be in current working directory
### Print entire DataFrame

```python

df = pd.read_csv('data.csv')

print(df.**to_string**())
```

### `max_rows`
- How much rows would be printed by default
- Check current value
    
    ```python
    print(pd.options.display.max_rows)
    ```
    
    - Ex: `60` means `print(df)` will print first and last 5 rows when there’s more than 60 rows
- Change `max-rows`
    
    ```python
    pd.options.display.max_rows = 9999
    ```
    
## Read JSON
- `JSON` = Python dictionary

```python
df = pd.read_json('/Users/thisalkenula/Desktop/data.json')

print(df)
```

### Print entire DataFrame

```python
print(df.to_string())
```

### DataFrame from Python dictionary

```python
data = {
    "Duration":{
    "0":60,
    "1":60,
    "2":60,
    "3":45,
    "4":45,
    "5":60
    },
    "Pulse":{
    "0":110,
    "1":117,
    "2":103,
    "3":109,
    "4":117,
    "5":102
    },
    "Maxpulse":{
    "0":130,
    "1":145,
    "2":135,
    "3":175,
    "4":148,
    "5":127
    },
    "Calories":{
    "0":409,
    "1":479,
    "2":340,
    "3":282,
    "4":406,
    "5":300
    }
}

df = pd.DataFrame(data)

print(df.to_string())
```

## Analyzing DataFrames
### `head`

```python
df = pd.read_csv('data.csv')
print(df.head(10)) # Print first 10 rows
```

### `tail`

```python
df = pd.read_csv('data.csv')
print(df.tail(5)) # Print last 5 rows
```

### `info`

```python
df = pd.read_csv('data.csv')

# Print info about the DataFrame
print(df.info())
```
