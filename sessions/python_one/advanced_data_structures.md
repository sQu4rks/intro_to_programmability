# Advanced Data Structures
So far we have only discussed "simple" variables like strings or integers and these can already be used for many different things. But what if we need some more advanced things? 

* What if we don't know the number of variables? 
* What if we have a list of variables?
* What if a function should return more then one variable? 

We need more advanced data structures that can satisfy this need! 

## Lists

*Lists* are, as the name suggests, a list of variables. We can, for example, have a list of strings with the names of all our switches. A list in python is declared using the `[]` operator. Sometimes you can also come across the `list()` operator. Both work in the exact same way.

```python

l = []
l = list()
```

We can initialize a list with initial values 

```python

l = [1, 2, 3, 4, 5]
```

and we can mix the types of objects we put into our list

```python

l = [1, "two", "three", 4.0, 5, None]
```

Accessing a list item is done by their *index*.

```python
l = ["one", "two", "three"]

print(l[0])
```

> :warning: List indices start at 0. The first item in a list is not `l[1]` but `l[0]`.

We can also add and remove items from a list

```python

l = ["one"]
l.append("two") # This adds the item to the list
l.remove("one") # This removes the item with VALUE one
```

> :computer: Do it yourself! Create a list that holds the strings one, two, three, four and five. Then append the string six to the list and print the string a **index** 2

<details>
  <summary>Click here to show solution</summary>
  
  ```python3
  l = ["one", "two", "three", "four", "five"]
  l.append("six")
  print(l[2])
  ```
</details>

### Iterating over a list

Often we want to do some sort of operation to all the items in a list. To do so we can use our for loop. 

```python

l = ["one", "two", "three"]

for itm in range(0, len(l)):
    print(itm)
```

You can see we are using the `len` function to get the length of our list. This allows us to plug that length into our `range` function to get all the indices that are in the list. 

> :wrench: You can now see why the range function leaves the last item out. It is meant to facilitate this kind of iterations.

> :computer: Create a list with the names of three switches: `switch-1`, `switch-2` and `switch-3`. 
> 
> Iterate over the list and print the name of the switches

<details>
  <summary>Click here to show solution</summary>
  
  ```python
  l = ["switch-1", "switch-2", "switch-3"]
  for i in range(0, len(l)):
    print(l[i])
  ```
</details>

### Lists and for-loops revisited
When I told you that, with lists, you will see a new concept I was actually lying. You have been using lists all along. The `range` function we saw previously returns a list of numbers in the specified range. This is called a *for-each* loop. 

For-each loops allow us to iterate over all items in a list without having to use the index. Let's modify above code sample to use a for-each loop:

```python

l = ["switch-1", "switch-2", "switch-3"]
for switch in l:
    print(switch)
```

> :computer: You receive a list of switch statuses. The status is a string that is either `active`, `unknown` or `inactive`. 
> 
> Count the number of switches active, unknown or inactive.
> 
> You can use the boilerplate code below:
> 
> ```python
> 
> switch_statuses = ["active", "active", "active", "unknown", "inactive"]
> 
> number_active = 0
> number_unknown = 0
> number_inactive = 0
> 
> # Add your code here!
> print("Number of active switches: " + str(number_active))
> print("Number of unknown switches: " + str(number_unknown))
> print("Number of inactive switches: " + str(number_inactive))
> ```

<details>
  <summary>Click here to show solution</summary>
  
  ```python
  
  switch_statuses = ["active", "active", "active", "unknown", "inactive"]
  
  number_active = 0
  number_unknown = 0
  number_inactive = 0

  # Add your code here!
  for status in switch_statuses:
    if status == "active":
        number_active += 1
    elif status == "inactive":
        number_inactive += 1
    elif status == "unknown":
        number_unknown += 1

  print("Number of active switches: " + str(number_active))
  print("Number of unknown switches: " + str(number_unknown))
  print("Number of inactive switches: " + str(number_inactive))
  ```
</details>

## Dictionaries

The last puzzle piece we need are *dictionaries*. *Dictionaries* or *dicts* are a way of associating a key with a value. This is a quite common requirement. Let's say you want to store configuration information or information about a user. This is where dictionaries shine!

We initialize or declare a dictionary as follows:

```python

d = {}
```

We can now go ahead an assign values:

```python

d["key"] = "value"
```

A example would be a dictionary holding some information about a user:

```python 

user = {}

user["first_name"] = "Marcel"
user["last_name"] = "Neidinger"
user["age"] = 24
```

We can then access a value by its *key* using the key as an index:

```python
user = {}

user["first_name"] = "Marcel"
user["last_name"] = "Neidinger"
user["age"] = 24

print(user["age"]) # This is the access
```

> :computer: Do it for yourself! Declare a `user` dictionary with the keys `first_name`, `last_name` and `age` and then print them all out!

<details>
  <summary>Click here to show solution</summary>
  
  ```python
  
  user = {}

  user["first_name"] = "Marcel"
  user["last_name"] = "Neidinger"
  user["age"] = 24
  
  print(user["first_name"])
  print(user["last_name"])
  print(user["age"])
  ```

</details>

### Iterating over dictionaries

Quite often we want to access all elements in a dictionary and sometimes (i.e. if that dictionary is returned to us by an API) we don't exactly know the keys. We can use our for loop to get rid of that problem!

```python

user = {}

user["first_name"] = "Marcel"
user["last_name"] = "Neidinger"
user["age"] = 24

for key in user.keys():
    print(user[key])
```

> :wrench: The function `dict.keys()` just returns a list of all the keys. We are using the for-each loop again!

> :computer: Rewrite the code from the last exercise, the one printing out all the properties of the user dictionary, using the for-each loop and the `keys()` function.
> 
> You can use this boilerplate: 
> 
> ```python
> user = {}
>
> user["first_name"] = "Marcel"
> user["last_name"] = "Neidinger"
> user["age"] = 24
> ```

<details>
  <summary>Click here to show solution</summary>
  
  ```python
  
  user = {}

  user["first_name"] = "Marcel"
  user["last_name"] = "Neidinger"
  user["age"] = 24
  
  for key in user.keys():
    print(user[key])
  ```

</details>
<div align="right">
   
   [Prev](functions.md) - [Next](/sessions/python_two/Readme.md)
</div>