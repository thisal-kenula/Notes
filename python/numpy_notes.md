# NumPy

[W3Schools](https://www.w3schools.com/python/numpy/default.asp)

Learn from: [Seaborn](https://www.w3schools.com/python/numpy/numpy_random_seaborn.asp#:~:text=Seaborn)

## Create `ndarray`

```python
import numpy as np

# Convert list, tuple or other array like object to ndarray
arr = np.array([1, 2, 3, 4, 5])

print(arr)
print(type(arr)) # ndarray
```

## Dimensions

```python
import numpy as np

d0 = np.array(1) # 0-D array
d1 = np.array([1, 2, 3]) # 1-D array
d2 = np.array([[1, 2], [3, 4]]) # 2-D array
# Any number of dimensions are possible
```

### Check the number of dimensions

```python
print(d2.ndim) # 2
```

### Define the number of dimensions

```python
# Define the number of dimensions
arr = np.array([1, 2, 3, 4], ndmin=5)

print(arr) # [[[[[1 2 3 4]]]]]
```

### All sub arrays should have same length

```python
arr = np.array([[1, 2, 3, 4], [5, 6, 7]]) # This raises an error
```

## Indexing

### Multi dimensional indexing

```python
>>> arr = np.array(0)
>>> print(arr)
0
```

```python
>>> arr = np.array([1, 2])
>>> print(arr[0])
1
```

```python
>>> arr = np.array([[1, 2], [3, 4]])
>>> print(arr[0, 1]) # similar to arr[0][1] in arrays
2
```

### Slicing

```python
arr = np.array([10, 20, 30, 40, 50])
print(arr[1:4])  # Output: [20 30 40]
```

- Multi dimensional slicing
    - Multi-dimensional indexing + Slicing
    
    ```python
    >>> arr2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
    >>> print(arr2d[:, 1:3])
    [[2 3]
        [5 6]
        [8 9]]
    >>> print(arr2d[0:2, 1:3])
    [[2 3]
        [5 6]]
    ```
    
- `[start:stop:step]`
    
    ```python
    arr = np.array([1, 2, 3, 4, 5])
    arr[::2] # [1, 3, 5]
    ```
    
### Fancy indexing

```python
>>> arr = np.array([10, 20, 30, 40, 50])
>>> print(arr[[1, 3, 4]])
[20 40 50]
```

### Boolean indexing

```python
>>> arr = np.array([10, 20, 30, 40, 50])
>>> condition = arr > 30 # Creates array [False, False, False, True, True]
>>> result = arr[condition]
>>> print(result)
[40 50]
```

or just

```python
>>> result = arr[arr > 30]
>>> print(result)
[40 50]
```

### Negative indexing

Just like Python arrays

## Data types

### Check data type

```python
arr = np.array([1, 2, 3, 4, 5])
print(arr.dtype) # int64
```

### Define data type/size

```python
arr = np.array([1, 2, 3, 4, 5], dtype='S') # S is for byte string
print(arr.dtype) # |S1
print(arr[0]) # b'1'
```

- Data types
    - `i` - integer
    - `b` - boolean
    - `u` - unsigned integer
    - `f` - float
    - `c` - complex float
    - `m` - timedelta
    - `M` - datetime
    - `O` - object
    - `S` - string
    - `U` - unicode string
    - `V` - fixed chunk of memory for other type ( void )
    - These data types slightly differ from default Python data types. Review before using
        - Ex: Python integers are `int64` but `i` integers are `int32`
- Define data size
    
    ```python
    arr = np.array([1, 2, 3, 4, 5], dtype='i4')
    # i4 means 4 bytes integer (int 32)
    ```
    
    - `i8` for `int64`
    - Size can be defined for `i`, `u`, `f`, `S` and `U`

### Convert data type

```python
arr = np.array([1.1, 2.1, 3.6])
newarr = arr.astype(int) # or arr.astype('i')
print(newarr.dtype) # int32
print(newarr) # [1 2 3]
```

- When can’t convert: `ValueError`

## Copy & View

### `copy`: Creates a new copy

```python
arr = np.array([1, 2, 3, 4, 5])
x = arr.copy()
arr[0] = 42
x[1] = 42
print(arr) # [42  2  3  4  5]
print(x) # [ 1 42  3  4  5]
```

### `view` : Creates a reference

```python
arr = np.array([1, 2, 3, 4, 5])
x = arr.view()
arr[0] = 42
x[1] = 42
print(arr) # [42 42  3  4  5]
print(x) # [42 42  3  4  5]
```

### Check if array owns its data

```python
arr = np.array([1, 2, 3, 4, 5])

x = arr.copy()
y = arr.view()

print(x.base) # None
print(y.base) # [1 2 3 4 5]
```

- Prints `None` if it owns the data

## Shape
### Number of elements in each dimension

```python
arr = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])
print(arr.shape)  # (2, 4)
# 2 in the first dimension and 4 in the second dimension
# or Rows, Columns for 2D matrix
```

### Reshape

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]) # 1D array
arr = arr.reshape(4, 3) # Reshape the array to 4x3
print(arr)
'''
[[ 1  2  3]
    [ 4  5  6]
    [ 7  8  9]
    [10 11 12]]
'''
```

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]) # 1D array
arr = arr.reshape(2, 3, 2) # 3D array
```

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]) # 1D array
arr = arr.reshape(5, 3) # ValueError
```

- `reshape` returns a view
    
    ```python
    arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]) # 1D array
    arr = arr.reshape(3, 4) # 2D array; 
    # arr still points to the original data
    print(arr.base) # [1 2 3 4 5 6 7 8 9 10 11 12]
    ```
    
    - Use `arr.reshape(3, 4).copy()` to create a copy
- Unknown dimension
    
    ```python
    arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]) # 1D array
    arr = arr.reshape(2, 2, -1) # NumPy will calculate the relevant number
    print(arr.shape) # (2, 2, 3)
    ```
    
- Flattening the arrays
    
    ```python
    arr = np.array([[1, 2, 3], [4, 5, 6]])
    newarr = arr.reshape(-1)
    print(newarr) # [1 2 3 4 5 6]
    ```
    
## Iterating

### Like Python arrays

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])

for x in arr:
    print(x)

'''
[1 2 3]
[4 5 6]
'''
```

### `nditer()`
- Iterate on each scalar element
    
    ```python
    arr = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
    
    for x in np.nditer(arr):
        print(x, end=' ') # 1 2 3 4 5 6 7 8
    ```
    
- Iterate with different data type
    
    ```python
    arr = np.array([1, 2, 3])
    
    for x in np.nditer(arr, op_dtypes=float, flags=['buffered']):
        print(x, end=' ') # 1.0 2.0 3.0
    ```
    
    - This doesn’t change the original array. `buffered` is required to store the changed data temporarily
- Iterate with different step size
    
    ```python
    arr = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])
    
    for i in np.nditer(arr[:, ::2]):
        print(i) # 1 3 5 7
    ```
    
- Enumerate
    
    ```python
    arr = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])
    
    for i, val in np.ndenumerate(arr):
        print(i, val)
    
    '''
    (0, 0) 1
    (0, 1) 2
    (0, 2) 3
    (0, 3) 4
    (1, 0) 5
    (1, 1) 6
    (1, 2) 7
    (1, 3) 8
    '''
    ```
    
## Join arrays

### Concatenate

```python
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

arr3 = np.concatenate((arr1, arr2))
print(arr3) # [1 2 3 4 5 6]
```

- Axis
    - Axis = which dimension to extend
    - All other dimensions must match in size
    - Default = `0`
    
    ```python
    a = np.array([[[1, 2], [3, 4]]]) # Shape: (1, 2, 2)
    b = np.array([[[5, 6], [7, 8]]]) # Shape: (1, 2, 2)
    ```
    
    ```python
    c = np.concatenate((a, b), axis=0) # Shape (1+1, 2, 2)
    '''
    [[[1 2]
        [3 4]]
    
        [[5 6]
        [7 8]]]
    '''
    ```
    
    ```python
    c = np.concatenate((a, b), axis=1) # Shape (1, 2+2, 2)
    '''
    [[[1 2]
        [3 4]
        [5 6]
        [7 8]]]
    '''
    ```
    
    ```python
    c = np.concatenate((a, b), axis=2) # Shape (1, 2, 2+2)
    '''
    [[[1 2 5 6]
        [3 4 7 8]]]
    '''
    ```
    
    ```python
    c = np.concatenate((a, b), axis=None) # Shape (Number of all scalars)
    '''
    [[[1 2 5 6]
        [3 4 7 8]]]
    '''
    ```
    
### Stack
- Same as concatenate, but done along a new axis

```python
a = np.array([[[1, 2], [3, 4]]]) # Shape: (1, 2, 2)
b = np.array([[[5, 6], [7, 8]]]) # Shape: (1, 2, 2)

arr = np.stack((a, b), axis = 1) # Shape: (1, 2, 2, 2)
'''
[[[[1 2]
    [3 4]]

    [[5 6]
    [7 8]]]]
'''
```

### Stack along rows columns and depth

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
```

- Rows
    
    ```python
    arr = np.hstack((a, b))
    '''
    [1 2 3 4 5 6]
    '''
    ```
    
- Columns
    
    ```python
    arr = np.vstack((a, b))
    '''
    [[1 2 3]
        [4 5 6]]
    '''
    ```
    
- Height(depth)
    
    ```python
    arr = np.dstack((a, b))
    '''
    [[[1 4]
        [2 5]
        [3 6]]]
    '''
    ```
    
## Splitting

```python
a = np.array([1, 2, 3, 4, 5, 6])

arr = np.array_split(a, 3) # returns a list of arrays
print(arr) # [array([1, 2]), array([3, 4]), array([5, 6])]
print(arr[0]) # [1 2]
```

### When the array has less elements than required

```python
#It will adjust from the end accordingly
arr = np.array_split(a, 4) 
print(arr) # [array([1, 2]), array([3, 4]), array([5]), array([6])]
```

### `split`

```python
a = np.array([1, 2, 3, 4, 5, 6])

arr = np.split(a, 3) # [array([1, 2]), array([3, 4]), array([5, 6])]

arr = np.split(a, 4) # Raises an error
```

### Axis

```python
arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12], [13, 14, 15], [16, 17, 18]])

newarr = np.array_split(arr, 3)

print(newarr[0])
'''
[[1 2 3]
    [4 5 6]]
'''

newarr = np.array_split(arr, 3, axis=1) # Splits along the row
print(newarr[0])
'''
[[ 1]
    [ 4]
    [ 7]
    [10]
    [13]
    [16]]
'''
```

- `hsplit`
    
    ```python
    newarr = np.hsplit(arr, 3) # Same as `axis = 1` with `array_split`
    ```
    
- `vsplit` and `dsplit` also exist

## Searching
### Find the indexes where

```python
arr = np.array([1, 2, 3, 4, 5, 4, 4])

# Find the indexes where the value is 4:
x = np.where(arr == 4) # (array([3, 5, 6]),)
```

- Find the indexes where the values are even
    
    ```python
    # Find the indexes where values are even:
    x = np.where(arr%2 == 0) # (array([1, 3, 5, 6]),)
    ```
    
### `search sorted`
- Perform a binary search and return the index where the specified value **should be inserted** to maintain search order
- Assumed to do on sorted arrays

```python
arr = np.array([6, 7, 9, 10])

x = np.searchsorted(arr, 8)

print(x) # 2
```

- Search from the right side
    - Get the rightmost index
    
    ```
    arr = np.array([6, 7, 8, 9])
    
    x = np.searchsorted(arr, 7, side='right') # 2
    # Without side='right', it will return 1
    ```
    
- Multiple values
    
    ```python
    arr = np.array([1, 3, 5, 7])
    
    x = np.searchsorted(arr, [2, 4, 6]) 
    
    print(x) # [1 2 3]
    ```
    
## Sorting

- Returns a copy of the array(original not modified)

```python
arr = np.array([3, 2, 0, 1])

print(np.sort(arr)) # [0 1 2 3]
print(arr) # [3 2 0 1]
```

- Other data types (string, boolean) are also possible

### Sorting 2D arrays
- Both arrays will be independently sorted

```python
arr = np.array([[3, 2, 4], [5, 0, 1]])
print(np.sort(arr))
'''
[[2 3 4]
    [0 1 5]]
'''
```

## Filtering

```python
arr = np.array([41, 42, 43, 44])

x = [True, False, True, False]

newarr = arr[x]

print(newarr) # [41 43]
```

### Common usage

```python
arr = np.array([41, 42, 43, 44])

x = [i%2==1 for i in arr]

newarr = arr[x]

print(newarr) # [41 43]
```

- Even better
    
    ```python
    arr = np.array([41, 42, 43, 44])
    
    x = arr%2 == 1 # [ True False  True False]
    
    new_arr = arr[x]
    print(new_arr) # [41 43]
    ```
    

## **Random**

### Generate random number

```python
from numpy import random

# Generate random int in range(0, 100) 
x = random.randint(100)
```

```python
# Generate random float in range(0.0, 1.0) 
x = random.rand()
```

### Generate array

```python
# Generate a 1-D array with 5 integers
x = random.randint(100, size=(5))
```

- 2D array
    
    ```python
    # Generate a 2-D array with 3 rows containing 5 numbers
    x = random.randint(100, size=(3, 5))
    '''
    [[60 79 73 50 93]
        [51 29 61 53 32]
        [39 30 30  2 32]]
    '''
    ```
    
- Floats
    
    ```python
    # Generate a 1-D array with 5 floats
    x = random.rand(5)
    '''
    [0.42355618 0.90319025 0.03151179 0.0785196  0.99553938]
    '''
    ```
    
    - 2D array
        
        ```python
        # Generate a 2-D array with with 3 rows containing 5 numbers
        x = random.rand(3, 5)
        ```
        
### Choose from array

```python
x = random.choice([3, 5, 7, 9])
```

- Choose array of values
    
    ```python
    x = random.choice([3, 5, 7, 9], size=(3, 5))
    '''
    [[3 3 9 7 9]
        [7 5 9 7 7]
        [5 7 9 5 5]]
    '''
    ```
    
### Random Data Distribution

```python
# `p` is the probability of each element
# sum of all probabilities should be 1
x = random.choice([3, 5, 7, 9], p=[0.1, 0.3, 0.6, 0.0], size=(100))
```

### Permutations
- `shuffle` : Shuffles the original array
- `permutation` : Generates a permutation without affecting the original
- Shuffle array
    
    ```python
    from numpy import random
    import numpy as np
    
    arr = np.array([1, 2, 3, 4, 5])
    
    random.shuffle(arr)
    
    print(arr) # [3 2 1 4 5]
    ```
    
- Generate a permutation
    
    ```python
    from numpy import random
    import numpy as np
    
    arr = np.array([1, 2, 3, 4, 5])
    
    print(random.permutation(arr)) # [2 1 5 3 4]
    ```



