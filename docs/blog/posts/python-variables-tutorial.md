---
date:
    created: 2025-03-16 
---

# Python Variables and Type Casting

Variables are fundamental building blocks in Python programming. They act as containers for storing data values that can be manipulated and referenced throughout your code. This guide covers the basics of variable declaration, assignment, and type conversion in Python.

## Variable Declaration and Basic Types

Python supports several basic variable types:

1. `int` – Integer type (whole numbers)
2. `float` – Floating point numbers (decimal numbers)
3. `bool` – Boolean values (True or False)
4. `str` – String type (textual data)

Unlike some other programming languages, Python uses dynamic typing, which means you don't need to declare the variable type explicitly.

```python
var1 = 2        # integer
var2 = 5.0      # float
v3 = True       # boolean
```

You can display variables using the `print()` function:

```python
print("variable - 1= ", var1)
print("variable - 2= ", var2)
print("variable - 3= ", v3)
```

Output:
```
variable - 1=  2
variable - 2=  5.0
variable - 3=  True
```

## Checking Variable Types

The `type()` function allows you to check the data type of any variable:

```python
type(var1)  # returns <class 'int'>
type(var2)  # returns <class 'float'>
type(v3)    # returns <class 'bool'>
```

## Multiple Assignment

Python allows you to assign values to multiple variables in a single line:

```python
x, y = 1, 2.5

print('x =', x)
print('y =', y)
```

Output:
```
x = 1
y = 2.5
```

## Type Casting

Type casting is the process of converting one data type into another. Python provides several built-in functions for type conversion:

### Integer Conversions

#### Converting Integer to Float
```python
int_number = 5
float_number = float(int_number)
print(float_number)               # Output: 5.0
print('data type =', type(float_number))  # Output: data type = <class 'float'>
```

#### Converting Integer to String
```python
int_number = 5
str_number = str(int_number)
print(str_number)                 # Output: 5
print('data type =', type(str_number))  # Output: data type = <class 'str'>
```

### Float Conversions

#### Converting Float to Integer
```python
val1 = 5.1
val2 = 5.51
# int() truncates the decimal part (does not round)
int_val1 = int(val1)
int_val2 = int(val2)
print('int_val1 =', int_val1)  # Output: int_val1 = 5
print('int_val2 =', int_val2)  # Output: int_val2 = 5
```

#### Special Rounding Functions

Python provides several functions for rounding floating-point numbers:

##### 1. The `round()` Function
```python
val1 = 5.1
val2 = 5.51
int_val1 = round(val1)
int_val2 = round(val2)
print('int_val1 =', int_val1)  # Output: int_val1 = 5
print('int_val2 =', int_val2)  # Output: int_val2 = 6
```

##### 2. The `ceil()` Function
The `ceil()` function from the `math` module always rounds up to the next integer:

```python
from math import ceil

val1 = 5.1
val2 = 5.51
int_val1 = ceil(val1)
int_val2 = ceil(val2)
print('int_val1 =', int_val1)  # Output: int_val1 = 6
print('int_val2 =', int_val2)  # Output: int_val2 = 6
```

##### 3. The `floor()` Function
The `floor()` function from the `math` module always rounds down to the previous integer:

```python
from math import floor

val1 = 5.1
val2 = 5.51
int_val1 = floor(val1)
int_val2 = floor(val2)
print('int_val1 =', int_val1)  # Output: int_val1 = 5
print('int_val2 =', int_val2)  # Output: int_val2 = 5
```

#### Converting Float to String
```python
float_number = 5.0
str_float_number = str(float_number)
print(str_float_number)  # Output: 5.0
print('data type =', type(str_float_number))  # Output: data type = <class 'str'>
```

### Boolean Conversions

Boolean values can be converted to other types:

```python
# Boolean to Integer
print(int(True))   # Output: 1
print(int(False))  # Output: 0

# Boolean to String
print(str(True))   # Output: 'True'
print(str(False))  # Output: 'False'
```

It's worth noting that in Python, any non-zero number or non-empty string evaluates to `True` when converted to a boolean:

```python
bool_val = bool(-1)
print(bool_val)  # Output: True

print(bool(0))   # Output: False
print(bool(1))   # Output: True
print(bool(""))  # Output: False
print(bool("hello"))  # Output: True
```

### String Conversions

Converting strings to numeric types is conditional on the string content:

#### Converting String to Integer
```python
# Works only if the string contains a valid integer
var8 = '5'
var8_int = int(var8)
print(var8_int)  # Output: 5
print(type(var8_int))  # Output: <class 'int'>

# This will raise a ValueError
# var7 = "datascience"
# int(var7)  # Error: invalid literal for int() with base 10: 'datascience'
```

#### Converting String to Float
```python
# Works only if the string contains a valid number
var8 = '5.1'
var8_float = float(var8)
print(var8_float)  # Output: 5.1
print(type(var8_float))  # Output: <class 'float'>

# This will raise a ValueError
# var7 = "datascience"
# float(var7)  # Error: could not convert string to float: 'datascience'
```

#### Multi-step Conversions
Sometimes you might need to perform multiple conversions:

```python
var8 = '5.1'
var8_float = float(var8)  # First convert string to float
var8_int = int(var8_float)  # Then convert float to int
print(var8_int)  # Output: 5
print(type(var8_int))  # Output: <class 'int'>
```

## Best Practices

1. Choose descriptive variable names that indicate what the variable represents
2. Use type casting carefully, particularly when converting between numeric types and strings
3. Handle potential errors when converting strings to numbers
4. Be aware of the difference between truncation and rounding when converting floats to integers

## Summary

Python's dynamic typing system and built-in type conversion functions provide flexibility in handling different data types. Understanding how to properly declare variables and convert between types is essential for writing effective Python code.

By mastering these concepts, you'll be better prepared to handle data transformation and manipulation tasks in your Python programs.
