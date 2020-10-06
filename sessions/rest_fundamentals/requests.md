# Consuming REST APIs with requests and python

If you come from a different programming language you might be terrified about having to do web requests with it. In the past it had been pretty cumbersome to do web requests from a programming language. Fundamentally this is still true but the python community has done a great job in abstracting this complexity away into packages. 

The package we are going to use today is called `requests`. In your online editor you can go ahead and just import it into your script like we have seen in the previous sessions. 

```python

import requests
```

> :rocket: `requests` is not part of the python standard library but rather part of the python package ecosystem. If you want to learn more about these and how to install them check out the additional session on [PIP, PyPi and the Python Package Ecosystem](../extras/pip_and_pypi/Readme.md).

With `requests` imported we can go ahead and make our first HTTP request from python! The deck of cards API allows us to "draw" a card by sending a `GET` request to `https://deckofcardsapi.com/api/deck/<<deck_id>>/draw/`. As you can see we have the `deck_id` of the card we want to request as a *Path Segment Parameter*. 

Using the the Id we got from the request with Postman lets construct the url we have to request:

```python

deck_id = "bv6t3gdoujzd" #Note: Yours will be different

url = "https://deckofcardsapi.com/api/deck/" + str(deck_id) + "/draw/"
```

Next, we need to tell the deck of cards api, using the `count` query parameter, how many cards to draw from our deck. We could hard-code this parameter into the url but a nicer way to do it is to create a parameter dictionary

```python
parameters = {
   'count': 1
}
```

Finally, we need to do our get request. This is done using the `requests.get` method. 

```python
response = requests.get(url, params=parameters)
```

And that's it. The full script then looks like this:

```python
import requests

deck_id = "bv6t3gdoujzd" #Note: Yours will be different

url = "https://deckofcardsapi.com/api/deck/" + str(deck_id) + "/draw/"

parameters = {
   'count': 1
}

response = requests.get(url, params=parameters)
```

Pretty neat but so far we are not doing anything with our response. So lets first print out the status code. It's always good practice to check this code in order to make sure that the request has been fulfilled correctly. 

In `requests` the response object returned has a argument called `status_code` that contains our return code. So lets go ahead an print that:

```python

return_code = response.status_code

print("Web request had a status of " + str(return_code))
```

Now we would also like to access the *information* returned by the response. As you have seen in the Postman section the deck of cards API returns a json string. We *could* go ahead and use `response.text` to retrieve the raw json string that the API has returned and parse that using the `json` module. However, we can also use the easier to use `response.json()` method that will automatically parse the json and return a dictionary. 

So let's go ahead and retrieve the cards json into a dictionary and print out all the keys. 

```python

card = response.json()

for key in card.keys():
   print("- " + str(key))
```

One property of the json is a list of cards that have been retrieved (stored in the `cards` attribute). So as a final step lets go ahead and get the first card and print out the code of it. 

```
card_code = card['cards'][0]['code']

print("Card code is: " + str(card_code))
```

And thats it! You can now make requests using the `requests` library right from your python script. The complete script looks like this: 

```python

import requests

deck_id = "bv6t3gdoujzd" #Note: Yours will be different

url = "https://deckofcardsapi.com/api/deck/" + str(deck_id) + "/draw/"

parameters = {
   'count': 1
}

response = requests.get(url, params=parameters)

return_code = response.status_code

print("Web request had a status of " + str(return_code))

card = response.json()
card_code = card['cards'][0]['code']

print("Card code is: " + str(card_code))
```
 
 > :rocket: We have not covered authentication as well as other types of requests like `POST` in this section. If you are interested have a look at the additional session on [Authentication in REST](../extras/authentication_in_rest/Readme.md).
 
<div align="right">
   
   [Prev](postman.md) - [Next](next_steps.md)
</div>