## List Comprehensions
* List comprehension are a unique way of quickly creating a list with Python.
* If you find yourself using a for loop along with .append() to create a list, LC are a good alternative.
~~~
___________________________________________________
mystring = 'hello'
mylist=[]
for letter in mystring:
  mylist.append(letter)
  
___________________________________________________
mylist = [letter for letter in mystring]  # element for element in "object"
#['h', 'e', 'l', 'l', 'o']

___________________________________________________
mylist = [x for x in range(0,11)]
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

___________________________________________________
mylist = [num**2 for num in range(0,11,2)]
# [0, 4, 16, 36, 64, 100]

___________________________________________________
mylist = [x for x in range(0,11) if x%2==0]
[0, 2, 4, 6, 8, 10]

___________________________________________________
celcius = [0, 10 ,20 ,30 ,35]
fahrenheit = [((9/5)*temp+32) for temp in celcius]
# [32.0, 50.0, 68.0, 86.0, 95.0]

___________________________________________________
celcius=[0,10,15,20,25,30]
fahrenheit=[]
for temp in celcius:
    fahrenheit.append((9/5)*temp+32)
# [32.0, 50.0, 68.0, 86.0, 95.0]

___________________________________________________
mylist = [x if x%2==0 else 'ODD' for x in range(0,11)]
# [0, 'ODD', 2, 'ODD', 4, 'ODD', 6, 'ODD', 8, 'ODD', 10]
~~~

## Nested loops
~~~
___________________________________________________
mylist=[]
for x in [1,2,3]:
    for y in ['a','b','c']:
        mylist.append(x*y)
# ['a', 'b', 'c', 'aa', 'bb', 'cc', 'aaa', 'bbb', 'ccc']
    
___________________________________________________
mylist=[]
for x in ['a','b','c']:
    for y in [1,2,3]:
        mylist.append(x*y)
# ['a', 'aa', 'aaa', 'b', 'bb', 'bbb', 'c', 'cc', 'ccc']       

___________________________________________________
mylist = [x*y for x in [2,4,6] for y in [10,100,1000]]
# [20, 200, 2000, 40, 400, 4000, 60, 600, 6000]

___________________________________________________
mylist = [x*y for x in ['a','b','c'] for y in [1,2,3]]
# ['a', 'aa', 'aaa', 'b', 'bb', 'bbb', 'c', 'cc', 'ccc']
~~~

## Methods
* python documentation
* the PYTHON STANDARD LIBRARY DOCUMENTATION
~~~
___________________________________________________
# help function, description of method
help(mylist.insert)
~~~

## Functions
* Creating clean repeatable code is a key part of becoming an effective programmer.
* Functions allow us to create blocks of code that can be easily executed many times, without needing constantly rewrite the entire block od code.
* def - keyword
* paranthesis at the end. In order to take variables and use it in function.
* ''' docstring.
* Functions can accept arguments to be passed by the user.
* data type issues.
~~~
___________________________________________________
def my_function(name):
    print('Hello ' + name)
my_function('Almas')
# Hello Almas

___________________________________________________
# if name is not provided use default value
def say_hello(name='Default'):
  print(f'Hello {name}')
# Hello Default

___________________________________________________
# return
def add_num(a,b):
  return a+b
result = add_num(10,20)
# 30

___________________________________________________
def even_check(num):
    return num%2==0
# even_check(8) True
# even_check(5) False
___________________________________________________
def check_even_list(num_list):
    for num in num_list:
        if num%2==0:
            return True
        else:
            pass
    return False
    
___________________________________________________
# return only even numbers
def check_even_numbers(num_list):
    even_numbers=[]
    for num in num_list:
        if num%2==0:
            even_numbers.append(num)
        else:
            pass
    return even_numbers

___________________________________________________
def even_numbers(mylist):
    return [item if item%2==0 else 'ODD' for item in mylist]
# even_numbers([1,5,3,9,5,5])  ['ODD', 'ODD', 'ODD', 'ODD', 'ODD', 'ODD']

def even_numbers(mylist):
    return [item for item in mylist if item%2==0]
# even_numbers([1,5,3,8,5,5])  [8]

~~~

### tuple unpacking in functions
~~~
___________________________________________________
car_prices = [('Hyundai',19500),('Kia',18000),('Pajero',25000)]
def car_decision(car_prices):
    car_maxprice = 0
    car_name = ''
    for cur_car_name, cur_car_price in car_prices:
        if car_maxprice < cur_car_price:
            car_maxprice = cur_car_price
            car_name = cur_car_name
    return(car_name, car_maxprice)
~~~

## ARGS and KWARGS
~~~
*args - arguments
*kwargs - keyword arguments
~~~
* args
* by default python will take all the parameters that are passed in and set them to be inside a tuple.
* args - returns back a tuple.
~~~
___________________________________________________
def myfunc(a,b,c=0,d=0,e=0):
    return sum((a,b)) * 0.05
# myfunc() takes from 2 to 5 positional arguments.

___________________________________________________
def myfunc(*args):
    print(args)
    return sum(args) * 0.05
# as many arguments as I want
myfunc(10,20,70,80,100)
# (10, 20, 70, 80, 100)
# 14.0
~~~

* kwargs
* builds a dictionary of key value pairs.
* kwargs - return back a dictionary.
~~~
___________________________________________________
def myfunc(**kwargs):
    print(kwargs)
    if 'fruits' in kwargs:
        print(f'My fruit of choice is {kwargs["fruits"]}')
    else:
        print(f'I did not find any fruit here. I found {kwargs["chocolate"]}')

myfunc(fruits='orange', chocolate='snickers')
# {'fruits': 'orange', 'chocolate': 'snickers'}
# My fruit of choice is orange.

myfunc(fruits111='orange', chocolate='snickers')
# I did not find any fruit here. I found snickers.
~~~

~~~
___________________________________________________
def myfunc(*args, **kwargs):
    print(args)
    print(kwargs)
    print(f'I would like {args[0]} {kwargs["food"]}')
myfunc(10,20,30,40,  fruit='apple', lady='sex', food='sushi')
(10, 20, 30, 40)
{'fruit': 'apple', 'lady': 'sex', 'food': 'sushi'}
I would like 10 sushi
~~~

~~~
___________________________________________________
def myfunc(*args):
    even_nums=[]
    for num in args:
        if num%2==0:
            even_nums.append(num)
    return even_nums
~~~

## MAP, FILTER, LAMBDA functions
### MAP
~~~
___________________________________________________
def square(nums):
    return nums**2
nums = [1,2,3,4,5]
for item in map(square, nums):
    print(item)
list(map(square, nums))
# [1, 4, 9, 16, 25]
___________________________________________________
def splicer(string):
    if len(string)%2==0:
        return 'EVEN'
    else:
        return string[0]
string = ['Almas', 'Tolkyn', 'Mirana', 'Aslan', 'Tomiris']
list(map(splicer, string))
# ['A', 'EVEN', 'EVEN', 'A', 'T']
~~~
### FILTER
~~~
___________________________________________________
def check_even(nums):
    return nums%2==0
nums = [1,2,3,4,5,6,7,8]
list(filter(check_even, nums))
# [2, 4, 6, 8]
~~~

### LAMBDA
~~~
___________________________________________________
def square(num):
    return num**2
# -->
def square(num): return num**2
# -->
square = lambda num: num**2
square(5)
# 25

___________________________________________________
# where to use lambda
nums = [1,2,3,4,5,6,7,8]
list(map(lambda num: num**2, nums))
# [1, 4, 9, 16, 25, 36, 49, 64]

list(filter(lambda num: num%2==0, nums))
# [2, 4, 6, 8]
~~~

## Nested Statements and Scope
#### LEGB rule format.
So LEGB stands for Local, Enclosing function locals, Global and Built-in.
* 1 Local
* 2 Enclosing
* 3 Global
~~~
___________________________________________________
# GLOBAL
name = 'THIS IS GLOBAL VARIABLE'

def greet():
    #ENCLOSING
    name = 'Almas'
    
    def hello():
        #LOCAL
        name = 'Local variable'
        print('Hello' + name)
    hello()
greet()
~~~

~~~
___________________________________________________
x = 50
def func(x):
    print(f'x is = {x}')
    #  LOCAL
    x = 200
    print(f'Locally Reassignment of {x}')

func(x)
# x is = 50
# Locally Reassignment of 200

print(x)
# 50
~~~

~~~
___________________________________________________
# If you want to be x global from inside a function
x = 50
def func():
    global x
    print(f'x is = {x}')
    #  LOCAL
    x = 200
    print(f'Locally Reassignment of {x}')
# 200
~~~

~~~
___________________________________________________
# if you still want to affect to global variable
x = 50
def func(x):
    print(f'x is = {x}')
    #  LOCAL
    x = 200
    print(f'Locally Reassignment of {x}')
    return x
x = func(x)
~~~
