# The User Interface

## Getting inputs from the user

So far we have always only returned information to the user by printing them. Often we want to get input
from the user however. In python this can be achieved using the build-in `input()` function. 

```python

name = input("What is your name? ")
print("The name is " + name)
```

## Writing our interface

So for our interface function lets get started by printing out some basic textual information and then 
ask the user which command they would like to use:

```python

def interface():
    print("Welcome to our todo application")
    print("What would you like to do?")
    print("-> create: create a new todo item")
    print("-> list: list all todo items")
    print("-> done: mark a todo item as done")
```

This little part just prints out the commands that are available to the user. Let's prompt for a command to be carried out:

```python

cmd = input("Command: ")
```

`cmd` now contains the string provided by the user. We can now use `if-elif-else` conditionals to invoke the correct function:

```python

if cmd == "create":
    createItem()
elif cmd == "list":
    listItems()
elif cmd == "done":
    markItemDone()
else:
    print("I don't understand the command")
```

Put together, this is how our `interface` function then looks like:

```python

def interface():
    print("Welcome to our todo application")
    print("What would you like to do?")
    print("-> create: create a new todo item")
    print("-> list: list all todo items")
    print("-> done: mark a todo item as done")

    cmd = input("Command: ")

    if cmd == "create":
        createItem()
    elif cmd == "list":
        listItems()
    elif cmd == "done":
        markItemDone()
    else:
        print("I don't understand the command")
```

Next, we will be creating the `createItem()` functionality.

<div align="right">
   
   [Prev](structure.md) - [Next](create.md)
</div>