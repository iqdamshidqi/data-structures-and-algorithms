# **🚀 A Quick Review of Pyhton! 🐍**

## ✍️ Leaving Notes

### **Single-Line Comments**

```{python}
# This comment explains the next line of code.
print("Hello, World!") # This comment is on the same line as the code.
# This comment explains the after line of code.
```

### **Multi-Line Comments**

```{pyhton}
# This is a longer comment
# that takes up
# multiple lines.
print("Multi-line comments are useful!")

'''
You can also use triple single quotes.
This is great for detailed explanations
about your code's purpose.
'''
print("Another way to comment!")
```

## 📦 Storing Information

**Rules for Naming Your "Boxes":**
* Start with a letter or underscore `(_)`: `my_variable` is good, but 1st_variable is not.
* No special characters: Use only letters, numbers, and underscores (`A-z`, `0-9`, `_`).
* Case-sensitive: `my_age` and `My_Age` are two different variables.
* No reserved words: You can't name a variable `if`, `for`, `print`, etc [Python's reserved keywords](https://www.w3schools.com/python/python_ref_keywords.asp).


```{python}
X = 1
x = 2
y = "Klein"

print(X)
print(x)
print(y)
```

### **Casting**
You can always check a variable's type with the `type()` function.

```{python}
number = 42
pi_value = 3.14159
message = "Coding is fun!"
is_learning = True

print(type(number))   # Output: <class 'int'>
print(type(pi_value)) # Output: <class 'float'>
print(type(message))  # Output: <class 'str'>
print(type(is_learning)) # Output: <class 'bool'>
```

> **Important**: *Variables in Python are dynamic. This means you can change their type at any time.*

```{python}
x = 3 # x is an integer
print(x, type(x))

x = "Moretti" # Now, x is a string
print(x, type(x))
```

### **Multiple Ways to Assign Variables**

```{python}
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

## 🖨️ Printing Output
