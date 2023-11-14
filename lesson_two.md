# Intro to programming w/ Python

**NOTE:NOTE:NOTE:NOTE!**

> From now on we will be using a collaborative real-time coding platform to
learn, practice and run code together!

[Click here to check it
out!](https://replit.com/@JoshJetson/Learningisgood#lesson_2.py)

## Dictionaries, Booleans and Functions, OH MY!

**Dictionaries**


- Dictionaries are used when we need two things associated with each other.
- A dictionary in other languages may be called a hashmap.
- When you start working with APIs your going to recognize the most commonly
used API file format, which is called JSON, as a type of hashmap or
"Dictionary."

> Lets first understand why we might want to use a Dictionary to help us get a
better understanding of exactly what it is.
>
> Consider the following situation:
> > You need to, for whatever reason, associate a students name with their grade
> > You can do something like this following:


```python


list_of_name = ['Yomi', 'Josh', 'Andrew']

list_of_grades = [3.4, 3.2, 4.0]


```

> Alright cool!
> But when I want to access these names or grades I need to access two
separate lists and your gonna find that as this kind of data grows it gets more
and more annoying to manipulate or access the contents of both lists possibly at the same
time.

*Dictionaries to the rescue!!!*

> Check this out!
>


```python

student_grades = {'Yomi': 3.4, 'Josh': 3.2, 'Andrew': 4.0}


```

> What you are seeing above is what is called a {'Key': 'Value'} pair.
> For every Key we have a value of something.
> In this way we could associate two things and access or manipulate them much
easier. Below are some examples of how you might access and manipulate
dictionaries.

```python


student_grades = {'Yomi': 3.4, 'Josh': 3.2, 'Andrew': 4.0}

# Create a new key value pair.

student_grades['Paulina'] = 4.1

print(student_grades)

{'Yomi': 3.4, 'Josh': 3.2, 'Andrew': 4.0, 'Paulina': 4.1}




```
*Recommended*

[Click here for a more in depth look into Dictionaries](https://realpython.com/python-dicts/)




**Booleans**


> In programming we need to use True or False values a lot. We call these
booleans.
> A value of True in programming is equal to anything other than 0 or None
> A False value is equal to 0


```python

switch = True
second_switch = False

if switch:
    print('This thing is True')

if not second_switch:
    print('This thing must be False')


```

> Don't get hung up on this concept right now just keep it in the back of your
mind.
> We will use it plenty and you will start to understand quickly the
usefulness of it conceptually.




**Functions**

> What is a function ?
>
> A function is another type of object in programming. Functions are similar to
really big boxes. You could fit more things into them and get more things out
of them.
>
- A functions value is equal to whatever the heck it gives you back or
"returns."
- The value of a function could also be stored in some other object or it could
simply be used as like a logical process or set of instructions in your program
that ultimately does something.
- At the end of the day a function could do all of the above in the body of the
function and also more. Much more!


> You have already been introduced to functions without you knowing.

```python

print('This is a print function notice how we "Call" the print function')

input('This is another built in function we have used, notice any similarities?')



```

```python

# How do you make a function
# You need the def keyword followed by some other stuff. Observe


def myfunc():
    return 'I guess I am a function whose only value is this dumb sentence.'

# How to call a function

myfunc()

'I guess I am a function whose only value is this dumb sentence.'

```

> You can also create parameters for a function but if you do when you call a
function its going to require arguments.

```python

# A function with one parameter

def myfunc(saying):
    return saying

# Call the function and pass it an argument, because it expects one now.

myfunc('This is now the value of the function')

'This is now the value of the function'

# or

poetic_line = 'To be or not to be'

myfunc(poetic_line)

'To be or not to be'


```

> That doesn't seem too useful. Lets check out some other examples

```python

# Multiple parameters

def myfunc(first_number, second_number):
    first_number = first_number * .1
    second_number = second_number * .5
    combined = first_number + second_number
    divided = combined / first_number
    months = 12
    calculation = divided / months
    return calculation

last_months_clients = 128
new_monthly_clients = 35


# Lets use a print function with an f string to display the output of the above
# function in a nice way

print(f'Your growth percentage this month is {myfunc(last_months_clients,
new_monthly_clients)} %')


'Your growth percentage this month is 0.197265625 %'

```


> Some other ways to use a function.
>

```python


def my_program():
    question = input('How old are you ?: ')
    if int(question) >= 21:
        print('You are old enough to buy a beer.')
        question = input('Would you like to play again? ')
        if question == 'y':
            my_program()
        else:
            return 'Good Bye!'
    if int(question) < 21:
        print('You need to go home and eat some candy child!')
        question = input('Would you like to play again? ')
        if question == 'y':
            my_program()
        else:
            return 'Good Bye!'

my_program()


```


[Click here for more extensive info on functions](https://realpython.com/defining-your-own-python-function/#functions-in-python)
