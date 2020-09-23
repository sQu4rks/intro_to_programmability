# Marking an item as done

In order to mark a item as done we will need to get the id from the user. To do that we can use our `input` function again. 

```python
def markItemDone():
    print("Mark item as done")

    todo_id = input("Id: ")
```

Based on this we can create the path of said todo item. Looking at the [documentation for the os module](https://docs.python.org/3/library/os.html#module-os) again shows that there is a `os.remove()` function. Let's use that function to delete the todo item. 

```python

todo_path = "todos/" + str(todo_id) + ".todo"
os.remove(todo_path)
print("Removed todo item with id " + str(todo_id))
```

Put together our `markItemDone` function then looks like this:

```python
def markItemDone():
    print("Mark item as done")

    todo_id = input("Id: ")
    
    todo_path = "todos/" + str(todo_id) + ".todo"
    os.remove(todo_path)
    print("Removed todo item with id " + str(todo_id))
```

<div align="right">
   
   [Prev](list.md) - [Next](finish.md)
</div>