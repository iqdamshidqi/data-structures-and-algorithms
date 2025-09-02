# **🚀 A Quick Review of Pyhton! 🐍**

## **✍️ Leaving Notes**

Imagine you're writing a complex recipe. You might add little notes like "don't overmix\!" or "preheat the oven first." In programming, these notes are called **comments**. Comments help you (and others) understand what your code is trying to do.

Python will completely ignore any text that starts with a `#` symbol.

### **Single-Line Comments**

You can place a comment on its own line or right after a line of code.

```python
# This is a 1-line comment.
print("Hello, World!") # This comment is on the same line as the code.
```

### **Multi-Line Comments**

For longer notes, you can either use a `#` on each line or wrap your text in triple quotes (`'''` or `"""`). This is very useful for detailed explanations.

```python
# This is a comment
# written in
# more than just one line.
print("Hello, World!")
```

```python
'''
This is also a multi-line comment
using triple single quotes.
This method is often used for "docstrings,"
which are documentation for functions or classes.
'''
print("Hello, World!")
```

-----

## **📦 Storing Information**

Think of a **variable** as a labeled box where you can store information. You give the box a name (the **variable name**) and put something inside it (the **value**).

```python
# Variables do not need to be declared with any particular type
X = 1       # An integer data type
x = 2       # Variables are case-sensitive, so X and x are different
y = "Klein" # A string data type

print(X)
print(x)
print(y)
```

### **Rules for Naming Your "Boxes" ❗**

There are a few important rules when naming your variables:

1.  A variable name must start with a **letter** or an **underscore** (`_`).
2.  A variable name **CANNOT** start with a number.
3.  A variable name can only contain **alpha-numeric** characters and **underscores** (A-z, 0-9, and \_).
4.  Variable names are **case-sensitive** (`age`, `Age`, and `AGE` are three different variables).
5.  A variable name cannot be any of [Python's reserved keywords](https://www.w3schools.com/python/python_ref_keywords.asp) (e.g., `if`, `for`, `while`).

### **Casting: Specifying a Data Type**

Sometimes, you want to ensure a variable has a specific data type. This process is called *casting*.

```python
x = str(3)    # x will be '3' (a string)
y = int(3)    # y will be 3 (an integer)
z = float(3)  # z will be 3.0 (a float)

print(x, y, z)
print(type(x))
print(type(y))
print(type(z))
```

> **Important:** Variables in Python are dynamic. This means you can change their type at any time.

```python
x = 3 # x is an integer
print(x, type(x))

x = "Moretti" # Now, x is a string
print(x, type(x))
```

### **Multiple Ways to Assign Variables**

Python is very flexible in how you can assign values to variables.

```python
# Unpack a collection
fruits = {"apple", "banana", "cherry"}
x, y, z = fruits
print(x)
print(y)
print(z)

# Assign values to multiple variables at once
x, y, z = "Orange", "Banana", "Cherry"
print(x, y, z)

# Assign one value to multiple variables
x = y = z = "Orange"
print(x, y, z)
```

-----

## **🖨️ Printing Output: `print()` and Formatting**

The `print()` function is your best friend for displaying information. There are several ways to combine variables with text.

### **Combining Variables**

You can use a comma (`,`) or a plus sign (`+`).

```python
x = "Python"
y = "is"
z = "awesome"
# The comma automatically adds a space
print(x, y, z)

# The plus sign directly joins the strings (concatenation)
print("Python " + "is " + "awesome")
```

> **Warning:** Using `+` only works if all variables are of the same data type.

```python
x = 5
y = 10
print(x + y) # This works because both are numbers

# print(x + "Hahaha") # This will cause a TypeError!
```

### **String Formatting with `.format()`**

This method allows you to place placeholders `{}` inside a string and fill them with variables.

```python
num = 20
name = "Dunn Smith"

# Using order
print("My number is: {}, and my name is: {}".format(num, name))

# Using keyword names
print("My number is: {one}, and my name is: {two}".format(one=num, two=name))
```

### **Formatting with f-strings (The Modern Way)**

This is a newer and often more readable method. Simply add an `f` before the opening quote.

```python
num = 20
name = "Dunn Smith"

print(f"My number is: {num}, and my name is: {name}")
```

-----

## **🧐 Data Types and Data Structures**

We've already touched on some basic data types. Now let's look deeper, including how to organize data into collections.

### **Primitive Data Types**

  * **Integer** (`int`): Whole numbers. `print(type(1+1))`
  * **Float** (`float`): Decimal numbers. `print(type(1/2))`
  * **String** (`str`): Text. `print(type('A'))` or `print(type("Jojo"))`
  * **Boolean** (`bool`): `True` or `False`. `print(type(False))`

### **String Operations: "Manipulating Text"**

Strings come with many built-in "superpowers."

```python
a = " Hello, World! "

print(len(a)) # Counts the length of the string
print(a[8:13]) # Slicing: gets a part of the string (index 8 up to, but not including, 13)
print(a.strip()) # Removes whitespace from the beginning and end
print(a.lower()) # Converts all to lowercase
print(a.upper()) # Converts all to uppercase
print(a.replace("H", "J")) # Replaces a character
print(a.split(",")) # Splits the string into a list based on a separator
```

You can also format numbers inside an f-string:

```python
price = 591209380219.345123
txt = f"The price is {price:,.3f} dollars" # Format with a comma separator for thousands and 3 decimal places
print(txt)
```

### **Data Structures (Non-Primitive)**

#### **List 🛍️ (Changeable, Ordered, Allows Duplicates)**

Like a shopping list that you can cross off, change, or add to. Created with `[]`.

```python
my_list = ['a', 'b', 'c']
my_list.append('d')      # Adds an item to the end -> ['a', 'b', 'c', 'd']
my_list[0] = 'NEW'       # Changes the item at index 0 -> ['NEW', 'b', 'c', 'd']
my_list.insert(2, 'NEW') # Inserts an item at index 2 -> ['NEW', 'b', 'NEW', 'c', 'd']
my_list.remove('NEW')    # Removes the first occurrence of the item 'NEW' -> ['b', 'NEW', 'c', 'd']
print(my_list[1:])       # Slicing: gets items from index 1 to the end -> ['NEW', 'c', 'd']

# Lists can be nested
nest = [1, 2, 3, [4, 5, ['target']]]
print(nest[3][2][0]) # Accessing 'target'
```

#### **Tuple 📜 (Unchangeable, Ordered, Allows Duplicates)**

Like a permanent list that cannot be changed after it's created. Created with `()`.

```python
t = (1, 2, 3)
print(t[0])

# t[0] = 'NEW' # This line would cause a TypeError because tuples are immutable
```

#### \**Dictionary 📖 (Changeable, Unordered*, Unique by Key)\*\*

Like a real dictionary, it stores data in `key:value` pairs. Created with `{}`.
(\*In Python 3.7+, dictionaries have become ordered by insertion).

```python
d = {'key1': 'item1', 'key2': 'item2'}
print(d['key1']) # Accessing a value by its key

d['key3'] = "item4" # Adding a new pair
d['key2'] = "item3" # Changing an existing value
print(d)

d.pop("key2") # Removing an item by its key
print(d)
```

#### **Set 🚫 (Changeable, Unordered, No Duplicates)**

Like an exclusive club where every member is unique. Created with `{}` but without key:value pairs.

```python
s = {1, 2, 3, 2, 1}
print(s) # Output: {1, 2, 3} (duplicates are automatically removed)

u = {4, 5, 6}
s.update(u) # Merging set s with set u
print(s)

s.remove(4) # Removing the value 4 (not an index!)
print(s)
```

-----

## **⚖️ Comparison and Logic Operators**

Your program needs to make comparisons to make decisions.

### **Comparison Operators**

These result in a `True` or `False` value.

  * `>` (Greater than)
  * `<=` (Less than or equal to)
  * `==` (Equal to)
  * `'BYE' == 'bye'` -\> `False` (case-sensitive)
  * `1 == '1'` -\> `False` (different data types)
  * `"BYE" < "bye"` -\> `True` (comparison is based on ASCII code values)

### **Logical Operators**

These combine multiple conditions.

  * `and` (`&`): All conditions must be `True` for the result to be `True`.
      * `(1 > 2) and (2 < 3)` -\> `False`
  * `or` (`|`): Only one condition needs to be `True` for the result to be `True`.
      * `(1 > 2) or (2 < 3)` -\> `True`

-----

## **🎛️ Control Flow: `if`, `for`, `while`**

### **Conditional Statements: `if`, `elif`, `else`**

Make your program take different "paths" based on conditions.

```python
if 2 == 2:
    print('first')
elif 3 == 3:
    print('middle') # This block will not be executed because the first condition was already True
else:
    print('last')
```

### **Loops: `for` and `while`**

Repeat a block of code multiple times.

**`for` loop:** For each item in a sequence.

```python
seq = [1, 2, 3, 4, 5]
for item in seq:
    print(item)
```

**`while` loop:** As long as a condition is `True`.

```python
i = 1
while i < 5:
    print(f'i is: {i}')
    i += 1 # Important! Without this, the loop would run forever (infinite loop).
```

### **The `range()` Function**

A number generator that is very useful for loops. `range(start, stop, step)`.

```python
# Print numbers from 0 to 10
for i in range(11):
    print(i)

# Create a list from a range
print(list(range(5))) # [0, 1, 2, 3, 4]
print(list(range(2, 11, 2))) # [2, 4, 6, 8, 10]
```

### **List Comprehension: An Elegant Shortcut**

A concise way to create lists from a loop.

**The standard way:**

```python
x = [1, 2, 3, 4]
squares = []
for number in x:
    squares.append(number**2)
print(squares)
```

**With List Comprehension:**

```python
x = [1, 2, 3, 4]
squares = [number**2 for number in x]
print(squares)
```

-----

## **🔧 Building Your Own Tools: Functions**

Functions are reusable blocks of code. They make your code cleaner and more efficient.

```python
def my_func(param1='default', param2="abc"):
    """
    This is a docstring.
    This function is for practice, it prints two parameters.
    """
    print(param1, param2)

my_func() # Calling with default parameters
my_func('new param', 'xyz') # Calling with new parameters

def square(number):
    """This function returns the square of a number."""
    return number ** 2

out = square(2)
print(out)
```

### **`map` and `filter` (with `lambda`)**

Functional tools for working with lists.

  * `lambda`: A small, one-time-use, anonymous function.
  * `map`: Applies a function to every item in a list.
  * `filter`: Filters items in a list based on a condition.

<!-- end list -->

```python
seq = list(range(1, 6)) # [1, 2, 3, 4, 5]

# Using map to multiply every item by 2
print(list(map(lambda var: var*2, seq)))

# Using filter to get only the even numbers
print(list(filter(lambda item: item%2 == 0, seq)))
```

-----

## **📊 Statistical Measurement**

Python is a very powerful tool for data analysis. We will use several popular libraries.

  * `statistics`: For basic statistical functions.
  * `numpy`: For working efficiently with numerical arrays.
  * `scipy`: For more advanced statistical functions.
  * `pandas`: For working with labeled datasets (DataFrames).

<!-- end list -->

```python
import math
import statistics
import numpy as np
from scipy import stats

x = [8.0, 1, 2.5, 4, 28.0, 1]
x_with_nan = [8.0, 1, 2.5, math.nan, 4, 28.0, 1] # nan = Not a Number
```

### **Measures of Central Tendency (The Center of Data)**

  * **Mean**: The average. `mean_ = sum(x) / len(x)`
  * **Median**: The middle value.
  * **Mode**: The value that appears most frequently.

<!-- end list -->

```python
print('Mean (statistics):', statistics.mean(x))
print('Mean (numpy):', np.mean(x))

print('Median (statistics):', statistics.median(x))
print('Median (numpy):', np.median(x))

print('Mode (statistics):', statistics.mode(x))
```

### **Measures of Variability (The Spread of Data)**

  * **Variance ($s^2$):** $s^2 = \\frac{\\Sigma\_i(x\_i - \\text{mean}(x))^2}{n-1}$
  * **Standard Deviation:** The square root of the variance.
  * **Skewness:** A measure of the asymmetry of the data distribution.
  * **Percentiles:** The value below which a percentage of data falls.
  * **Ranges:** The difference between the maximum and minimum values.

<!-- end list -->

```python
# Variance
print('Variance (statistics, n-1):', statistics.variance(x))
print('Variance (numpy, n):', np.var(x)) # numpy defaults to dividing by n

# Standard Deviation
print('Std Dev (statistics, n-1):', statistics.stdev(x))
print('Std Dev (numpy, n):', np.std(x))

# Skewness
print('Skewness (scipy):', stats.skew(x))

# Percentile (example: the second quartile or median)
print('50th Percentile (numpy):', np.percentile(x, 50))

# Range
print('Range (numpy):', np.ptp(x))
```

### **Conclusion on Using Statistical Libraries**

  * Use **Python's `statistics`** for the most important, basic statistical functions.
  * Use **`NumPy`** to handle numerical arrays efficiently.
  * Use **`SciPy`** for additional, more advanced statistical routines.
  * Use **`pandas`** to work with labeled datasets (e.g., from CSV or Excel files).
