# Listing all ToDo Items

In order to list items we will need to interact with the file system of our system. Basically we need to find a module that allows us to list all files in a directory. 

## Exploring the Python Standard Library
You haven't missed something! So far we did not introduce that library. As mentioned in last weeks session the python standard library includes a comprehensive documentation so lets have a look at how we can find the correct module and function. 

First, go to the [python standard library documentation](https://docs.python.org/3/library/). Here we can find a long list of 
everything that is included. All modules are categorized. The *File and Directory Access* category looks interesting for what we 
are trying to achieve. 

At the bottom there is a yellow box that mentions the `os` module. The description specifies that `os` allows us to "[Use] Operating system interfaces, including functions to work with files at a lower level than Python file objects". Let's navigate to the [os module documentation](https://docs.python.org/3/library/os.html#module-os). Here we find a list of all the functions that this module provides. 

Let's search the page for something like `listdir`. Doing so reveals the `os.listdir()` function that takes a optional `path` argument and returns a list of all files and folders in that `path`. Exactly what we were looking for. 

So lets add the `os` module to our list of imported modules:

```python
import os
```

## Retrieving our todos from the files
Next, lets list all files in our `todos/` folder and create a read-only file handler for each of them:

```python

def listItems():
    print("List all ToDo items")

    for todo_file_name in os.listdir("todos/"):
        todo_path = "todos/" + todo_file_name

        file_handler = open(todo_path, "r")
```

The `json` module does not only allow us to write directly to a file handler but also allows us to load directly from one. For this we can use the `json.load` function. Mind the missing "s" at the end of the function name. 

```
item = json.load(file_handler)
```

We now have a dict called `item` that contains our todo item. We can use this to print out the information to the user. 

```python
print("Id: " + str(item['id']))
print("-> Title: " + str(item['title']))
print("-> Priority: " + str(item['priority']))
```

The complete function then looks like this:

```python
def listItems():
    print("List all ToDo items")

    for todo_file_name in os.listdir("todos/"):
        todo_path = "todos/" + todo_file_name

        file_handler = open(todo_path, "r")
        item = json.load(file_handler)

        print("Id: " + str(item['id']))
        print("-> Title: " + str(item['title']))
        print("-> Priority: " + str(item['priority']))
```

Last but not least we now need a functionality to mark an todo as done. Marking as done for us simply means deleting the item. 

<div align="right">
   
   [Prev](create.md) - [Next](done.md)
</div>