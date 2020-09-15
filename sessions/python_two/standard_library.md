# The Standard Library

The python programming language is often called *batteries included*. 
This means that, with the standard installation, a lot of functionality has been 
provided already.

These pieces of code that can be reused by your script are called **modules**. In this
section we will have a look at the modules that come included with python, the so-called
*standard library*.

## Importing Modules and using module functions

In order to use functions developed by other people in modules we will need to import them. 
In python this is done with the `import` statement. These statements, in theory, can be 
everywhere in the code but it is good practice to put these at the top of your script. 

```python

import test_module
```

Above (non-functioning) code would import the module `test_module`. Assuming that the `test_module` 
defines a function called `test_function` we could now go ahead and use this function like this:

```python

import test_module

test_module.test_function("This is input")
```

Sometimes you only want to import one function from a module instead of loading the entire module. You can also do this using the following snippet. 

```python

from test_module import test_function
```

Calling the `test_function` now works like this:

```python

from test_module import test_function

test_function("This is also input")
```

With this knowledge, lets explore the standard library and put these imports to good use!

<div align="right">
   
   [Prev](/sessions/python_one/Readme.md) - [Next](random.md)
</div>


