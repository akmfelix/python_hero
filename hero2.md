# Object Oriented Programming
## OOP
* OOP allows programmers to create their own objects that have methods and attributes.
* These methods act as functions that use information about the object, as well as the object itselt to return results, or change the current object.
* OOP allows us to create code that is repeatable and organized.
* For much larger scripts of Python code, functions by themselves aren't enough for organization and repeatablity. Commonly repeated tasks and objects can be defined with OOP to create code that is more usable.
* __init__ - can basically be thought as the constructor for a class, and it's going to be called automatically when you create an instance of the class.
* self - keyword. It represents the instance of the object itself.
* One of the issues with Python being so flexible is that later on when you're a programmer and expecting other people to use your classes, you're going to need to add in some documentation to let them know, hey, I'm expecting strings for breed, strings for name, and spots should be a Boolean, because right now, I could say something like, 'no spots'.
* But right now, what I really wanna focus on is the basic idea that you use the class keyword with capitalized names, you define the name of your class. And the very first method in your class is going to be a special method called the __init__ method. And this init method acts as a constructor. And we have this self keyword which is a reference to the instance of the class. So that instance of the class is then going to have these .attributes that you pass in based off what parameters you define up here. And by convention, the parameter name, the attribute name are the same, which means you will see it three times, once when you pass it in, and then once here for the attribute, and once for the actual assignment call.

~~~
___________________________________________________
class Sample():
    pass

# instance of a Sample class
my_sample = Sample()
type(my_sample)
# __main__.Sample

___________________________________________________
class Dog():
    def __init__(self, breed):
        self.breed = breed
my_dog = Dog(breed='Lab')
my_dog.breed
# 'Lab'

___________________________________________________
class Dog():
    def __init__(self, mybreed):
        # Attributes
        # We take in the argument
        # Assign it using self.attribute_name
        self.my_attribute = mybreed
my_dog = Dog(mybreed='Huskie')
my_dog.my_attribute
# 'Huskie'
~~~

~~~
___________________________________________________
class Dog():
    def __init__(self, breed, name, spots):
        self.breed = breed
        self.name = name
        self.spots = spots
my_dog = Dog(breed='Lab', name='Sammy', spots = True)
my_dog = Dog.breed
# Lab
my_dog.name
# Sammy
my_dog.spots
# True
~~~

~~~
___________________________________________________
class Dog():
    # class object attribute
    # same for any instance of a class
    species = 'mammal'
    
    def _init(self, breed, name, spots):
        self.breed = breed
        self.name = name
        self.spots = spots

my_dog = Dog(breed='Lab', name='Sammy', spots = True)
my_dog = Dog.species
# 'mammal'
~~~

* Notice that attributes never had open and close parentheses. And that's because attributes aren't really something that you execute. Instead it's just something that's a characteristic of the object that you call back.
~~~
___________________________________________________
class Dog():
    # class object attribute
    # same for any instance of a class
    species = 'mammal'
    
    def __init__(self, breed, name):
        self.breed = breed
        self.name = name

    # OPERATIONS/ Actions ---> Methods
    def bark(self):
        print(f'Boooo!! My name is {self.name}')
my_dog = Dog(breed='Cat', name='Cucumber')
my_dog.bark()
# Boooo!!

___________________________________________________
class Dog():
    # class object attribute
    # same for any instance of a class
    species = 'mammal'
    
    def __init__(self, breed, name):
        self.breed = breed
        self.name = name

    # OPERATIONS/ Actions ---> Methods
    def bark(self, food):
        print(f'Boooo!! My name is {self.name} and my favorite food is {food}.')
my_dog = Dog(breed='Cat', name='Cucumber')
my_dog.bark(food='meat')
Boooo!! My name is Cucumber and my favorite food is meat.
~~~

~~~
___________________________________________________
class Circle():
    # CLASS OBJECT ATTRIBUTE
    pi = 3.14
    def __init__(self, radius=1):
        self.radius = radius
    # METHOD
    def area(self):
        return self.pi * self.radius**2
my_circle = Circle(radius=5)
my_circle.area()
# 78.5
my_circle.pi
# 3.14
my_circle.radius
# 5

___________________________________________________
class Circle():
    # CLASS OBJECT ATTRIBUTE
    pi = 3.14
    def __init__(self, radius=1):
        self.radius = radius
        self.circumference = 2 * self.pi * self.radius
        # or self.circumference = 2 * self.pi * Circle.radius
    # METHOD
    def area(self):
        return self.pi * self.radius**2
        # or return Circle.pi * self.radius**2
~~~








