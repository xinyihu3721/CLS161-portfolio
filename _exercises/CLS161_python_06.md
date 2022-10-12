---
layout: page
title: Exercises Ch. 6
description: Python Crash Course Chapter6 Exercises
---
# Python Crash Course Chapter 6

## 6-1. Person: 
Use a dictionary to store information about a person you know. Store their first name, last name, age, and the city in which they live. You should have keys such as `first_name`, `last_name`, `age`, and `city`. Print each piece of information stored in your dictionary.


```python
person = {'first_name':'Xinyi','last_name':'Hu','age':21,'city':'Medford'}
print(person['first_name'])
print(person['last_name'])
print(person['age'])
print(person['city'])
```

    Xinyi
    Hu
    21
    Medford


## 6-2. Favorite Numbers ##
Use a dictionary to store people’s favorite numbers. Think of five names, and use them as keys in your dictionary. Think of a favorite number for each person, and store each as a value in your dictionary. Print each person’s name and their favorite number. For even more fun, poll a few friends and get some actual data for your program.


```python
fav_number = {'Selena':7,'Tony':21,'Amy':9,'Latte':1,'Mocha':3}
for n in fav_number:
    print (n, fav_number[n])
```

    Selena 7
    Tony 21
    Amy 9
    Latte 1
    Mocha 3


## 6-3. Glossary: 
A Python dictionary can be used to model an actual dictionary. However, to avoid confusion, let’s call it a glossary.

- Think of five programming words you’ve learned about in the previous chapters. Use these words as the keys in your glossary, and store their meanings as values.
- Print each word and its meaning as neatly formatted output. You might print the word followed by a colon and then its meaning, or print the word on one line and then print its meaning indented on a second line. Use the newline character (`\n`) to insert a blank line between each word-meaning pair in your output.


```python
glossary = {'Algorithm':'A list of instructions, procedures, or formulas used to solve a problem.','variable':'A location capable of storing temporary data within a program.','function':"A piece of code that can be called",'Loop':'A loop describes the process of a software program or script repeats the same instructions or processes the same information over and over until receiving the order to stop. Loops are restricted to a specific area of the program','code':'Is a language of letters, numbers and symbols used to give a computer a set of instruction.'}
for n in glossary:
    print (f'{n.title()}: {glossary[n]}\n')
```

    Algorithm: A list of instructions, procedures, or formulas used to solve a problem.
    
    Variable: A location capable of storing temporary data within a program.
    
    Function: A piece of code that can be called
    
    Loop: A loop describes the process of a software program or script repeats the same instructions or processes the same information over and over until receiving the order to stop. Loops are restricted to a specific area of the program
    
    Code: Is a language of letters, numbers and symbols used to give a computer a set of instruction.
    


## 6-4. Glossary 2: 
Now that you know how to loop through a dictionary, clean up the code from Exercise 6-3 (page 99) by replacing your series of print() calls with a loop that runs through the dictionary’s keys and values. When you’re sure that your loop works, add five more Python terms to your glossary. When you run your program again, these new words and meanings should automatically be included in the output.


```python
glossary = {'Algorithm':'A list of instructions, procedures, or formulas used to solve a problem.','variable':'A location capable of storing temporary data within a program.','function':"A piece of code that can be called",'Loop':'A loop describes the process of a software program or script repeats the same instructions or processes the same information over and over until receiving the order to stop. Loops are restricted to a specific area of the program','code':'Is a language of letters, numbers and symbols used to give a computer a set of instruction.','Byte': 'A common unit of digital data','Command': 'A section of code that tells the computer to do one thing','Input': 'The way a computer receives information','IP Address': 'A number assigned to every device that is connected to the Internet','Program': 'An algorithm that has been coded by a programmer into something that can be run by a device','URL': 'A Uniform Resource Locator, an easy-to-remember name you can use to find a specific Web page'}
for n in glossary:
    print (f'{n.title()}: {glossary[n]}\n')
```

    Algorithm: A list of instructions, procedures, or formulas used to solve a problem.
    
    Variable: A location capable of storing temporary data within a program.
    
    Function: A piece of code that can be called
    
    Loop: A loop describes the process of a software program or script repeats the same instructions or processes the same information over and over until receiving the order to stop. Loops are restricted to a specific area of the program
    
    Code: Is a language of letters, numbers and symbols used to give a computer a set of instruction.
    
    Byte: A common unit of digital data
    
    Command: A section of code that tells the computer to do one thing
    
    Input: The way a computer receives information
    
    Ip Address: A number assigned to every device that is connected to the Internet
    
    Program: An algorithm that has been coded by a programmer into something that can be run by a device
    
    Url: A Uniform Resource Locator, an easy-to-remember name you can use to find a specific Web page
    


## 6-7. 
People: Start with the program you wrote for Exercise 6-1 (page 99). Make two new dictionaries representing different people, and store all three dictionaries in a list called people. Loop through your list of people. As you loop through the list, print everything you know about each person.




```python
person1 = {'first_name':'Xinyi','last_name':'Hu','age':21,'city':'Medford'}
person2 = {'first_name':'Latte','last_name':'Hu','age':1,'city':'Medford'}
person3 = {'first_name':'Mocha','last_name':'Zhang','age':1,'city':'Medford'}
people = [person1,person2,person3]
for person in people:
    print(person['first_name'],person['last_name'],person['age'],'city')
```

    Xinyi Hu 21 city
    Latte Hu 1 city
    Mocha Zhang 1 city


# 6-8. Pets: 
Make several dictionaries, where each dictionary represents a different pet. In each dictionary, include the kind of animal and the owner’s name. Store these dictionaries in a list called pets. Next, loop through your list and as you do, print everything you know about each pet.


```python
pet1 = {'name' : 'Latte','kind':'cat','owner':'Selena'}
pet2 = {'name' : 'Mocha', 'kind':'dog','owner':'Theo'}
pet3 = {'name' : 'Micky', 'kind':'rat','owner':'Shirley'}
pets = [pet1,pet2,pet3]
for p in pets:
    print(f"{p['name']} is a {p['kind']}, and its owner is {p['owner']}.")
```

    Latte is a cat, and its owner is Selena.
    Mocha is a dog, and its owner is Theo.
    Micky is a rat, and its owner is Shirley.


## 6-9. Favorite Places: 
Make a dictionary called `favorite_places`. Think of three names to use as keys in the dictionary, and store one to three favorite places for each person. To make this exercise a bit more interesting, ask some friends to name a few of their favorite places. Loop through the dictionary, and print each person’s name and their favorite places.


```python
favorite_places = {
    'Selena': ['Boston', 'Yellow Stone Park', 'Arcadia'],
    'Alice': ['Hawaii', 'Norway'],
    'Peter': ['China', 'Thailand', 'Brazil']
    }

for name, places in favorite_places.items():
    print(name + " likes the following places:")
    for place in places:
        print("- " + place+"\n")
```

    Selena likes the following places:
    - Boston
    
    - Yellow Stone Park
    
    - Arcadia
    
    Alice likes the following places:
    - Hawaii
    
    - Norway
    
    Peter likes the following places:
    - China
    
    - Thailand
    
    - Brazil
    


## 6-11. Cities: 
Make a dictionary called `cities`. Use the names of three cities as keys in your dictionary. Create a dictionary of information about each city and include the country that the city is in, its approximate population, and one fact about that city. The keys for each city’s dictionary should be something like `country`, `population`, and `fact`. Print the name of each city and all of the information you have stored about it.


```python
cities = {
    'paris': {
        'country': 'france',
        'population': 2161000,
        'nearby mountains': 'northern alps',
        },
    'guiyang': {
        'country': 'china',
        'population': 4679000,
        'nearby mountains': 'qianling',
        },
    'kathmandu': {
        'country': 'nepal',
        'population': 1003285,
        'nearby mountains': 'himilaya',
        }
    }

for city, city_info in cities.items():
    country = city_info['country'].title()
    population = city_info['population']
    mountains = city_info['nearby mountains'].title()

    print(city.title() + " is in " + country + ".")
    print("  It has a population of about " + str(population) + ".")
    print("  The " + mountains + " mountains are nearby."+"\n" )
```

    Paris is in France.
      It has a population of about 2161000.
      The Northern Alps mountains are nearby.
    
    Guiyang is in China.
      It has a population of about 4679000.
      The Qianling mountains are nearby.
    
    Kathmandu is in Nepal.
      It has a population of about 1003285.
      The Himilaya mountains are nearby.
    

