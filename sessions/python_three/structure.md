# The Structure

Lets start by writing out the structure of our program. Based on our requirements we will 
have four functions:

* `createItem()` to create a new todo item
* `listItems()` to list all items that we currently have in our todo system
* `markItemDone()` to mark a item as done
* `interface()` to provide a commandline interface for the user to interact with our system

The basic structure of our program thus looks like this:

```python

def createItem():
    print("Create a new ToDo item")

def listItems():
    print("List all ToDo items")

def markItemDone():
    print("Mark item as done")

def interface():
    print("Welcome to our todo application")

interface()
```

Above code defines a function for each of the functionalities we want to provide and then calls the 
`interface()` function for the user to interact with our application. 

Next, let's write the user interface.

<div align="right">
   
   [Prev](project.md) - [Next](interface.md)
</div>