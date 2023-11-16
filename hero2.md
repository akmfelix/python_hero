# Object Oriented Programming
User defined objects are created using the class keyword. The class is a blueprint that defines the nature of a future object. From classes we can construct instances. An instance is a specific object created from a particular class. For example, above we created the object lst which was an instance of a list object.                
                
By convention we give classes a name that starts with a capital letter. Note how x is now the reference to our new instance of a Sample class. In other words, we instantiate the Sample class. Inside of the class we currently just have pass. But we can define class attributes and methods. An attribute is a characteristic of an object. A method is an operation we can perform with the object.
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
# Create a new object type called Sample
class Sample:
    pass
# Instance of Sample
x = Sample()
print(type(x))

# instance of a Sample class
my_sample = Sample()
type(my_sample)
# __main__.Sample
~~~
##### +
* __init__ method is used to initialize the attributes of an object
~~~
___________________________________________________
class Dog():
    def __init__(self, breed):
        self.breed = breed
my_dog = Dog(breed='Lab')
my_dog.breed
# 'Lab'
~~~

##### +
* Each attribute in a class definition begins with a reference to the instance object. It is by convention named self. The breed is the argument. The value is passed during the class instantiation.
~~~
___________________________________________________
class Dog():
    def __init__(self, mybreed):
        self.my_attribute = mybreed
my_dog = Dog(mybreed='Huskie')
my_dog.my_attribute
# 'Huskie'

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

##### +
* In Python there are also class object attributes. These Class Object Attributes are the same for any instance of the class.
* Notice that attributes never had open and close parentheses. And that's because attributes aren't really something that you execute. Instead it's just something that's a characteristic of the object that you call back.
~~~
___________________________________________________
class Dog():
    # class object attribute same for any instance of a class
    species = 'mammal'
    
    def _init(self, breed, name, spots):
        self.breed = breed
        self.name = name
        self.spots = spots

my_dog = Dog(breed='Lab', name='Sammy', spots = True)
my_dog = Dog.species
# 'mammal'
~~~

##### +
* Methods are functions defined inside the body of a class. They are used to perform operations with the attributes of our objects. Methods are a key concept of the OOP paradigm. They are essential to dividing responsibilities in programming, especially in large applications.
* You can basically think of methods as functions acting on an Object that take the Object itself into account through its self argument.
~~~
___________________________________________________
class Dog():
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
~~~

##### +
* In the _init_ lower above, in order to calculate the area attribute, we had to call Circle.pi. This is because the object does not yet have its own .pi attribute, so we call the Class Object Attribute pi instead.
* In the setRadius method, however, we'll be working with an existing Circle object that does have its own pi attribute. Here we can use either Circle.pi or self.pi.
~~~
___________________________________________________
class Circle:
    pi = 3.14

    # Circle gets instantiated with a radius (default is 1)
    def __init__(self, radius=1):
        self.radius = radius 
        self.area = radius * radius * Circle.pi

    # Method for resetting Radius
    def setRadius(self, new_radius):
        self.radius = new_radius
        self.area = new_radius * new_radius * self.pi

    # Method for getting Circumference
    def getCircumference(self):
        return self.radius * self.pi * 2


c = Circle()

print('Radius is: ',c.radius)
print('Area is: ',c.area)
print('Circumference is: ',c.getCircumference())
~~~

## Inheritance and Polymorphism
Inheritance is a way to form new classes using classes that have already been defined. The newly formed classes are called derived classes, the classes that we derive from are called base classes. Important benefits of inheritance are code reuse and reduction of complexity of a program. The derived classes (descendants) override or extend the functionality of base classes (ancestors).        

### Inheritance
* An Inheritance is a way to form new classes using classes that have already been defined.
* Benefits from using an Inheritance are the ability to reuse code that you've already worked on and to reduce the complexity of a program.
* The main idea in INHERITANCE is that: all you need to do is inherit from your base class and now you have access to all those old methods.
* And if you ever want to overwrite them, you can just overwrite them. Recall the same method name and then do whatever you want there.
* And you can always add in more methods.
* SO that's how inheritance works.
##### +
* In this example, we have two classes: Animal and Dog. The Animal is the base class, the Dog is the derived class. 
* The derived class inherits the functionality of the base class. It is shown by the eat() method.
* The derived class modifies existing behavior of the base class. shown by the whoAmI() method.
* Finally, the derived class extends the functionality of the base class, by defining a new bark() method.
~~~
___________________________________________________
class Animal:
    def __init__(self):
        print("Animal created")
    def whoAmI(self):
        print("Animal")
    def eat(self):
        print("Eating")

class Dog(Animal):
    def __init__(self):
        Animal.__init__(self)
        print("Dog created")
    def whoAmI(self):
        print("Dog")
    def bark(self):
        print("Woof!")

d = Dog()
# Animal created
# Dog created
d.whoAmI()
# Dog
d.eat()
# Eating
d.bark()
# Woof!
~~~

### Polymorphism
We've learned that while functions can take in different arguments, methods belong to the objects they act on. In Python, polymorphism refers to the way in which different object classes can share the same method name, and those methods can be called from the same place even though a variety of different objects might be passed in.

* Here we have a Dog class and a Cat class, and each has a .speak() method. When called, each object's .speak() method returns a result unique to the object.
* There a few different ways to demonstrate polymorphism. First, with a for loop.
* Another is with functions.
* In both cases we were able to pass in different object types, and we obtained object-specific results from the same mechanism.
~~~
___________________________________________________
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

for pet in [mydog,mycat]:
    print(type(pet))
    print(pet.speak())
# <class '__main__.Dog'>
# Morris says Whoof!
# <class '__main__.Cat'>
# Cucumber says Meow!

def pet_speak(pet):
    print(pet.speak())
pet_speak(mydog)
# Morris says Whoof!
pet_speak(mycat)
# Cucumber says Meow!
~~~

* A more common practice is to use abstract classes and inheritance. An abstract class is one that never expects to be instantiated. For example, we will never have an Animal object, only Dog and Cat objects, although Dogs and Cats are derived from Animals.
~~~
___________________________________________________
class Animal():
    def __init__(self, name):  # Constructor of the class
        self.name = name
    def speak(self):
        raise NotImplementedError('Subclass must implenet this abstract method')
myanimal = Animal('fred')
myanimal.speak()
# NotImplementedError: Subclass must implement this abstract method.

class Dog(Animal):
    def speak(self):       # Abstract method, defined by convention only
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

## Special methods/ To use built-in Python libraries on a class
* Classes in Python can implement certain operations with special method names.
* __init__(), __str__(), __len__() and __del__() methods
* These special methods are defined by their use of underscores. They allow us to use Python specific functions on objects created through our class.
~~~
___________________________________________________
class Book():
    def __init__(self, title, author, pages):
        self.title = title
        self.author = author
        self.pages = pages
        
    def __str__(self):
        return f'{self.title} written by {self.author}'
    
    def __len__(self):
        return self.pages
## In order to basically specify extra things that may occur when you call delete
    def __del__(self):
        print('A book object has been deleted.')

b = Book(title='Python Rocks', author='Head First', pages=500)
print(b)
# Python Rocks by Head First
len(b)
# 500

## delete object
del b
# A book object has been deleted
## name 'b' is not defined

~~~

