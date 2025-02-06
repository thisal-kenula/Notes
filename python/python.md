# Python

# Concepts

## Mutable: changeable

```python
# Variables are simply names that refer to objects in memory
# a=b always mean object a is an reference to object b

# Mutable
my_list = [1, 2, 3, 4]
my_list[2] = 5 # changes my_list
my_list_2 = my_list # my_list_2 is an reference to my_list
my_list_2[2] = 10 # also changes my_list
print(my_list) # [1, 2, 10, 4]

# Immutable
x = 10
y = x # y equals x
y = 50 # 50 is a newly created object. Now y is a reference to 50. 
        # y no longer refers to x
print(x) #10
```

## Polymorphism

```python
class Car:
  def __init__(self, brand, model):
    self.**brand** = brand
    self.model = model

  def move(self):
    print("Drive!")

class Boat:
  def __init__(self, brand, model):
    self.**brand** = brand
    self.model = model

  def move(self):
    print("Sail!")

class Plane:
  def __init__(self, brand, model):
    self.**brand** = brand
    self.model = model

  def move(self):
    print("Fly!")

car1 = Car("Ford", "Mustang")       #Create a Car class
boat1 = Boat("Ibiza", "Touring 20") #Create a Boat class
plane1 = Plane("Boeing", "747")     #Create a Plane class

for x in (car1, boat1, plane1):
  x.move()
```

## Code introspection

```python
help()
dir() 
hasattr() 
id() 
type() 
repr() 
callable() 
issubclass() 
isinstance() 
__doc__ 
__name__
```

### Usage

```python
# example
print(help(zip)) # will print help on `zip`
```

```python
def my_function():
    pass

print(my_function.__name__) # my_function
```

# Variables

## Make / Delete variables

```python
# Make variables
x, y, z  = 'Orange', 'Banana', 'Cherry'
x = y = z = 'Orange'

# Delete variables
x = 56
del x
# print(x) will cause an error
```

## Output

```python
x = "Python"
y = "is"
z = "awesome"
print(x, y, z)
# Same as
print(x + y + z)
```

## Scope

```python
#x and x are 2 seperate variables
x = 300 # global

def myfunc():
  x = 200 # local
  print(x) # 200

myfunc()

print(x) # 300
```

### Global Keyword

```python
def myfunc():
  global x # create global variable
  x = 300

myfunc()

print(x)
```

```python
x = 300

def myfunc():
  global x # access global variable
  x = 200

myfunc()

print(x)
```

### Nonlocal Keyword

The `nonlocal` keyword makes the variable belong to the outer function.

```python
def myfunc1():
  x = "Jane"
  def myfunc2():
    nonlocal x # variable of myfunc1
    x = "hello"
  myfunc2()
  return x

print(myfunc1())
```

## Type

### Get the type

```python
a = 'Thisal'
print(type(a)) # <class 'str'>
```

Check the type:

```python
x = 200
print(isinstance(x, int)) # True
```

### Casting (Setting specific data type)

```python
x = int(3.0)
print(x) # 3
```

### Change type

```python
x = 5
x = "Thisal" # is valid
```

### None

```python
def noReturn():
    pass

x = noReturn()
print(x) # None 
print(type(x)) # <class 'NoneType'>
```

## Strings/Characters

### `‘’` and `""`

```python
c = 5
x = str(c) # '5'
```

```python
x = 'Thisal'
# is same as
x = "Thisal"
```

### Quotes inside quotes

```python
print("'chatGPT' from OpenAI")
print('"chatGPT" from OpenAI')
```

### Multiline strings

```python
# This will be printed on multiple lines
a = """Lorem ipsum dolor sit amet,
consectetur adipiscing elit,
sed do eiusmod tempor incididunt
ut labore et dolore magna aliqua.""" # `'` can be used instead of `"`
```

- Single line of string in multiple lines of code
    
    ```python
    my_string = "This is a single-line **\**
    string created using multiple lines of code."
    
    print(my_string) # This is a single-line string created using multiple lines of code.
    ```
    
- Multiline string in single line of code
    
    ```python
    # \n is used to represent line breaks within the string.
    multiline_string = "This is**\n**a multiline**\n**string**\n**written**\n**in a single line"
    ```
    

### Iterable

```python
x = "Thisal"
print(x[0]) # T
```

- Loop through string
    
    ```python
    x = "Thisal"
    for letter in x:
        print(letter)
    ```
    
- Check if exist
    
    ```python
    x = "Thisal"
    print('This' in x) # True
    print('This' not in x) # False
    ```
    
- Slicing/ Range
    
    ```python
    x = "Thisal wrote this on May 18 Saturday"
    print(x[0:4]) # This
    print(x[0:4:2]) # Ti
    print(x[:4]) # This
    print(x[22:]) # ay 18 Saturday
    
    print(x[-8:-1]) # Saturda
    # x[0:6] = "Kenula" is not valid
    
    **# x[start: stop: step]**
    # including: start
    # not including: stop
    ```
    
- Easy way to reverse
    
    ```python
    name = 'thisal'
    print(name[::-1]) # lasiht
    ```
    

### Methods

```python
x = "Thisal"
print(print(ord('L'))) # 76 (Unicode number in Decimal)
print(len(x)) # 6
print(x.lower()) # thisal
print(x.upper()) # THISAL
print(x.replace('is', 'dh')) # Thdhal
print(x.split('al')) # ['This', ' Kenula']
```

```python
x = " Thisal"
print(x.strip()) #Thisal
```

### Variables inside strings

```python
x = 24
name = "Thisal"
# print(x + name) # is not valid
print(name, "is", x, "years old") # Thisal is 24 years old
print(f"{name} is {x} years old") # Thisal is 24 years old
txt = f"The price is {10 * 10} dollars" # The price is 100 dollars

print("{} is {} years old".format(name, x)) # Thisal is 24 years old
print("{**1**} is {**0**} years old".format(**x, nam**e))
print("**{nm}** is **{ag}** years old".format(**nm** = name, **ag** = x))

print('Name is **%s**'%name)
print('age is **%d**'%age)
```

- Modifiers
    
    ```python
    price = 59
    txt = f"The price is {price:.2f} dollars"
    print(txt) # The price is 59.00 dollars
    ```
    
    [🔗 More modifiers](https://www.w3schools.com/python/python_string_formatting.asp)
    

### Escape characters

```python
txt = "We are the so-called \"Vikings\" from the north."
```

## Numbers

```python
x = 5 # int
y = 4+2j # complex
z = 0.5 # float
print(x+z, x+y, y+z) # 5.5 (9+2j) (4.5+2j)
```

```python
x = 3E2
print(x) # 300.0
```

### Change type

```python
x = int(1.9) # 1 **(Not 2)**
x = int('1') # 1 # **Can fail if can't convert**
```

### abs

```python
abs(-5.5) # = 5.5
abs(3+4j) # Magnitude of the complex number = 5
```

### `eval`

```python
x = 50
eval('x+4-3') # 51
```

### `sum`

```python
sum([1, 2, 3]) # 6
sum(range(0,10)) # 45 # Use sum_n = n*(n+1)//2 instead
```

### Binary ↔︎ Decimal

- Decimal to binary
    
    ```python
    bin(10)# 0b1010 (<class 'str'>)
    ```
    
- Binary to decimal
    
    ```python
    int("1010", 2) # 10 int("number_str", base)
    ```
    
    - Hexadecimal and octal are valid as well

### infinity

`float('inf')`

### `decimal` module

- Useful for precise decimal floating-point arithmetic(financial, scientific etc.)

```python
from decimal import Decimal

x = Decimal('0.1')
y = Decimal('0.2')
print(x + y) # 0.3
```

- `float` won’t always precise results because they are represented in binary
    
    ```python
    x = 0.1 # n binary is approximately 0.000110011001100...(repeating).
    y = 0.2
    print(x + y) # 0.30000000000000004
    ```
    
- `float`
    - **very efficient** for computations
    - Part of **IEEE 754 standard**, widely adopted for consistency across hardware and software

## Booleans

```python
print(bool('Hello')) # True
print(bool('')) # False
print(bool(5)) # True
print(bool(0)) # False
# empty lists etc return false
```

### Also returns `false` if length of an object is 0

```python
class myclass():
    def __len__(self):
        return 0
    
myobj = myclass()
print(bool(myobj))
```

```python
stack = [5, 4, 3]
itemsThere = bool(stack)
print(itemsThere) # True
```

## Collections

### Methods

- `len`
    
    ```python
    len(thistuple)
    ```
    
- `join`
    
    Combine items of an iterable into single string
    
    ```python
    x = "s".join(['a', 'b', 'c', '1', '2'])
    print(x) # asbscs1s2
    ```
    
- `sorted`
    
    ```python
    list = [5,4,2,1,3]
    mytuple = tuple(sorted(list))
    print(mytuple) # (1, 2, 3, 4, 5)
    ```
    

### Allows different types

```python
list1 = ["abc", 34, True, 40, "male"] # is valid
```

### Create a collection

```python
thislist = list(("apple", "banana", "cherry"))
```

### Unpack a collection

```python
fruits = ["apple", "banana", "cherry"]
x, y, z = fruits
# x=apple, y=banana, z=cherry

fruits = ("apple", "banana", "cherry", "car")
x, ***y**, z = fruits
#x=apple, y=[banana,cherry, car]

math.lcm(*range(1, 11)) # Equivalent to math.lcm(1, 2, ..., 10)
```

### Check if an item exist

```python
my_list = [1, 2, 3, 4, 5]

# Check if item exists
if 3 in my_list:
    print("Item exists in the list")
```

### Lists

- Ordered
- changeable(mutable)
- Allow duplicates
- Access
    
    ```python
    thislist = ["apple", "banana", "cherry"]
    thislist[1:2] = ["blackcurrant", "watermelon"]
    print(thislist) #['apple', 'blackcurrant', 'watermelon', 'cherry']
    ```
    
    - Index out of range:
        
        ```python
        x = [1,2,3,4,5,6]
        
        print(x[10:11]) # []
        #print(x[10]) will cause error
        ```
        
- Methods
    
    ```python
    thislist = ["apple", "banana", "cherry"]
    
    # Add items
    thislist.insert(2, "watermelon") # ['apple', 'banana', 'watermelon', 'cherry']
    thislist.append("orange") #['apple', 'banana', 'cherry', 'orange']
    
    #Combine
    tropical = ["mango", "pineapple", "papaya"]
    thislist.extend(tropical) # ['apple', 'banana', 'cherry', 'mango', 'pineapple', 'papaya']
    thistuple = ("kiwi", "orange")
    thislist.extend(thistuple) # ['apple', 'banana', 'cherry', 'kiwi', 'orange']
    
    #Remove
    thislist.remove('apple') #['banana', 'cherry']
    thislist.pop(1) #['apple', 'cherry']
    del thislist[1] #['apple', 'cherry']
    a = thislist.pop() # a = "cherry"
    
    fruits = ["apple", "banana", "cherry", "kiwi", "mango", "apple"]
    fruits.remove('apple') # removes first 'apple'
    
    ```
    
    ```python
    #Clear
    thislist.clear() #[]
    ```
    
    [x = thisset.pop()](https://www.notion.so/Python-03ffc7f7b1e6427c87bb017f79121e11?pvs=21)
    
    - Count
        
        ```python
        fruits = ["apple", "banana", "cherry"]
        print(fruits.count('banana')) # 1
        ```
        
    - Sort
        
        ```python
        #Sort
        thislist.sort() # sorts the list alphanumerically, case sensitive(all capital ones come first)
        thislist.sort(reverse = True) # descending
        thislist.sort(key = str.lower) # case insensitive sort
        
        # Reverse list
        thislist.reverse()
        ```
        
        - Custom sort
            
            ```python
            def myfunc(n):
                return abs(n-50)
            
            thislist = [100, 50, 65, 82, 23]
            thislist.sort(key=myfunc) **# sorts the list ascending the return value of the function for each argument**
            # [50, 65, 23, 82, 100] 
            ```
            
    - Filter
        
        ```python
        # Define a function to filter even numbers
        def is_even(num):
            return num % 2 == 0
        
        # Create a list of numbers
        numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        
        # Use filter() to get even numbers from the list
        even_numbers = list(filter(is_even, numbers))
        
        print(even_numbers)  # Output: [2, 4, 6, 8, 10]
        ```
        
    - Index
        
        ```python
        fruits = ("apple", "banana", "cherry", "banana")
        print(fruits.index('banana')) #1
        ```
        
    - Copy
        
        ```python
        list2 = list1 # list2 is just another name for list1
        list2 = list1.copy() # creates a new list but still syncs with list1
        # deep copy to solve problem
        ```
        
        - Shallow and deep copy
            
            ```python
            import copy
            
            original = [[1, 2, 3], [4, 5, 6]]
            
            **# Shallow copy**
            shallow_copy = original.copy()
            shallow_copy[0].append(7)
            print(original)       # Output: [[1, 2, 3, **7**], [4, 5, 6]]
            print(shallow_copy)   # Output: [[1, 2, 3, 7], [4, 5, 6]]
            
            original = [[1, 2, 3], [4, 5, 6]]
            **# Deep copy**
            deep_copy = copy.deepcopy(original)
            deep_copy[0].append(8)
            print(original)       # Output: [[1, 2, 3], [4, 5, 6]]
            print(deep_copy)      # Output: [[1, 2, 3, 7, 8], [4, 5, 6]]
            ```
            
            - Manually
                
                ```python
                new_matrix = [row[:] for row in matrix]
                # using `row` instaed of `row[:]` will create 
                # shallow copies for each row even though the matrix 
                # is new
                ```
                
- List comprehension
    
    `[expression for item in iterable if condition==True]`
    
    ```python
    thislist = ["apple", "banana", "cherry"]
    [print(x) for x in thislist]
    '''
    apple
    banana
    cherry'''
    
    print([x for x in thislist]) # ['apple', 'banana', 'cherry']
    ```
    
    ```python
    fruits = ["apple", "banana", "cherry", "kiwi", "mango"]
    newlist = [x for x in fruits if 'a' in x] # ['apple', 'banana', 'mango']
    newlist = [x.upper() for x in fruits] #['APPLE', 'BANANA', 'CHERRY', 'KIWI', 'MANGO']
    newlist = ['hello' for x in fruits] #['hello', 'hello', 'hello', 'hello', 'hello']
    ```
    
    ```python
    newlist = [x for x in range(5)] # [0, 1, 2, 3, 4]
    ```
    
    - Set comprehension and Dictionary comprehension are also valid
    
- Multiply
    
    ```python
    fruits = ["apple", "banana", "cherry"]
    mylist = fruits * 2 # ['apple', 'banana', 'cherry', 'apple', 'banana', 'cherry']
    ```
    
    ```python
    x = [[0]*3]*3 # [[0, 0, 0], [0, 0, 0], [0, 0, 0]]
    x[0][0] = 1 # [[**1**, 0, 0], [**1**, 0, 0], [**1**, 0, 0]]
    # Use list comprehension when this is a problem
    ```
    
- Combine
    
    ```python
    list3 = list1+list2
    for x in list1: list2.append(x)
    ```
    

### Tuples

- Ordered
- **unchangeable(immutable)**(but set(list(set)) is allowed)
- Allow duplicates
- Used to store multiple items in a single variable
- Access just like lists
- Combine
    
    ```python
    thistuple = ("apple", "banana", "cherry")
    y = ("orange",) # comma is needed for a tuple with one item
    thistuple += y
    ```
    

### Set

- **Unordered**(unindexed), **unchangeable(mutable)(**but can remove and add**), No duplicates**
- Faster than other arrays
- Removes duplicates
    
    ```python
    thisset = {"apple", "banana", "cherry", "apple", True, 1}
    print(thisset) # {True, 'cherry', 'banana', 'apple'}
    # **True and 1(not other numbers) considered same value (also 0 and False))**
    ```
    
- [Methods](https://www.w3schools.com/python/python_ref_set.asp)
    - Add
        - Add new item
            
            `thisset.add("orange")`
            
        - Add new array
            
            ```python
            # Add new set
            thisset = {"apple", "banana", "cherry"}
            tropical = {"pineapple", "mango", "papaya"}
            thisset.update(tropical) #{'apple', 'pineapple', 'mango', 'cherry', 'papaya', 'banana'}
            
            # To a new set
            # set3 = set2 + set1 is not allowed
            set1 = {1, 2, 3}
            set2 = {4, 5, 6}
            set3 = set1.union(set2) # set1.union(set2, set3, set4)
            print(set3)  # Output: {1, 2, 3, 4, 5, 6}
            
            set3 = set1 | set2 # set1 | set2 | set3
            print(set3)  # Output: {1, 2, 3, 4, 5, 6}
            ```
            
            ```python
            #Add any iterable
            thisset = {"apple", "banana", "cherry"}
            mylist = ["kiwi", "orange"]
            
            thisset.update(mylist)
            
            # To a new set
            newset = thisset.union(mylist)
            ```
            
    - Keep only duplicates
        - Into a new set
            
            ```python
            set1 = {"apple", "banana", "cherry"}
            set2 = {"google", "microsoft", "apple"}
            
            set3 = set1.intersection(set2) # {'apple'}
            set3 = set1 & set2 # {'apple'}
            # &= valid
            ```
            
        - Into existing set
            
            ```python
            set1 = {"apple", "banana", "cherry"}
            set2 = {"google", "microsoft", "apple"}
            
            set1.intersection_update(set2) # set1 = {'apple'}
            ```
            
    - Difference
        
        > returns a new set with unique items in first set
        > 
        
        ```python
        # create new set
        set1 = {"apple", "banana", "cherry"}
        set2 = {"google", "microsoft", "apple"}
        
        set3 = set1.difference(set2) # {'cherry', 'banana'}
        set3 = set1 - set2 # {'cherry', 'banana'}
        
        #change existing set
        set1.difference_update(set2)
        ```
        
    - Symmetric difference
        
        > Removes common items
        > 
        
        ```python
        # To a new set
        set1 = {"apple", "banana", "cherry"}
        set2 = {"google", "microsoft", "apple"}
        
        set3 = set1.symmetric_difference(set2) #{'cherry', 'google', 'banana', 'microsoft'}
        set3 = set1 ^ set2 # Does the same
        
        #To an existing set
        set1.symmetric_difference_update(set2)
        ```
        
    - Remove item
        
        ```python
        thisset = {"apple", "banana", "cherry"}
        thisset.remove("banana") # Will raise an error if does not exist
        thisset.discard("banana") # Will not raise an error
        ```
        
        ```python
        thisset = ["apple", "banana", "cherry"]
        thisset.pop() # Will remove random item
        ```
        
        ```python
        thisset = {"apple", "banana", "cherry"}
        x = thisset.pop() # Removes and assigns the popped item
        print(x)
        ```
        
        - [Clear](https://www.notion.so/Python-03ffc7f7b1e6427c87bb017f79121e11?pvs=21)
    - [Filter](https://www.notion.so/Python-03ffc7f7b1e6427c87bb017f79121e11?pvs=21)

### Get a quick list of numbers

`list(range(10))` [0,1,2,3,4,5,…9]

### When a list grows beyond allocated memory

Python allocates a larger block of memory, copies the existing elements to the new block, and then adds the new elements. This reallocation follows an exponential growth strategy (ex. doubling) to minimize the frequency of such operations, ensuring that the average time complexity for adding an element remains efficient at O(1).

### Dictionaries

- Ordered
- Changeable(mutable)
- Duplicates not allowed(unique keys)
- Duplicates will override existing
    
    ```python
    thisdict = {
      "brand": "Ford",
      "model": "Mustang",
      "year": 1964,
      "year": 2020 # will replace 1964
    }
    ```
    
- Allows multiple types
    
    ```python
    mixed_dict = {
        1: "integer one",
        "1": "string one",
        2: "integer two"
    }
    ```
    
- Create
    
    `thisdict = dict(name = "John", age = 36, country = "Norway")`
    
- Access items
    
    ```python
    thisdict = {
      "brand": "Ford",
      "model": "Mustang",
      "year": 1964
    }
    x = thisdict["model"] # Mustang
    x = thisdict.get("model") # does the same
    ```
    
    - Get items
        
        ```python
        thisdict = {
        "brand": "Ford",
        "model": "Mustang",
        "year": 1964
        }
        x = thisdict.items()
        ```
        
        - Get keys
            
            `x = thisdict.keys()`
            
        - Get values
            
            ```python
            x = thisdict.values() #dict_values(['Ford', 'Mustang', 1964])
            ```
            
    - Add/Change items
        
        ```python
        car = {
        "brand": "Ford",
        "model": "Mustang",
        "year": 1964
        }
        car["year"] = 2020 # Will change the item
        car["color"] = "white" # Will add new attribute
        thisdict.update({"year": 2020})
        ```
        
    - Remove items
        
        ```python
        thisdict = {
          "brand": "Ford",
          "model": "Mustang",
          "year": 1964
        }
        thisdict.pop("model")
        thisdict.popitem() # removes last inserted item
        del thisdict["model"]
        thisdict.clear() # {}
        ```
        
    - Check if key exist
        
        ```python
        thisdict = {
        "brand": "Ford",
        "model": "Mustang",
        "year": 1964
        }
        print("Yes" if 'model' in thisdict else 'No') # Yes
        ```
        
- Loop
    
    ```python
    thisdict = {
      "brand": "Ford",
      "model": "Mustang",
      "year": 1964
    }
    for x in thisdict: print(x) # will print keys (thisdict.items also will)
    for x in thisdict.values: print(x) # will print values
    for x, y in thisdict.items(): print(x, y) # Will print keys and values
    ```
    
    - Loop through nested dictionaries
        - Example
            
            ```python
            myfamily = {
              "child1" : {
                "name" : "Emil",
                "year" : 2004
              },
              "child2" : {
                "name" : "Tobias",
                "year" : 2007
              },
              "child3" : {
                "name" : "Linus",
                "year" : 2011
              }
            }
            ```
            
        
        ```python
        for x, obj in myfamily.items():
          print(x)
        
          for y in obj:
            print(y + ':', obj[y])
        ```
        
- Copy
    
    [Copy](https://www.notion.so/Copy-e7f47aecb5a2476cae982b7eac519cfa?pvs=21) 
    
    ```python
    thisdict = {
      "brand": "Ford",
      "model": "Mustang",
      "year": 1964
    }
    mydict = dict(thisdict)
    ```
    
- Nested
    
    ```python
    myfamily = {
      "child1" : {
        "name" : "Emil",
        "year" : 2004
      },
      "child2" : {
        "name" : "Tobias",
        "year" : 2007
      },
      "child3" : {
        "name" : "Linus",
        "year" : 2011
      }
    }
    
    # can be also done by
    child1 = {
      "name" : "Emil",
      "year" : 2004
    }
    child2 = {
      "name" : "Tobias",
      "year" : 2007
    }
    child3 = {
      "name" : "Linus",
      "year" : 2011
    }
    
    myfamily = {
      "child1" : child1,
      "child2" : child2,
      "child3" : child3
    }
    ```
    
    - Access items
        
        ```python
        print(myfamily["child2"]["name"])
        ```
        
- Methods
    - `clear()`: Removes all the elements from the dictionary
    - `copy()`: Returns a copy of the dictionary
    - `fromkeys()`: Returns a dictionary with the specified keys and values
    - `get()`: Returns the value of the specified key
    - `items()`: Returns a list containing a tuple for each key-value pair
    - `keys()`: Returns a list containing the dictionary's keys
    - `pop()`: Removes the element with the specified key
    - `popitem()`: Removes the last inserted key-value pair
    - `setdefault()`: Returns the value of the specified key. If the key does not exist: inserts the key, with the specified value
    - `update()`: Updates the dictionary with the specified key-value pairs (Merge)
    - `values()`: Returns a list of all the values in the dictionary

# Basic Operations

## Sequence

```python
range(start : stop : step) 
# including: start
# not including: stop 
```

```python
lst = [0, 1, 2, 3, 4, 5]
lst[1:5:2] # [1, 3]
lst[3:] # [3, 4, 5]
lst[:-2] # [0, 1, 2, 3]
lst[:] # [0, 1, 2, 3, 4, 5]
lst[::2] # [0, 2, 4]
lst[::-1] # [5, 4, 3, 2, 1, 0]
```

## Pass

```python
if condition:
    # Placeholder for future code
    pass
```

## Operators

```python
#Arithmetic
print(5/3.3) #1.5151515151515151
print(5//3.3) #1.0
print(5%3) #2
print(5**3) #125

#Assignment
x = 5
x += 3 
print(x) #8
print(x:=8) # same as x=8 print(x)

#Logical operators: and, or, not 
print(True and False) #false

#Membership operators
print(5 not in [1,3,5]) # False

#Bitwise operators: & | ^ ~ << >>
print(4&2)# 10 AND 01 = 00 = 0
print(4<<2)# 100 add two 0s to left -> 10000 = 16
print(4>>2) # 100 shift two digits from right = 1 
```

### Precedence

1. await x
2. *
3. +x, -x, ~x
4. , @, /, //, %
5. +, -
6. <<, >>
7. &
8. ^
9. |
10. in, not in, is, is not, <, <=, >, >=, !=, ==
11. not x
12. and
13. or
14. if – else
15. lambda
16. :=

### Bitwise

- `&` : AND
- `|` : OR
- `^` : XOR
- `~` : NOT

## If else

### Use function as condition

```python
def myfunc():
    return True

if myfunc(): print('Yes!') # Yes!
```

### ‘is’ and ‘==’

- 'is' checks if the objects are same in memory
- '==' checks if they're equal. (Always use '==')

### Ternary operator

`value_if_true if condition else value_if_false`

```python
x = False
newlist = 'hello' if x else 'bye' # bye
```

### When only checks one condition of multiple

- `and`: Only checks the second condition if first is True
    
    ```python
    # Wouldn't cause error if A is false
    if A and 10/0: 
        print("Both A and B are true.")
    else:
        print("Either A is false or B is false.")
    ```
    
- `or`: Only checks second if first is false
    
    ```python
    # Wouldn't cause error if A is true
    if A or 10/0:
        print("Both A and B are true.")
    ```
    

## Loop

### Break

The break statement is used to stop the loop prematurely.

Example:

```python
i = 1
while i < 6:
  print(i)
  if i == 3:
    break
  i += 1
```

### Continue

The continue statement is used to stop the current iteration and continue with the next.

Example:

```python
i = 0
while i < 6:
  i += 1
  if i == 3:
    continue
  print(i)
```

### Else

The else statement can be used to run a block of code once when the condition is no longer true.

```python
i = 1
while i < 6:
  print(i)
  i += 1
else: # will not execute if loop was stopped by Break
  print("i is no longer less than 6")
```

### For

- Loop through a collection
    
    ```python
    thislist = ["apple", "banana", "cherry"]
    for x in thislist:
      print(x)
      
    # Loop through index numbers
    for i in range(len(thislist)):
      print(thislist[i])
    ```
    
- Loop specific number of times
    
    ```python
    for x in range(6):
      print(x) # 0 1 2 3 4 5 
    ```
    
    Can be iterated through a [custom range](https://www.notion.so/Python-03ffc7f7b1e6427c87bb017f79121e11?pvs=21)
    
- Loop through value and index at once
    
    ```python
    for j, val in enumerate(merged):
                    print("index: ", j)
                    print("value: ", val)
    ```
    
    - For multiple values
        
        ```python
        # bucket = [(1, 5), (4, 4), (5, 7)]
        for i, (k, v) in enumerate(bucket):
        ```
        
    - Start index
        
        ```python
        for j, val in enumerate(merged, 1):
        ```
        
        Will start from `1` instead of `0`
        

### While

While loops are used for repeated execution as long as a condition is met.

```python
i = 1
while i < 6:
  print(i)
  i += 1
```

- Loop through a list
    
    ```python
    thislist = ["apple", "banana", "cherry"]
    i = 0
    while i < len(thislist):
      print(thislist[i])
      i = i + 1
    ```
    

# Advanced Operations

## `divmod`

```python
quotient, remainder = divmod(10, 3)
print(quotient)  # Output: 3 (10/3=3)
print(remainder) # Output: 1 (10%3=1)
```

## `map`

`map(function, iterable)`

```python
numbers = [1, 2, 3, 4, 5]

doubled_numbers = map(lambda x:x*2, numbers)
print(type(doubled_numbers)) # <class 'map'>
print(list(doubled_numbers)) # [2, 4, 6, 8, 10]
```

### Multiple iterables

```python
circle_areas = [3.56773, 5.57668, 4.00914, 56.24241, 9.01344, 32.00013]

result = list(map(round, circle_areas, range(1, 7)))
#[3.6, 5.58, 4.009, 56.2424, 9.01344, 32.00013]
```

- Explanation
    - `round(3.56773, 1)` → 3.6
    - `round(5.57668, 2)` → 5.58
    - `round(4.00914, 3)` → 4.009
    - `round(56.24241, 4)` → 56.2424
    - `round(9.01344, 5)` → 9.01344

## `round`

```python
print(round(2.71828))  # Output: 3
print(round(2.71828, 3))  # Output: 2.718
print(round(3.6, 0))  # Output: 4.0

print(round(1234, -1))  # Output: 1230
print(round(1234, -2))  # Output: 1200
```

### bankers rounding (nearest even)

```python
print(round(2.5))  # Output: 2
print(round(3.5))  # Output: 4
```

## `zip`

```python
a = [1, 2, 3]
b = ['a', 'b', 'c']
print(list(zip(a, b)))
```

### `zip` creates an iterable

```python
a = [1, 2, 3]
b = ['a', 'b', 'c']
result = zip(a, b)  # Produces an iterator of tuples
for pair in result:
    print(pair)
# Output:
# (1, 'a')
# (2, 'b')
# (3, 'c')
print(list(result)) # this would print [] because all the items in `result` are already iterated
```

## `reduce`

```python
from functools import reduce

numbers = [3, 4, 6, 9, 34, 12]

def custom_sum(first, second):
    return first + second

result = reduce(custom_sum, numbers)
print(result) #68

# (((((3+4)+6)+9)+34)+12) = 68
```

### with initial value

```python
from functools import reduce

numbers = [3, 4, 6, 9, 34, 12]

def custom_sum(first, second):
    return first + second

result = reduce(custom_sum, numbers, 10)
print(result) # 78

# (((10+3)+4)+...)
```

## `all`

- Returns true if a condition is true for all elements in a list

```python
a = [1, 2, 3, 4, 5]
b = [1, 2, 3, 4, 5]
if all(a[i] == b[i] for i in range(len(a))):
    print("Yes")
```

# Functions

```python
def my_function(fname, lname): # 2 parameters
  print(fname + " " + lname)

my_function("Emil", "Refsnes") # will get an error if more or less arguments
```

## Call vs. reference function

```python
def greet():
    return "Hello, World!"

**# Calling the function greet()**
message = greet()
print(message)  # Output: Hello, World!

**# Assigning the function greet to a variable**
my_function = greet # Using the variable to call the function
message = my_function()
print(message)  # Output: Hello, World!
```

## Arguments

### Keyword and positional arguments

- Keyword arguments
    
    ```python
    def my_function(child3, child2, child1):
      print("The youngest child is " + child3)
    
    my_function(child1 = "Emil", child2 = "Tobias", child3 = "Linus")
    ```
    
- Keyword-only arguments
    
    ```python
    # parameters after the * are keyword-only
    def my_function(a, b, *, c, d):
        print(f"a: {a}, b: {b}, c: {c}, d: {d}")
    
    # Valid call with keyword-only arguments
    my_function(1, 2, c=3, d=4)
    # Output: a: 1, b: 2, c: 3, d: 4
    
    # Invalid call without keyword for keyword-only arguments
    my_function(1, 2, 3, 4)  # This will raise a TypeError
    ```
    
- Positional-only arguments
    
    ```python
    # Parameters before / are positional only
    def my_function(a, b, /, c, d):
        print(f"a: {a}, b: {b}, c: {c}, d: {d}")
    
    # Valid call with positional and keyword arguments
    my_function(1, 2, c=3, d=4)
    # Output: a: 1, b: 2, c: 3, d: 4
    
    # positional args shouldn't appear after keyword args
    ```
    
- Positional only with Keyword only
    
    ```python
    def my_function(a, b, /, *, c, d):
      print(a + b + c + d)
    
    my_function(5, 6, c = 7, d = 8)
    ```
    

### Arbitrary positional arguments(*args)

```python
def my_function(*kids): # kids becomes a tuple when multiple agrs passed
  print("The youngest child is " + kids[2])

my_function("Emil", "Tobias", "Linus")
```

### Arbitrary keyword arguments(**kwargs)

```python
def my_function(**kid): # kid receive a dictionary of arguments
  print("His last name is " + kid["lname"])

my_function(fname = "Tobias", lname = "Refsnes")
```

### Default parameter value

```python
def my_function(country = "Sri Lanka"):
  print("I am from " + country)

my_function("India") # I am from India
my_function() # I am from Sri Lanka
```

## Getter and Setter

```python
class MyClass:
    def __init__(self):
        self._my_property = 0

    **@property # getter**
    def my_property(self):
        **# Code to execute when a property is accessed**
        return self._my_property

    **@my_property.setter** 
    def my_property(self, value):
        **# Code to execute when property is changed**
        print("Property value changed to", value)
        self._my_property = value

# Usage
obj = MyClass()
obj.my_property = 10  # Output: Property value changed to 10
```

## Return values

### Terminates function

```python
def example():
    return 42
    print("This will never be printed")
```

- Exit a function
    
    ```python
    def early_exit():
        print("Before return")
        return
        print("After return") # Would never run
    ```
    

### Return multiple values

```python
def divide_and_remainder(a, b):
    return a // b, a % b

quotient, remainder = divide_and_remainder(10, 3)
```

## Recursion

```python
def factorial(n):
    if n == 0:
        return 1  # Base case(When func. should stop): 0! = 1
    else:
        return n * factorial(n - 1)  # Recursive case(Repeating part): n * (n-1)!

# Testing the factorial function
print(factorial(5))  # Output: 120
```

### Explanation

### How it Works:

Let's break down the call `factorial(5)`:

- `factorial(5)` calls `factorial(4)`.
- `factorial(4)` calls `factorial(3)`.
- `factorial(3)` calls `factorial(2)`.
- `factorial(2)` calls `factorial(1)`.
- `factorial(1)` calls `factorial(0)`.
- `factorial(0)` hits the base case and returns 1.

Then the recursion unwinds:

- `factorial(1)` returns `1 * 1 = 1`.
- `factorial(2)` returns `2 * 1 = 2`.
- `factorial(3)` returns `3 * 2 = 6`.
- `factorial(4)` returns `4 * 6 = 24`.
- `factorial(5)` returns `5 * 24 = 120`.

## Lambda functions

`lamda parameter : return_value`

```python
# Sort the list by age
people = [
    {'name': 'Alice', 'age': 25},
    {'name': 'Bob', 'age': 30},
    {'name': 'Charlie', 'age': 20}
]

def get_age(dic): return dic['age']

# instead of sort(key = get_age)
people.sort(key=lambda dic: dic['age']) 
```

### Multiple variables

```python
add = lambda x, y: x + y
print(add(2, 3))  # Output: 5
```

## Decorators

```python
def my_decorator(func): # Receives a function as argument
    def wrapper():
        print("Something is happening before the function is called.")
        func() # Call the original function
        print("Something is happening after the function is called.")
    return wrapper # should return the wrapper function

@my_decorator # Calls the decorator
def say_hello(): # Original function
    print("Hello!")

say_hello()
'''Output:
Something is happening before the function is called.
Hello!
Something is happening after the function is called.
'''
```

### This is same as without `@`

```python
def say_hello():
    print("Hello!")

say_hello = **my_decorator(say_hello)**

say_hello()

# Or just my_decorator(say_hello)()
```

### Decorator inside function

```python
def name(nm):
    def decorator(func):
        def wrapper():
            print(nm)
            func()
        return wrapper
    return decorator

@name('Thisal')
def say_hello():
    print("Hello!")

say_hello()
#Thisal
#Hello!
```

## Encapsulation

```python
class Person:
    def __init__(self, name):
        self.name = name # public 
        self.**__**age = 0 # private

    def year_passed(self):
        self.__age += 1

me = Person('Thisal')
me.year_passed # is allowed
**# print(me.age) will cause error**
```

# Classes and Objects

## Methods

### Double underscore methods

```python
class MyClass:
    def __init__(self, x):
        self.x = x  # Initializes the object with a value for 'x'
    
    def __repr__(self):
        return f"MyClass(x={self.x})"  # Returns an unambiguous string representation of the object
    
    def __str__(self):
        return f"This is MyClass with x={self.x}"  # Returns a readable string representation of the object
    
    def __len__(self):
        return len(str(self.x))  # Returns the length of the string representation of 'x'
    
    def __add__(self, other):
        return MyClass(self.x + other.x)  # Defines addition behavior when using the '+' operator
    
    def __eq__(self, other):
        return self.x == other.x  # Defines equality behavior when using the '==' operator
    
    def __lt__(self, other):
        return self.x < other.x  # Defines less than behavior when using the '<' operator
    
    def __gt__(self, other):
        return self.x > other.x  # Defines greater than behavior when using the '>' operator
```

- Usage
    
    ```python
    # Create instances of MyClass
    obj1 = MyClass(5)
    obj2 = MyClass(10)
    
    # Test dunder methods
    print(repr(obj1))  # Output: MyClass(x=5)
    print(str(obj1))   # Output: This is MyClass with x=5
    print(len(obj1))   # Output: 1 (length of '5' is 1)
    print(obj1 + obj2) # Output: MyClass(x=15)
    print(obj1 == obj2) # Output: False
    print(obj1 < obj2)  # Output: True
    print(obj1 > obj2)  # Output: False
    ```
    

### Object methods

```python
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

  **def myfunc(self):**
    print("Hello my name is " + self.name)

p1 = Person("John", 36)
**p1.myfunc()**
```

`self` is a reference to current instance. Any name instead of `self` can be used. But it has to be first parameter

## Properties

```python
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

p1 = Person("John", 36)
# Modify property
p1.age = 45 
# Delete Property
del p1.age
# Delete object
del p1
```

## Inheritance

```python
class Person: # Parent class 
  def __init__(self, fname, lname):
    # Parent properties
    self.firstname = fname
    self.lastname = lname

  # Parent methods
  def printname(self):
    print(self.firstname, self.lastname)

class Student(**Person**): **# Child class**
  def __init__(self, fname, lname, year): **# Overrides Parent's __init__**
    super().__init__(fname, lname) # same as Person.__init__(self, fname, lname) 
    self.graduationyear = year **# Child property**

  def welcome(self): **# Child Method**
    print("Welcome", self.firstname, self.lastname, "to the class of", self.graduationyear)

```

## Class objects are mutable

```python
# Example
class ListClass:
    def __init__(self) -> None:
        self.lst = [1, 2, 3]
    
    def copy_list(self):
        return self.lst.copy()

x = ListClass()
y = x.lst # y is a reference to x.lst
z = x.copy_list() # z is a new copy of x.lst
y.append(10) # this will change `x`
z.append(20) # this won't change `x`
print(x.lst) # [1, 2, 3, 10]
```

```python
# Example
class personClass:
    def __init__(self, name) -> None:
        self.name = name

def changeName(person: personClass):
    person.name = "Thisal"

x = personClass("Kenula")
changeName(x)
print(x.name) **# will print `Thisal`**
# If want to create a copy of `x`, a method should be 
# added in class like `copy` that returns self (y = x.copy())
```

## Enums

```python
**from enum import Enum**

class LockerState(**Enum**):
    closed = 0
    open = 1

a = LockerState.closed
print(a) # LockerState.closed
print(a.value) # 0
```

### `auto()`

```python
from enum import Enum, **auto**

class LockerState(Enum):
    closed = **auto()**
    open = auto()

a = LockerState.open
print(a.value) # 2
```

# Iterators

```python
mytuple = ("apple", "banana", "cherry") # is an iterable object
myit = iter(mytuple) # now myit is an **iterator**

print(next(myit))
print(next(myit)) 
print(next(myit))
```

- Protocol: `__iter__` and `__next__` methods

## Create an iterator

```python
class MyNumbers:
    def __iter__(self): 
        """
        Returns an iterator when called.
        This method is called to obtain an iterator from an iterable object.
        """
        self.a = 1
        return self

    def __next__(self):
        """
        Returns the next item in the sequence.
        This method is called to get the next value from the iterator.
        """
        x = self.a
        self.a += 1
        return x

myclass = MyNumbers()  # Creates an iterable object
myiter = iter(myclass)  # Creates an iterator
print(next(myiter)) # 1
print(next(myiter)) # 2
```

### Stop iteration

```python
  def __next__(self):
    if self.a <= 20:
      x = self.a
      self.a += 1
      return x
    else:
      raise StopIteration
```

# Generators

Iterate through a sequence without creating entire sequence at once

## Generator functions

```python
def simple_generator():
    yield 1
    yield 2
    yield 3

gen = simple_generator()

print(next(gen))  # Output: 1
print(next(gen))  # Output: 2
print(next(gen))  # Output: 3
```

### `yield`

`yield` pauses the function

```python
def my_numbers():
    a = 2
    while True:
        yield a
        print(a)
        a += 2

numbers = my_numbers()
print(next(numbers))
print(next(numbers))
'''Output:
2
2
4
'''
```

- How it works:
    
    **First Call to `next(numbers)`:**
    
    - The `next()` function is called on the generator object `numbers`.
    - The generator function `my_numbers` starts executing.
    - `a` is initialized to 2.
    - The loop starts, and the first `yield a` statement is executed, yielding the value 2.
    - The function's state is saved at this point, and control is returned to the caller with the value 2.
    
    **Second Call to `next(numbers)`:**
    
    - The `next()` function is called again on the generator object `numbers`.
    - The generator function resumes execution right after the `yield` statement.
    - The `print(a)` statement is executed, printing the current value of `a` (which is still 2 at this point).
    - `a` is incremented by 2, so `a` now becomes 4.
    - The loop continues, and the `yield a` statement is executed again, yielding the value 4.
    - The function's state is saved again at this point, and control is returned to the caller with the value 4.

## Generator Expressions

```python
gen = (x for x in range(3))
print(next(gen))  # Output: 0
print(next(gen))  # Output: 1
print(next(gen))  # Output: 2
```

# Closures

Functions can be assigned to variables

```python
def outer_function(x):
    def inner_function(y):
        return x + y
    **return inner_function**

closure = outer_function(2) # closure now holds inner function
                            # with the value of 5 instead of x
print(closure(5)) # 7
```

## Change x inside inner function

```python
def outer_function(x):
    def inner_function(y):
        nonlocal x # allows modifications of x
        x += 1
        return x + y
    return inner_function

closure = outer_function(2) # closure now holds inner function
                            # with the value of x = 5
print(closure(5)) # 7
print(closure(5)) # 9
```

## Return multiple functions

```python
def create_counter(initial_value=0):
    value = initial_value

    def increment(amount=1):
        nonlocal value
        value += amount

    def decrement(amount=1):
        nonlocal value
        value -= amount

    def get_value():
        return value

    **return increment, decrement, get_value**

# Usage
increment, decrement, get_value = create_counter(5)
print(get_value())  # Output: 5
increment()
print(get_value())  # Output: 6
decrement(2)
print(get_value())  # Output: 4
```

# Error handling

```python
try:
  print(x)
except NameError:
  print("Variable x is not defined")
except:
  print("Something else went wrong")
else:
  print("Nothing went wrong")
finally:
  print("The 'try except' is finished")
```

## Raise an error

```python
def check_positive_number(number):
    if number < 0:
        **raise ValueError**("The number must be positive.")
    return number

try:
    check_positive_number(-5)
except ValueError **as e**: # assigns error message to variable e
    print(f"An error occurred: {**e**}") 
```

## Custom error

```python
# Define a custom exception
class NegativeNumberError(Exception):
    def __init__(self, value):
        self.value = value
        self.message = f"Invalid input: {value} is a negative number."
        super().__init__(self.message)

# Function that raises the custom exception
def check_positive_number(number):
    if number < 0:
        raise NegativeNumberError(number)
    return number

# Example usage
try:
    check_positive_number(-5)
except NegativeNumberError as e:
    print(f"An error occurred: {e}")

```

# File Handling

## Working directory

```python
import os

# Print current working directory
print(os.getcwd())

# Change current working directory
os.chdir('/path/to/directory')
```

## `with`

```python
# Open file using with statement
with open('example.txt', 'r') as file:
    # Read the content of the file
    content = file.read()
    print(content)
# file will be automatically closed when the block is exited.
```

## Open

```python
# open a file
f = open("demofile.txt", "rt") # file in current working directory
# use path instead to open file in anywhere
# 'rt' is default. So it's not necessary here

'''modes:
"r" - Read - Default value. Opens a file for reading, error if the file does not exist
"a" - Append - Opens a file for appending, creates the file if it does not exist
"w" - Write - Opens a file for writing, creates the file if it does not exist
"x" - Create - Creates the specified file, returns an error if the file exists

"t" - Text - Default value. Text mode
"b" - Binary - Binary mode (e.g. images)
'''
```

- At specified location
    
    ```python
    file = open('/Users/kaushalyepalugaswewa/Desktop/data.json')
    ```
    

## Read

```python
file = open('/Users/kaushalyepalugaswewa/Desktop/data.json')
print(file.read()) # prints the whole thing
print(file.read(5)) # prints first five characters
print(file.readline()) # prints first line
print(file.readline()) # prints second line
```

## Close

```python
f = open("demofile.txt", "r")
print(f.readline())
**f.close()** # should always close to reduce problems
```

## Write

```python
file.**write**('Now the file has more content')
```

## Delete

```python
import os
os.remove('/Users/kaushalyepalugaswewa/Desktop/thisl.txt')
```

- Delete folder
    
    ```python
    import os
    
    os.**rmdir**('/Users/kaushalyepalugaswewa/Desktop/untitled folder')
    # only empty folders can be deleted
    ```
    

## Check if file exist

```python
import os

if os.path.exists('/Users/kaushalyepalugaswewa/Desktop/thisl.txt'):
    print('Yes')
```

# Modules

## Create

Just save a code with `.py` extension

## Use

```python
**import mymodule**

mymodule.greeting("Jonathan")
```

### Variables in modules

```python
# mymodule.py
person1 = {
  "name": "John",
  "age": 36,
  "country": "Norway"
}
```

```python
import mymodule

a = mymodule.person1["age"]
print(a)
```

### Renaming a module

```python
import mymodule **as mx**

a = mx.person1["age"]
print(a)
```

### List all functions and variables in a module

```python
import platform

x = **dir(platform)**
print(x)
```

### Import from module

```python
# mymodule.py
def greeting(name):
  print("Hello, " + name)

person1 = {
  "name": "John",
  "age": 36,
  "country": "Norway"
}
```

```python
**from mymodule import person1**
or
**import mymodule.person1**

print (person1["age"])
```

## Virtual environment

- Install libraries for a specific project(folder)
- For system-wide installations: Use Hombrew

### Example scenario (in Terminal)

1. Navigate to the folder you want
2. Create a virtual environment 
    
    ```bash
    python3 -m venv myenv
    ```
    
    This creates a directory called `myenv` inside that folder for virtual environment
    
3. Activate virtual environment(After navigating to directory)
    
    ```bash
    source myenv/bin/activate
    ```
    
4. Install packages
    
    ```bash
    pip install yt-dlp
    ```
    
5. Deactivate the virtual environment
    
    ```bash
    deactivate
    ```
[📂 **SymPy**](/sympy.md)

## `datetime`

```python
# Import the datetime module
import datetime

# Get the current date and time
current_datetime = **datetime.datetime.now**() # module.class.function
print("Current date and time: ", current_datetime)

# Get the current year
current_year = current_datetime.year
print("Current year: ", current_year)

# Get the current time
current_time = current_datetime.time()
print("Current time: ", current_time)

# Formatting date and time
formatted_datetime = current_datetime.**strftime**("%Y-%m-%d %H:%M:%S")
print("Formatted date and time: ", formatted_datetime)

# Get the weekday name
weekday_name = current_datetime.strftime("%A")
print("Weekday name: ", weekday_name)

```

[All legal formats →](https://www.w3schools.com/python/python_datetime.asp)

### String to datetime

```python
**from datetime import datetime**

date_string = "2023-05-21 15:30:00"

# Define the format of the string
date_format = "%Y-%m-%d %H:%M:%S"

# Convert the string to a datetime object
date_object = datetime.**strptime**(date_string, date_format) #datetime is a class in the datetime module 
```

### `time_difference`

```python
# result of two `datetime` objects subtracting is `**timedelta**` object
time_difference = event_datetime - current_time 

print('days: ', time_difference.days)

'''* time_difference.hours is not valid (days, seconds, microseconds only)
* time_difference.seconds returns seconds after substracting dates
(1day 1hour will return 3600seconds)
'''
hours, remainder = divmod(time_difference.seconds, 3600)
minutes, seconds = divmod(remainder, 60)

print(hours, ':', minutes, ':', seconds)
```

## `string`

```python
import string

characters = string.ascii_letters
print(characters) # abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
```

## `random`

```python
import random
# randrange(start, stop, step)
print(random.randrange(1,10)) # 1...9 **(Not including 10)**

# randint(start, stop)
****print(random.randint(1,10)) # 1..10 **Include 10**

x = random.choice([1,2,3,4,5])
print(x) 
```

## `math`

[🔗 All methods and constants](https://www.w3schools.com/python/module_math.asp)

## `json`

### Json to Python

```python
import json

# this can be a string of a dictionary, list etc.
x = '{ "name":"John", "age":30, "city":"New York"}'
y = json.loads(x) # json string to python
print(y[5])

y = json.**load**(file) # json file to python
```

### Python to json

```python
# a Python object (dict):
x = {
  "name": "John",
  "age": 30,
  "city": "New York"
}

# convert into JSON string:
y = json.dumps(x) # {"name": "John", "age": 30, "city": "New York"}
```

- Indent
    
    ```python
    y = json.dumps(x, indent=2)
    '''
    {
      "name": "John",
      "age": 30,
      "city": "New York"
    }
    '''
    ```
    
- Separators
    
    ```python
    y = json.dumps(x, separators=('. ',' = ')) 
    # {"name" = "John". "age" = 30. "city" = "New York"}
    ```
    
- Order
    
    ```python
    y = json.dumps(x, sort_keys=True) 
    # {"age": 30, "city": "New York", "name": "John"}
    ```
    

## `RegEx`

[🔗](https://www.w3schools.com/python/python_regex.asp) Used to work with strings(like searching, filtering, editing etc.)

## `itertools` : Generate permutations

```python
import itertools

items = ['A', 'B', 'C', 'D']

permutations = list(itertools.permutations(items))
for p in permutations:
    print(p)
```

# Tips / Tricks

## Transpose Matrix

```python
old_list = [[1, 2, 3], [3, 4, 6], [5, 6, 7]]
[list(x) for x in zip(*old_list)]
# [[1, 3, 5], [2, 4, 6], [3, 6, 7]]
```

# Documentation

[Learn More from GitHub](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

## In code

```python
class ExampleClass:
    """
    Represents an example class.
    
    Conventions:
        - Private attributes are prefixed with an underscore (e.g., _cache).
        - Method names ending with '_async' are intended for asynchronous use.

    Attributes:
        attribute1 (str): Description of attribute1.
        attribute2 (int): Description of attribute2 with default value.

    Methods:
        method1(param1): Brief description of what method1 does.
    """

    def __init__(self, attribute1, attribute2=0):
        """
        Initializes ExampleClass with the given attributes.

        Args:
            attribute1 (str): The first attribute.
            attribute2 (int, optional): The second attribute. Default is 0.
        
        Example:
        grph = Graph(8) # Creates a graph with 8 vertices
        """
        self.attribute1 = attribute1
        self.attribute2 = attribute2

    def method1(self, param1):
        """
        Performs a specific action.

        Args:
            param1 (type): Description of param1.

        Returns:
            type: Description of return value.
        """
        pass
```

# Conventions

Use `_` to indicate private attributes (of a Class) 

```python
self._adj_matrix = [[0] * size for _ in range(size)]
```

indicates `_adj_matrix` shouldn’t be changed outside the class