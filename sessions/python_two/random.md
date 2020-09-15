# Random

The `random` module allows you to generate random numbers as well as some other tasks related to randomness. 

> :wrench: Not all functions in the `random` module are cryptographically save and thus suited for i.e. the handling of
> passwords. Refer to the documentation and double check. 

First, we need to import the module using 

```python

import random
```

Next, we can generate a random integer number using the `random.randint` function.

```python

import random

random_int = random.randint(0, 10)
```

Above code snippet generates a random integer between 0 and (including) 10. 

> :computer: Write a little script that imports the random module and generates 5 
> random numbers between 0 and 15. 
> 
> for-loops might be useful here.

<details>
  <summary>Click here to show solution</summary>
  
  ```python3
  import random

  for i in range(0, 5):
    random_num = random.randint(0, 15)
    print("Random number #" + str(i) + " is " + str(random_num))
  ```
</details>

We can also randomly draw a object out of a list. This functionality is provided by the `random.choice` and `random.choices` function. They both take a list of options and then return one (or more) randomly chosen items from that list. 

```python

import random

numbers = ["one", "two", "three", "four"]

# Get one random string 
one_random_number = random.choice(numbers)

print("Our one random number is: " + str(one_random_number))

# Get multiple
two_random_numbers = random.choices(numbers, k=2)

print("Your random numbers: ")
for num in two_random_numbers:
    print("- " + str(num))
```

For the `random.choice` function we only need to provide the list of choices. For the `random.choices` function 
we also need to tell the function how many to return. This is done by the argument `k`. 

When we covered function we didn't talk about *default arguments* so let's make a quick excursion into that topic.

## Functions and Default Arguments

As we have seen you can declare a function using the `def` argument and a function can receive arguments to pass
values into the function. Previously all these values had to be set when being called. We can, however, also provide 
default values. 

```python

def func_with_defaults(argument="test"):
    print("Our argument is " + str(argument))
```

If we want to call above function we now have three options: 

1. Not provide a value for `argument`. This will result in the default value of `test` being used

```python

func_with_defaults()
```

2. Provide a value for `argument` by passing the new value into the function. This is then referred to as a *positional argument*.

```python

func_with_defaults("passed into it")
```

3. Explicitly name the *function argument* that we want to specify. This then called a *keyword argument*

```python

func_with_defaults(argument="passed as keyword argument")
```

You can see all of these working in below code snippet

```python
def func_with_defaults(argument="test"):
    print("Our argument is " + str(argument))

func_with_defaults()
func_with_defaults("passed into it")
func_with_defaults(argument="passed as keyword argument")
```

Positional arguments are specified by their *position* within the function definition while *keyword arguments* are specified by their keyword in the function definition. 

> :wrench: The definition of a function, that means the name, arguments and default values is also called a *function signature* or the *signature of a function*.

To make things more complicated (or powerful, depending on your view point) we can mix *positional arguments* and *keyword arguments*.

```python

def func_with_mix(arg1, arg2):
    print("Arg1: " + str(arg1))
    print("Arg2: " + str(arg2))

func_with_mix("test1", arg2="test2")
```

What you can't do however, is call a positional argument **after** you have specified keyword arguments. So you can't do the following:

```python

func_with_mix(arg1="test1", "test2)
```

Coming back to our example of `random.choices` this is what we are doing when we call `random.choices(options, k=2)`. We specify the (required) *positional argument* options, which is a list of items to draw from, and the (optional) keyword argument *k*. By default `k` is set to `1`. 

> :computer: Write a little script that draws two winners out of a list of five possible winners and prints out their names. You can start with below code  
> 
> ```python 
> 
> import random
> 
> possible_winners = ["Sarah", "Sven", "Simon", "Sophie", "Samantha"]
> 
> # ToDo: Add the code needed to draw two winners here

<details>
  <summary>Click here to show solution</summary>
  
  ```python3
  import random

  possible_winners = ["Sarah", "Sven", "Simon", "Sophie", "Samantha"]

  winners = random.choices(possible_winners, k=2)

  for winner in winners:
    print("The winner is " + str(winner))
  ```
</details>

<div align="right">
   
   [Prev](standard_library.md) - [Next](random.md)
</div>