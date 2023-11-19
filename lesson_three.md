# Lesson Three


--------------------------------




<table rules=none>
 <tr>
<td> <img src="https://imgur.com/CXZP3Rn.png"></td>
<td> <h2><a href="https://joshjetson.github.io">Intro to<br>The Building Blocks<br>of Code <br> PT.1 </a></h2><br>This lesson covers: Classes, Attributes, Properties, Instances (Objects) and Loops</td>
</tr>
</table>



*Let us attempt to unravel the fabric of the python programming language. Piece by Piece!*

## PART ONE (Classes)

-----------------------------------------

**A Class**


> To be ablet to truly understand python, and most other programming languages, we have to understand a class.
> - What a class is, what it really is..
> - What a class property is.
> - What a method is.
> - How to access class methods, attributes and properties


> What is a class ?:

- A Class is a blueprint.
> - A Blueprint of what ?
> > A Blueprint for an Object......

- What is an Object ?
> - An Object is an instance of a class !
>
> *Huh ???? What ???? I'm lost i'm over programming.*


#### Before you lose your shirt .... Chill.

> Ok yea its confusing so let's put this into a context that is not confusing.
>
>
> Lets use some real life objects as examples.
> - A Watch
> - A House
> - A Desk

> Suppose I create some cool new design for a type of house and now I want to show others how to build this cool new house.
> How could I do this easily ?
> > - One way is by making a blueprint of how the house needs to be built and then having the blueprints accessible for people to study and view.
>
> Now suppose some people build some houses based on the blueprints, on the outside of all of the houses we see what looks like the same house.
> > But are the houses the same house ? No. They are different. They have different owners and contain different things inside of them.
> > - Might we know how to access all of the rooms in all of the houses though ? Yes because they were all built from the same blueprint.
>
> This is very closely related to the idea of a class. 
>
> When You build a house based on a blueprint, the house is not the blueprint the house is a physical instance of a blueprint.
> The blueprint contains default  attributes and properties for each room but as the house is built each room may contain a series of different elements dependant on the users needs.

*Following the house analogy*

- A class is the blueprint
- An object is the house.
- Just as each house has the ability to be different inside, so does each object built from the same blueprint.
- Rephrased: Just as each house has the ability to be different inside, so does each object *instantiated* from the same *class.*


**The Really Cool Part!**


Everything in python, and most other Object Oriented Programming languages, is an Object !
And remember, every object is an instance of a class.

> This means
> - Everything has attributes and likely properties.
> - Attributes can be accessed or modified
> - You can learn how the object is intended to be used by looking at its class.
> - Coolest of all, when you create a class you can define how each Object instance of it is supposed to behave!


> Lets have a look at a very simple class with some class attributes.
>



```python

class Example:
  attribute_one = 'This is a class attribute'
  attribute_two = 40

# Instantiate the class to create a new object.

my_simple_name - Example()# The name of this object is my_simple_name

# Print out or access the newly created objects attributes

print(my_simple_name.attribute_one)



```


> Lets pause for a second. 
>


```python

# See this dot, the dot after name 

my_simple_name.attribute_one

# We use this dot to access object attributes, properties and methods.
# In object oriented programming its called the dot notation.
# It is a common convention for object oriented programming languages and is not exclusive to Python.
# If you use it, your accessing something that belongs to an object and was defined in a class.


```





**Lesson 3 Lecture Notes**


```python

# Functions Vs Methods
# Under here under here this thing under here

new_list = [1, 4, 5]
new_list.append(6)


class myClass:
  def __init__(self, name, age):
    self.name = name
    self.age = age
    self.name_age = f'{name} age {age}'
    self.age_name = f'{age} name {name}'
    self.age_squared = age ** 2

  def print_name(self):
    return self.name

  def print_age(self):
    return self.age

  def print_name_age(self):
    return self.name, self.age

# This is one instance of myClass and is now an object
instance_one = myClass('Yomi', 36)

# This is a second instance of myClass and is now another object
instance_two = myClass('Josh', 40)

print(instance_two.age_name)

print(instance_one.age_squared)
# This is how we can print the print_name method per object
print(instance_one.print_name())

# This is how we can access or call the print_name method
instance_one.print_name()

instance_one.print_age()
print(instance_one.print_age())
instance_two.print_age()
print(instance_two.print_name_age())

# Accesing a property direcly
print(instance_one.name_age)



```
