---
layout: page
title: Exercises Ch. 8
description: Python Crash Course Chapter6 Exercises
---
# Python Crash Course Chapter 8

## 8-1. Message:
Write a function called `display_message()` that prints one sentence telling everyone what you are learning about in this chapter. Call the function, and make sure the message displays correctly.


```python
def display_message():
  print("I am learning Chapter8 about writin functions in python")

display_message()
```

    I am learning Chapter8 about writin functions in python


## 8-2. Favorite Book:
 Write a function called `favorite_book()` that accepts one parameter, `title`. The function should print a message, such as `One of my favorite books is Alice in Wonderland`. Call the function, making sure to include a book title as an argument in the function call.


```python
def favorite_book(title):
  print(f'One of my favorite books is {title.title()}.')

favorite_book('lincoln in the bardo')
```

    One of my favorite books is Lincoln In The Bardo.


## 8-3. T-Shirt:
Write a function called `make_shirt()` that accepts a size and the text of a message that should be printed on the shirt. The function should print a sentence summarizing the size of the shirt and the message printed on it.


  Call the function once using positional arguments to make a shirt. Call the function a second time using keyword arguments.


```python
def make_shirt(size, text):
  print("\nThis is a " + size + " t-shirt.")
  print('The text is "' + text + '".')
make_shirt('Small', 'Good morning')
make_shirt(text="Meow", size='Medium')
```

    
    This is a Small t-shirt.
    The text is "Good morning".
    
    This is a Medium t-shirt.
    The text is "Meow".


## 8-5. Cities: 
Write a function called describe_city() that accepts the name of a city and its country. The function should print a simple sentence, such as Reykjavik is in Iceland. Give the parameter for the country a default value. Call your function for three different cities, at least one of which is not in the default country.


```python
def describe_city(city, location = 'U.S'):
  print(f'{city.title()} is in {location.title()}')

describe_city('Boston')
describe_city('Beijing', 'China')
describe_city('san francisco')
```

    Boston is in U.S
    Beijing is in China
    San Francisco is in U.S


## 8-6. City Names:
 Write a function called city_country() that takes in the name of a city and its country. The function should return a string formatted like this:
```
 "Santiago, Chile"
```
Call your function with at least three city-country pairs, and print the values that are returned.




```python
def city_country(city,country):
  return city.title()+", "+country.title()


print(city_country('Santiago', 'Chile'))
print(city_country('victoria', 'canada'))
print(city_country('paris', 'France'))
```

    Santiago, Chile
    Victoria, Canada
    Paris, France


## 8-7. Album: 
Write a function called make_album() that builds a dictionary describing a music album. The function should take in an artist name and an album title, and it should return a dictionary containing these two pieces of information. Use the function to make three dictionaries representing different albums. Print each return value to show that the dictionaries are storing the album information correctly.


Use None to add an optional parameter to make_album() that allows you to store the number of songs on an album. If the calling line includes a value for the number of songs, add that value to the album’s dictionary. Make at least one new function call that includes the number of songs on an album.


```python
def make_album(artist_name, album_title,tracks=None):
  album = {'artist_name':artist_name.title(),'album_title':album_title.title()}
  if tracks:
        album['tracks'] = tracks
  return album


album = make_album('Taylor Swift', '1989')
print(album)

album = make_album('Beyonce', 'Beyonce')
print(album)

album = make_album('The Beatles',"Sgt. Pepper's Lonely Hearts Club Band",tracks = 7)
print(album)
```

    {'artist_name': 'Taylor Swift', 'album_title': '1989'}
    {'artist_name': 'Beyonce', 'album_title': 'Beyonce'}
    {'artist_name': 'The Beatles', 'album_title': "Sgt. Pepper'S Lonely Hearts Club Band", 'tracks': 7}

