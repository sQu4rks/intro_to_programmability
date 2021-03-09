# Loops and Control Structures

Writing operations line by line is fine but what if we want to carry out the same operation multiple times? Let's say we want to print the sentence `Hello from python` five times. We could do it like this:

```python

print("Hello from python")
print("Hello from python")
print("Hello from python")
print("Hello from python")
print("Hello from python")
```

You can probably tell that this is getting cumbersome when dealing with more then a trivial amount of times we want to run the code and outright impossible if we don't know the number of *iterations* before.

To solve this, python and all other programming languages, have the concept of *loops*. Let's first look at *for loops*.

## For loops

A `for loop` allows us to execute one or more instructions a certain number of times. To take the example from above:

```python

for a in range(0, 5):
    print("Hello from python")
```

There are a few things to consider here:

* We use the keyword `for` to specify that this is a *for loop*. 
* We use the `range(start, end)` function to specify the number of *iterations* we want this loop to run for. 
* The indented part (in this example just the line with the `print` statement) is what gets executed. python uses indentation to structure the code.

> :computer: Use a for loop to print the text "Good morning!" ten times.

<details>
  <summary>Click here to show solution</summary>
  
  ```python
  
  for a in range(0, 10):
    print("Good morning!")
  ```
</details>

In the for loop specified above we also have a variable `a`. This does not necessarily need to be a and you can use any variable name you like. We can also use this variable in the indented part of the body. Let's have our script print out the value of the variable.

```python

for a in range(0, 10):
    print("This is the " + str(a) + ". iteration")
```

As you can see we start with `This is the 0. iteration` and end with `This is the 9. iteration`.

Be aware that the range you specify always **excludes** the last number of you range. 

> :computer: Modify the code so that it prints 
> 
> ```
> This is the 1. iteration
> This is the 2. iteration
> This is the 3. iteration
> This is the 4. iteration
> This is the 5. iteration
> ```
>
> Pay close attention that you specify the correct range!

<details>
  <summary>Click here to show solution</summary>
  
  ```python
  
  for a in range(1, 6):
    print("This is the " + str(a) + ". iteration")
  ```
</details>

> :computer: Lets use this new knowledge to print out all ip addresses that are in a subnet.
> 
> Given a class C Network of `192.168.0.0/24` and a netmask of `255.255.255.0` print out all addresses that are available (including the network and broadcast address)
>
> Remember: The variable of your for loop will be an integer. You will need to cast accordingly!

<details>
  <summary>Click here to show solution</summary>
  
  ```python
  
  for host_part in range(0, 256):
    ip_address = "192.168.0." + str(host_part)
    print(ip_address)
  ```
</details>

We can also have a for loop inside another for loop. This for-loopception is called *nesting*.

```python

for x in range(0, 10):
    for y in range(0, 10):
        print("Looking at pixel (" + str(x) + "," + str(y) + ")")
```

> :computer: We can use nested for loops to print out multiplication tables. Modify the code below
> 
> ```python
>  for num in range(1, 11):
>       print("Multiplication table for " + str(num))
>       # Use another for loop for the `multiplier` variable 
>       # Insert here
>           res = num ∗ multiplier
>           print(str(num) + ” x ” + str(multiplier) + ” = ” + str(res))
> ```

<details>
  <summary>Click here to show solution</summary>
  
  ```python
    
  for num in range(1, 11):
        print("Multiplication table for " + str(num))
        for multiplier in range(1, 11):
           res = num ∗ multiplier
           print(str(num) + ” x ” + str(multiplier) + ” = ” + str(res))
  ```
</details>

## Control Structures

*If-clauses* can be used to change the program flow based on a a variable value. The instructions carried out when a *comparisson* or *condition* is met are also called a *branch*. They are again marked by indentation.

```python

a = 10
if a == 10:
    # This is the branch
    print("a has the value of " + str(a))
```

In this simple example we use `if` to mark that this is now a *if-clause*. 

The condition is then specified after that. Be aware that we are using `==` for the comparison. Remember that the `=` operator is already used for assigning variable values. 

We can use a number of comparison operators like 

* `a == b` to check if `a` is equal to `b`
* `a >= b` to check if `a` is bigger or equal to `b` 
* `a <= b` to check if `a` is less then or equal to b`
* `a%b == 0` to check if `a` can be divided by `b` wihtout a remainder

We can have more then one conditional. To declare these additional branches we use the `elif` keyword. Additionally we can use the `else` keyword to specify a branch that gets carried out when non of the conditions above were met

```python

a = 5
if a == 10:
    print("a is 10")
elif a == 5:
    print("a is 5")
else:
    print("a is neither 5 nor 10")
```
Be advised that python stops checking after the first condition is met! So if a variable would satisfy both the first and last conditions of your if-elif-else clauses only the first one will be executed.

> :computer: The **FizzBuzz** test is a famous question in entry-level coding interviews. The ask is simple:
> 
> Write a program that prints the numbers from 1 to (including) 20
> 
> * for multiples of three print **Fizz** instead of the number
> * for multiples of five print **Buzz** instead of the number
> * for multiples of both five and three print **FizzBuzz** instead of the number
> * In all other cases print the number
> 
> Three tips: 
> 
> 1) To check if a number is a multiple of another number you can use this conditional:
> 
> ```python
> 
> a = 10
> if a%5 == 0:
>   print("This number is a multiple of 5")
> ```
>
> 2) You can chain multiple conditions with the `and` keyword
> 
> ```python
> 
> age = 17
> if age > 10 and age < 18:
>   print("The person is a teenager")
> ```
> 
> 3) Remember for loops? They might come in handy in this exercise.

<details>
  <summary>Click here to show solution</summary>
  
  ```python
  
  for num in range(1, 21):
    if num % 3 == 0 and num % 5 == 0:
        print("FizzBuzz")
    elif num % 3 == 0:
        print("Fizz")
    elif num % 5 == 0:
        print("Buzz")
    else:
        print(str(num))
  ```
</details>

<div align="right">
   
   [Prev](variables.md) - [Next](functions.md)
</div>
