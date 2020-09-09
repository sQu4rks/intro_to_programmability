# Cheatsheet for Python Programmability - Part 1

This cheatsheet aims to provide a quick recap of all we have covered in part one of our three-part series on programmability with python. You can find the full version of the write up [here](/README.md). 

## Variables
[Link to Section](variables.md)
* Variables have a name and are assigned with the `=` operator. Example: `a = 10`
* Variables have data types that define what kind of values they hold. 
* The data types are:
  * `string` for text
  * `int` for whole numbers
  * `boolean` for boolean(true/false)
  * `float` for floating point numbers
  * `None` for nothing

```python

an_integer = 10
an_float = 50.0
text = "This is a text"
an_boolean = True
an_nothing = None
```

* You can convert(or *cast*) between variables of different data types

```python

a = 10
a_as_text = str(a)
```
* The conversion functions are
  * `str()` to convert to string
  * `bool()` to convert to boolean
  * `int()` to convert to integer
  * `float()` to convert to floating point number

## Loops
[Link to Section](loops.md)
* We can use `for` loops to execute a operation multiple times

```python
for a in range(0, 10):
  print("Iteration #" + str(a))
```
* Mind the indention. This is the loop body that gets executed
* The range provided is including the starting point and **excluding** the last number. This means that, for a range like `range(0, 5)`, the numbers will be `0,1,2,3,4` not including the last number 5.

## Conditionals 
[Link to Section](loops.md)
* We can use `if` clauses to specify conditionals
* A `if` clause has one or more conditionals that, if met, will be executed. 
* We can have additonal conditionals (using `elif`) and a catch-all that gets executed if non of the conditionals is met (using `else`)

```python

age = 10
if age == 12:
  print("Age is 12")
elif age == 15:
  print("Age is 15")
else:
  print("Age is something else")
```

| **Operator**  | **Description**                                   |
|---------------|---------------------------------------------------|
| `a == b`      | True if a is equal to b                           |
| `a > b`       | True if a is strictly greater than b              |
| `a >= b`      | True if a is greater or equal than b              |
| `a < b`       | True if a is strictly less than b                 |
| `a <= b`      | True if a is less of equal than b                 |
| `a % b == 0`  | True if a can be divided by b without a remainder |

## Functions
[Link to Section](functions.md)
* Functions allow you to encapsulate code for later re-use

```python

def my_function_name():
 print("Hello!")
```
 
 * Functions can have one or more arguments
 
 ```python 
 
 def my_function_name(argument_one, argument_two):
  print("Argument 1 is: " + str(argument_one))
  print("Argument 2 is: " + str(argument_two))  
```

* Functions can return information

```python

def my_function(name):
 return "Hi my name is " + str(name)
```
