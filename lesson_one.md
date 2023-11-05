# Intro to programming w/ Python

## Lesson 1


**Object Oriented Programming aka OOP**

> Everything in python is an object!
- What does this mean ?

> In order to understand what it means we have to understand
> what a property of something is.

- We can think of a box which has dimensions:
> - Length 
> - Width
> - Height 
> - Depth

> These dimensions of the box are properties of it.
> In a similar way in O.O.P when we create an object it has its own inherit set of properties.

- This idea may still not make complete sense to you yet but in further lessons it will.

**Kinds of objects**

> There are different kinds of objects in programming.
In this lesson we discussed:

- Variables

```python

number = 55
name = 'Josh'
animal = 'dog'
percent = 2.5

```

- Arrays or Lists

```python

students = ['Jim','Sasha','Liam','Raul']
grades = [3.4, 4.1, 4, 3.5]

# The list below is a list of the above lists

scoring = [grades, students]

```

- The print function (Used to print things out to the terminal or screen)

```python

print(' The number needs to be numerical, Please try again!')

# If the objects have been created you can print them directly

print(students)
print(grades)

```
- The input function

```python
# Tying all the concepts in lesson 1 together


question = input(' How old are you? ')
question = int(question) # You will understand this part later



if question >= 21:
    print(' COOL you can buy us beer!')
else:
    print(' Go back home and eat some candy! ')

```
**Concepts**

> We discussed a couple concepts:

- Data Types

> - Strings
```python

# This is a string
word = 'Hello'
# This is also a string
word = "Hello"
# You choose single or double quotes

```
> - Integers (Non Decimal numerical values)
> - Floats (Decimals)

- Conditionals or an Expression
> - if
> - elif
> - else

```python
this = 500
that = 'Nice number bro!'
other_thing = ' Not as cool as 500 bro'
something_else = 'Straight up something else happening here.'

if this >= 500:
    print(that)
elif this < 500:
    print(other_thing)
else:
    print(something_else)

```


- Operators

```python

# Equal to
==
# Greater than
>
# Less than
<
# Greater than or equal to
>=
# Less than or equal to
<=
# Not equal to
!=


```

- Operators are used in expressions and evaluate to either true or false.
> *You don't have to use operators only in a conditional you can ask the question straight away*
> - EX.

```python

# If you type the following in a python interpreter python will evaluate the expression and return
# either a true or a false value.

5 == 5
True

5 >= 44
False

4 != 55
False


```
