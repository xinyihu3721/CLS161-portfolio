---
layout: page
title: Exercises Ch. 5
description: Python Crash Course Chapter5 Exercises
---
# Python Crash Course Chapter 5

## 5-1. Conditional Tests
Write a series of conditional tests. Print a statement describing each test and your prediction for the results of each test. 

**Note: when use < or > to compare string variables, we are comparing their length**


```python
butterfly = 'Lycaenidae'
print("Is butterfly == 'Lycaenidae'? I predict True.")
print(butterfly == 'Lycaenidae')

print("\nIs butterfly == 'Tiger Swallowtail'? I predict False.")
print(butterfly == 'Tiger Swallowtail')

print("\nIs butterfly != 'Tiger Swallowtail'? I predict True.")
print(butterfly != 'Tiger Swallowtail')

print("\nIs butterfly < 'Tiger Swallowtail'? I predict False.")
print(butterfly < 'Tiger Swallowtail')

print("\nIs butterfly > 'Tiger Swallowtail'? I predict False.")
print(butterfly > 'Tiger Swallowtail')
```

    Is butterfly == 'Lycaenidae'? I predict True.
    True
    
    Is butterfly == 'Tiger Swallowtail'? I predict False.
    False
    
    Is butterfly != 'Tiger Swallowtail'? I predict True.
    True
    
    Is butterfly < 'Tiger Swallowtail'? I predict False.
    True
    
    Is butterfly > 'Tiger Swallowtail'? I predict False.
    False


## 5-2. More Conditional Tests

You don’t have to limit the number of tests you create to ten. If you want to try more comparisons, write more tests and add them to conditional_tests.py. Have at least one True and one False result for each of the following:

- Tests for equality and inequality with strings
- Tests using the `lower()` method
- Numerical tests involving equality and inequality, greater than and less than, greater than or equal to, and less than or equal to
- Tests using the `and` keyword and the `or` keyword
- Test whether an item is in a list
- Test whether an item is not in a list


```python
print("Is butterfly == 'Lycaenidae'? I predict True.")
print(butterfly == 'Lycaenidae')

print("\nIs butterfly == 'lycaenidae'? I predict False.")
print(butterfly == 'lycaenidae')
```

    Is butterfly == 'Lycaenidae'? I predict True.
    True
    
    Is butterfly == 'lycaenidae'? I predict False.
    False



```python
print("\nIs butterfly == 'lycaenidae'? I predict False.")
print(butterfly.lower() == 'lycaenidae')
```

    
    Is butterfly == 'lycaenidae'? I predict False.
    True



```python
print("31%3 != 2? I predict True.")
print(31%3 != 2)
print("1+1 == 2? I predict True.")
print(1+1 == 2)
print("200 > 2? I predict True.")
print(200 > 2)
print("-1 < 5? I predict True.")
print(-1 < 5)
```

    31%3 != 2? I predict True.
    True
    1+1 == 2? I predict True.
    True
    200 > 2? I predict True.
    True
    -1 < 5? I predict True.
    True



```python
print("200 > 2 and -1 < 5? I predict True.")
print((200 > 2)& (-1 < 5))
```

    200 > 2 and -1 < 5? I predict True.
    True



```python
historian = ["gibbon","eusebius","livy"]
print('Is gibbon" in historian? I predict Ture.')
print("gibbon" in historian)
```

    Is gibbon" in historian? I predict Ture.
    True



```python
historian = ["gibbon","eusebius","livy"]
print('Is Hume" in historian? I predict False.')
print("Hume" in historian)
```

    Is Hume" in historian? I predict False.
    False


## 5-6. Stages of Life

Write an if-elif-else chain that determines a person’s stage of life. Set a value for the variable age, and then:

- If the person is less than 2 years old, print a message that the person is a baby.
- If the person is at least 2 years old but less than 4, print a message that the person is a toddler.
- If the person is at least 4 years old but less than 13, print a message that the person is a kid.
- If the person is at least 13 years old but less than 20, print a message that the person is a teenager.
- If the person is at least 20 years old but less than 65, print a message that the person is an adult.
- If the person is age 65 or older, print a message that the person is an elder.


```python
age = 21
if age < 2:
    print("the person is a baby")
elif age < 4:
    print("the person is a toddler.")
elif age < 13:
    print("the person is a kid")
elif age < 20:
    print("the person is a teenager")
elif age <65:
    print("the person is an adult")
else:
    print("the person is an elder")
```

    the person is an adult


## 5-7. Favorite Fruit

Make a list of your favorite fruits, and then write a series of independent if statements that check for certain fruits in your list.

- Make a list of your three favorite fruits and call it favorite_fruits.
- Write five if statements. Each should check whether a certain kind of fruit is in your list. If the fruit is in your list, the if block should print a statement, such as You really like bananas!



```python
favorite_fruits=['oranges','mangoes','strawberry']
fruits=['apples','oranges','bananas','mangoes','grapes','strawberry']
for f in fruits:
    if f in favorite_fruits:
        print(f"I really like {f}")
```

    I really like oranges
    I really like mangoes
    I really like strawberry


## 5-8. Hello Admin

Make a list of five or more usernames, including the name 'admin'. Imagine you are writing code that will print a greeting to each user after they log in to a website. Loop through the list, and print a greeting to each user:

- If the username is 'admin', print a special greeting, such as Hello admin, would you like to see a status report?
- Otherwise, print a generic greeting, such as Hello Jaden, thank you for logging in again.


```python
usernames = ['admin','selena3721','xhu07','asfr','forever0007']
for name in usernames:
    if name == 'admin':
        print('Hello admin, would you like to see a status report?')
    else:
        print(f'Hello {name}, thank you for logging in again.')
```

    Hello admin, would you like to see a status report?
    Hello selena3721, thank you for logging in again.
    Hello xhu07, thank you for logging in again.
    Hello asfr, thank you for logging in again.
    Hello forever0007, thank you for logging in again.


## 5-9. No Users

Add an if test to hello_admin to make sure the list of users is not empty.

- If the list is empty, print the message We need to find some users!
- Remove all of the usernames from your list, and make sure the correct message is printed.


```python
usernames = []
if usernames:
    for name in usernames:
        if name == 'admin':
            print('Hello admin, would you like to see a status report?')
        else:
            print(f'Hello {name}, thank you for logging in again.')
else:
    print('We need to find some users!')
```

    We need to find some users!


## 5-10. Checking Usernames

Do the following to create a program that simulates how websites ensure that everyone has a unique username.

- Make a list of five or more usernames called current_users.
- Make another list of five usernames called new_users. Make sure one or two of the new usernames are also in the current_users list.
- Loop through the new_users list to see if each new username has already been used. If it has, print a message that the person will need to enter a new username. If a username has not been used, print a message saying that the username is available.
- Make sure your comparison is case insensitive. If 'John' has been used, 'JOHN' should not be accepted. (To do this, you’ll need to make a copy of current_users containing the lowercase versions of all existing users.)


```python
usernames = ['admin','selena3721','xhu07','XHU07','XINYI3721']
new_users = ['XHU07','XINYI3721','happy_dog','Life0926']
for name in new_users:
    if name in usernames:
        print(f'{name} is not available, please enter a different username.')
    else:
        print(f'{name} is available.')
```

    XHU07 is not available, please enter a different username.
    XINYI3721 is not available, please enter a different username.
    happy_dog is available.
    Life0926 is available.

