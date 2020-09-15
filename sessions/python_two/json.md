# JSON

JSON, stands for *JavaScript Object Notation* and is a popular text-based exchange format. We will learn more about the structure of JSON next week as well as during our REST API Fundamentals session. For now, let's see how we can read and write json from/to a dictionary in python.

First, we need to import the `json` module. This module is part of the standard library so you don't need to install anything!

```python

import json
```

## Turning a python dict into json

First we will need a python dictionary that we can then convert into a json string. Then we call the `json.dumps()` function. 

```python 

import json

d = {}

d["first_name"] = "Marcel"
d["last_name"] = "Neidinger"
d["mail"] = "mneiding@cisco.com"

string_representation = json.dumps(d)
print(string_representation)
```

`json.dumps()` takes a python dictionary and dumps it into a string.

## Turning a json string into a python dictionary

We can also do the reverse operation and turn a (correctly formatted) json string into a python dictionary. 

```python

import json

json_str = """
{"first_name": "Marcel", "last_name": "Neidinger", "mail": "mneiding@cisco.com"}
"""

d = json.loads(json_str)

print(str(d))
```

> :computer: Write a script that imports the json module and saves a dictionary as a string. The dictionary will contain the first name(dictionary key: `first_name`), last name (dictionary key: `last_name`) and age (dictionary key: `age`) of a person. The first and last name should be randomly drawn from a list of names while the age should be a random integer in the range 18 to 99.
> 
> You can find the list of first and last names in the code skeleton below
> 
> ```python
> #ToDo: imports
>
> first_names = ["Nadja", "Nick", "Lucy", "Howie", "Sandy", "AJ", "Vanessa", "Brian", "Jessica", "Kevin"]
> last_names = ["Smith", "Johnson", "Brown", "Miller", "Garcia", "Acors", "Alday"]
> 
> # ToDo: Create dictionary
> 
> # ToDo: populate dictionary with information
> 
> # ToDo: Get a json representation of the dictionary using the json module
> string_representation = ?
> 
> print(string_representation)
> ```

<details>
  <summary>Click here to show solution</summary>
  
  ```python3
  import random 
  import json

  first_names = ["Nadja", "Nick", "Lucy", "Howie", "Sandy", "AJ", "Vanessa", "Brian", "Jessica", "Kevin"]
  last_names = ["Smith", "Johnson", "Brown", "Miller", "Garcia", "Acors", "Alday"]

  d = {}

  d["first_name"] = random.choice(first_names)
  d["last_name"] = random.choice(last_names)
  d["age"] = random.randint(18, 99)

  string_representation = json.dumps(d)

  print(string_representation)
  ```
</details>

With that, we have covered two modules of the standard library we will be using next week!

<div align="right">
   
   [Prev](random.md) - Next
</div>