# Variables and Data types

The most basic concept of every programming language are *variables*. Simply put,
variables are placeholder for other values. For example your variable could hold 
the number of routes that are reachable from a router or the IP address of your 
gateway. In python variables have a name, the *variable name* that can be used 
to refer to them and are assigned a value. 

```python 

a = 10
b = "Hello"
pi = 3.14
```

The first time a variable is assigned we also talk about this variable being *initialized*.

## Data types

Values can come in many different shapes and forms. You could store a counter, which is just a whole number, or a message of the day which would be a text. These different types of data a variable can hold are also referred to as *data types*.

Python knows four different *simple* or *basic* data types. 

* `string` for storing text and characters
* `int` for storing integer numbers
* `float` for storing numbers that contain a decimal part
* `None` for "nothing"

Contrary to other programming languages python is not *statically typed*. What is behind that word you might ask? This simply means that you, as a programmer, don't have to specify what type your variable holds. The python interpreter figures this out on its own based on the value of the variable!

### Strings

*Strings* hold everything related to text in python. You declare a string by using 
quotation marks. Have a look at the example below:

```python

text_1 = "This is a text"
text_2 = 'We can also use single quotes to declare our text'

long_text = """
And we can have
our text go over
multiple lines when we use triple quotes
"""
```

You can also combine two strings into a new string. This is also referred to as 
*string concatenation*. In python this is achieved by using the `+` operator.

```python

text_1 = "I am a text."
text_2 = "And I am also a text"

text_3 = text_1 + " " + text_2
print(text_3)
```

As you can see in the example above, we can combine variables and a string we just declared(the `" "` whitespace in the example) into a new string.

> :computer: Modify the script below so that it included your name. You will need to specify a variable called `your_name` and then assign your name to it as a `string`
> 
> ```python3
> # You will need to add code here
> 
> print("Hello " + your_name)
> ```

<details>
  <summary>Click here to show solution</summary>
  
  ```python
  your_name = "Marcel"
  print("Hello " + your_name)
  ```
</details>

### Integers

*Integers* or *ints* hold everything related to whole numbers in python. You declare such a number by simply assigning it using the `=` symbol. There is no need for quotes or anything to mark it as a number. Have a look at the example below.

```python

a = 10
b = 5
```

We can add, subtract and multiply integers using the `+`, `-` and `*` operators.

```python

a = 10
b = a * 5 # b is now 50
c = 10
d = b - c # d is now 40
```

We can also subtract, multiply or add a value to the variable itself. 

```python

a = 5
a = a + 5 # Now a has the value 10
a = a * 2 # Now a has the value 20
a = a - 5 # Now a has the value 15
```

We can write this also with a shorthand to save us some typing:

```python

a = 5
a += 5
a *= 2
a -= 5
```

So far we have skirted around *divisions*. Divisions can't always be whole numbers. For example 5 divided by 2 is 2.5 which is not a whole number. To hold these types of values we will need a new data type, the *floats*.

> :computer: Use python to calculate the following operations:
> * Declare a variable `a` with value 10
> * Declare a variable `b` with value 2
> * Declare a variable `c` that is calculated by multiplying `a` and `b`
> * Add 10 to the variable `c`
> * Multiply `c` with itself

<details>
  <summary>Click here to show solution</summary>
  
  ```python
  
  a = 10
  b = 2
  c = a * b
  c += 10 # alternative: c = c + 10
  c *= c # alternative: c = c * c
  ```
</details>

### Floats

*Floats* hold everything related to floating or decimal numbers like 2.5 or 3.14159. floats are declared by using the `=` operator. To help python distinguish floats from integers we use the `.` to separate the whole and fractional number part. We can carry out the same operations we can with integers.

```python

a = 10.5 # Mind the "."

a += 5
a *= 2.33
a = a / 2.5
```

As you can see we can mix floats and integers when doing any calculations. Python will always choose the right variable type to fit in the value of your calculation.

### None

*None* is a bit of an odd data type. What *None* represents is nothing. While it might be counter-intuitive to dedicate a entire data type to "nothing" we quite often have to represent nothing. As an example think about a piece of code that calculates the square root of a number, so the square root of 4 is 2, the square root of 9 is 3 and so. In basic mathematics it is not possible to calculate the square root of a negative number. How would your code represent that? How would you signal to someone using your code that this value is not a valid square root? You could use `0` however, 0 is a valid square root of 0. Maybe you would use `-1`? But `-1` is a valid square root of `1`. We need a data type that represents "nothing" and that is what "None" is for. 

```python

a = None
```

### Converting between data types

Often we have to convert between one data type and another. For example when using the `print` function to print out text we can only pass a variable of type string. But what if we want to print out a number? We have to convert the number into a string. This is also referred to as a *cast* or *type cast*.

To do this in python we have a variety of *cast functions*. 

```python

a = 10
b = str(a) # Converts the integer a into a string
c = float(a) # converts the integer a into a float
d = int(c) # converts the float c into an integer variable
```

> :warning: When converting a `float` to an `int` that number won't be rounded. Rather the fractional part will just be discarded. This means that, `int(3.9)` won't be `4` as would be the correct rounding but rather `3`. 

Of course you can't just *cast* everything into everything. Trying to cast a text like `text_1 = "This is a text"` into a integer will result in an error. Try it out for yourself and observe the `ValueError` python will return:

```python

text_1 = "This is a text"
int_1 = int(text_1)
```

<div align="right">
   
   [Prev](Readme.md) - [Next](loops.md)
</div>

