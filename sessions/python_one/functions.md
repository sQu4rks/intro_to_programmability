# Functions

Often we need to re-use part of our code. 

You might be tempted to just copy&paste the code over and over again. Let me be very clear here: **Copy&paste is never the correct answer**.

Copy&pasting code leads to many different problems but the biggest one is the clutter when changing parts. Lets say you have a piece of code that checks if your switches are still active by checking a switches `status` variable. The service you retrieve the switch status from suddenly changes the indication that this switch is still active from setting `status=ACTIVE` to `status=active`. If you have copy&pasted that piece of code you now have to change that conditional in every part you have copy&pasted the code into. This is a maintenance nightmare. 

Luckily we can capsulate our code in a way that we can reuse it. That is what *functions* are for. 

## Declaring functions

A function is simply a piece of code that can be called. You have been **using** functions all throughout this session! `print` is a function that python provides by default and so is `range`. 

Declaring your own functions is easy. We use the `def` keyword, a name and round brackets. 

```python

def my_first_function():
    print("This is my first function")
```

Everything that is indented is referred to as the *function body* and this is what gets executed when we *call* the function. 

How do we call a function? By using the name!

```python

def my_first_function():
    print("This is my first function")

my_first_function()
```

> :computer: Do it for yourself! Declare a function called `my_first_function` and have it print out the text `I am Marcel and this is my first function`. 
> Substitute Marcel for your own name.

<details>
  <summary>Click here to show solution</summary>
  
  ```python
  
  def my_first_function():
    print("I am Marcel and this is my first function")
  ```
</details>

## Functions with Arguments and Returns

Functions can have `arguments`. These are variables that are passed into the function to modify the functions behaviour. Lets modify the function above to print the name based on a argument. 

```python

def my_first_function(name):
    print("I am " + str(name) + " and this is my first function")

my_first_function("Marcel")
```    

We can also *return* something from a function. This can be achieved using the `return` statement. 

```python

def my_second_function(name):
    text = "I am " + str(name) + " and this is my second function"

    return text

print(my_second_function("Marcel"))
```

> :computer: Write a function called `test_switch` that receives the `name` and `status` of a switch as a arguments and **returns** either "The switch switch-1 is online" or "The switch switch-1 is offline" depending on wether the status is `active` or `inactive`. The name (`switch-1` in the example) should come from the `name` argument.
> 
> Call the function with the name "switch-2" and the status "inactive". Save the output of that function call in a variable called `out` and print the value of that variable.
> You can use the boilerplate code below as a starting point. You will need to change the questionmarks and fill the body
>
> ```python
> 
> def test_switch(?, ?):
>   
>   return ?
> out = ?
> print(out)
> ```
> 
> Pay close attention to which parts of the program need to be inside the function and which parts need to be outside of the function.

<details>
  <summary>Click here to show solution</summary>
  
  ```python
  
  def test_switch(name, status):
    if status == "active":
        return "The switch " + str(name) + " is online"
    elif status == "inactive":
        return "The switch " + str(name) + " is offline"

  out = test_switch("switch-2", "inactive")
  print(out)
  ```
</details>

<div align="right">
   
   [Prev](loops.md) - [Next](advanced_data_structures.md)
</div>