# Creating a new ToDo Item

As mentioned in the requirements we will need to store our todos as json files. This means we want to 
import the `json` module at the top of the file:

```python
import json
```

We will also need ids that are unique. There are many ways to generate ids that are guaranteed to be unique
but for this little project we will just use a random integer in the range `1000` to `10000`. This means we will also
need to import the `random` module. 

The top of our file should now look like this:

```python 

import json
import random
```

We will also need to create the `todos/` folder. To do so, in repl.it, click on the little *Add folder* icon and create a new 
folder called `todos`. Your directory structure should now look like this:

```
main.py
todos/
```

So lets get started by prompting the user for the required information. 

```python

def createItem():
    print("Create a new ToDo item")
    
    title = input("Title: ")
    priority = input("Priority: ")
```

We can now store these information in a dictionary so that we can easily export them to json. 

```python

d = {}
d["title"] = title
d["priority"] = priority
```

Next we need to generate our random id, so lets use the `random.randint()` function to get a random integer in our desired range 
and also store that one in our dictionary.

```python

random_id = random.randint(1000, 10000)
d["id"] = random_id
```

With this we are ready to store our information in a file. 

## Writing to and reading from files in python

Reading and writing files in python is made easy. There are two major things we need to know:

First, files in python are represented by *file handlers*. These objects allow you to write to and read from files and second we can use the `open()` function to create these file handlers. 

Writing to a file in python thus looks like this:

```python

file_handler = open("test.txt", "w")
file_handler.write("This is a test\n")
file_handler.close()
```

And reading all lines in a file looks like this:

```python

file_handler = open("test.txt", "r")
for line in file_handler.readlines():
    print(line)
```

Notice the second argument of the `open` function? This is the *mode* and it specifies what we want to do with the file. 
`r` is for reading a file, `w` for writing a file.

## Saving our ToDo Item

Lucky for us we don't even need to think about how to first convert our dictionary into a string and then write that string to 
a file. Instead the `json` module has a function called `json.dump()`. Notice the missing `s` at the end. This function now doesn't dump the content into a string but rather expects a file handler to write to. 

So let's store our dictionary in a file that ends in the file extension `.todo` and has the `id` as its file name. 

```python

file_path = "todos/" + str(random_id) + ".todo"

file_handler = open(file_path, "w")

json.dump(d, file_handler)
print("Saved todo item with id " + str(random_id))
```

Our full function thus looks like this:

```python
def createItem():
    print("Create a new ToDo item")
    
    title = input("Title: ")
    priority = input("Priority: ")

    d = {}
    d["title"] = title
    d["priority"] = priority

    random_id = random.randint(1000, 10000)
    d["id"] = random_id

    file_path = "todos/" + str(random_id) + ".todo"

    file_handler = open(file_path, "w")

    json.dump(d, file_handler)
    print("Saved todo item with id " + str(random_id))
```

Now that we can create todo items we also need a functionality to list all those items we already have. So next we are going to 
create the `listItems` function. 

<div align="right">
   
   [Prev](interface.md) - [Next](list.md)
</div>