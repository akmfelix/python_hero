# Object Oriented Programming
## OOP in Python
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
        self.circumference = 2 * Circle.pi * self.radius
        # or self.circumference = 2 * Circle.pi * pi.radius
    # METHOD
    def area(self):
        return self.pi * self.radius**2
        # or return Circle.pi * self.radius**2
~~~

## Inheritance and Polymorphism
### Inheritance
* An Inheritance is a way to form new classes using classes that have already been defined.
* Benefits from using an Inheritance are the ability to reuse code that you've already worked on and to reduce the complexity of a program.
* The main idea in INHERITANCE is that: all you need to do is inherit from your base class and now you have access to all those old methods.
* And if you ever want to overwrite them, you can just overwrite them. Recall the same method name and then do whatever you want there.
* And you can always add in more methods.
* SO that's how inheritance works.

~~~
___________________________________________________
## Create an instance of the Animal() class.
## I have base class Animal and then I have my other class of Dog, which is going to inherit the methods of the Animal class.
## Also all those old methods that where available for the Animal are now available for mydog,
## because I was able to derive them from my base class Animal. It's a main idea for inheritance.

class Animal():
    def __init__(self):
        print('ANIMAL CREATED')
    def who_am_i(self):
        print('I am an animal')
    def eat(self):
        print('I am eating')

myanimal = Animal()
# ANIMAL CREATED
myanimal.eat()
# I am eating
myanimal.who_am_i()
I am an animal


class Dog(Animal):
## use already defined method from base class
    def __init__(self):
        Animal.__init__(self)
        print('Dog created')
## Additionally you can OVERWRITE older methods.
    def eat(self):
        print('I am a Dog and eating')
## Add on methods.
    def bark(self):
        print('WHOOF!')
mydog = Dog()
# ANIMAL CREATED
# Dog created
mydog.eat()
# I am a Dog and eating
mydog.who_am_i()
# I am an animal
myanimal.who_am_i()
# I am an animal
mydog.bark()
# WHOOF!
~~~

### Polymorphism
* in Python, Polymorphism refers to the way in which different object classes can share the same method name \n
* and then those methods can be called from the same place even though a variety of different objects might be passed in.
* Basic idea is you have these two separate classes that happen to share the same method name, allowing you to then call those same method names \n
* without needing to worry about the specific class that's being passed in.


~~~
___________________________________________________
## So here we have a Dog class and a Cat class. Each of them has the speak method. When called each objects speak method, returns a result.
## That's unique to the object. That is to say it's unique for the dog to say woof and it's unique to the cat to say meow,
## as well as their names are going to be unique to that particular instance of the class.

class Dog():
    def __init__(self, name):
        self.name = name
    def speak(self):
        return self.name + ' says Whoof!'

class Cat():
    def __init__(self, name):
        self.name = name
    def speak(self):
        return self.name + ' says Meow!'

mydog = Dog('Morris')
mycat = Cat('Cucumber')
mydog.speak()
mycat.speak()
# 'Morris says Whoof!'
# 'Cucumber says Meow!'

___________________________________________________
for pet in [mydog,mycat]:
    print(type(pet))
    print(pet.speak())
# <class '__main__.Dog'>
# Morris says Whoof!
# <class '__main__.Cat'>
# Cucumber says Meow!

___________________________________________________
def pet_speak(pet):
    print(pet.speak())
pet_speak(mydog)
# Morris says Whoof!
pet_speak(mycat)
# Cucumber says Meow!
~~~

* Base class - as to raise an error in polymorphism
~~~
___________________________________________________
class Animal():
    def __init__(self, name):
        self.name = name
    def speak(self):
        raise NotImplementedError('Subclass must implenet this abstract method')
myanimal = Animal('fred')
myanimal.speak()
# NotImplementedError: Subclass must implement this abstract method.

class Dog(Animal):
    def speak(self):
        return self.name + ' says whoof'

class Cat(Animal):
    def speak(self):
        return self.name + ' says meow'

mydog = Dog('Morris')
mycat = Cat('Cucumber')

mydog.speak()
# 'Morris says whoof'
mycat.speak()
'Cucumber says meow'
~~~



