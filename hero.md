~~~
More Mathematical (and Harder) Practice:
https://projecteuler.net/archives

List of Practice Problems:
http://www.codeabbey.com/index/task_list

A SubReddit Devoted to Daily Practice Problems:
https://www.reddit.com/r/dailyprogrammer

A very tricky website with very few hints and touch problems (Not for beginners but still interesting)
http://www.pythonchallenge.com/
~~~

https://realpython.com/python-not-operator/
##### How do I know what directory my Notebooks are being saved?
To find out where your notebooks are type: pwd in a cell and run it with Shift+Enter. This will print your working directory.

##### How can I change where the Notebooks are being saved?
You will need to change the directory in which you are starting you jupyter notebook. Use cd in the terminal or command prompt to change to your desired directory if you are running jupyter notebook at your command line.

##### Our chat channel to talk to other students
https://discord.gg/TztE6B8
  
##### Video guide on how to use the chat room
https://www.youtube.com/watch?v=bkH89OJ001M 

##### I don't control certification, Udemy does, information on this can be found here
https://support.udemy.com/hc/en-us/articles/229603868-Certificate-of-Completion

##### Course Slides can be found here:
https://drive.google.com/drive/folders/1CKqOQzst1cGURXGiRVivi2Xsc0n-X8CR?usp=sharing


## Jupyter
* (base) PS C:\Users\00031730> jupyter server --generate-config
Writing default config to: C:\Users\00031730\.jupyter\jupyter_server_config.py
c.NotebookApp.browser = 'C:/Program Files/Google/Chrome/Application/chrome.exe %s'
* jupyter notebook
* pwd working directory


### CMD prompts in Windows
* cd: show current directory
* dir:  contents of my directory
* cd Desktop: change current directory
* cd .. : to go up in directory
* cls: clear all typed codes
* python myexample.py

### terminal prompts in Linux
* open terminal (command line interface)
* pwd: current directory
* ls: list all files in current directory
* cd Desktop: change current directory
* clear: clear screen
* cd .. : go up in directory

#### git+immersion
* create repository
* create a branch
* open a pull request
* some test

# Tips
~~~
b = None
~~~

## Python is dynamic language
* Python uses dynamic typing, meaning you can reassign variables to different data types. This makes Python very flexible in assigning data types; it differs from other languages that are statically typed.
~~~
my_dogs = 2
my_dogs = ['Sammy', 'Frankie']
type(my_dogs)
# list
~~~

## Data structures
* int. Integers
* float. Floating points
* str. Strings
* list. Lists ordered sequence of objects ['10', 'hello', '10.5']
* dict. Dictionaries. Unordered key:value pairs {'mykey':'value'}
* tup. Tuples. Ordered immutable sequence of objects ('10', 'hello', '10.5')
* set. Sets. Unordered collection of unique objects {'10', 'b'}
* bool. Booleans. True or False

## Numbers
* //; floor division. The // operator (two forward slashes) truncates the decimal without rounding, and returns an integer result.
* %; The % operator returns the remainder after division.

One illusion may beget another. For example, since 0.1 is not exactly 1/10, summing three values of 0.1 may not yield exactly 0.3, either:          
`.1 + .1 + .1 == .3`     
`False`

Since the 0.1 cannot get any closer to the exact value of 1/10 and 0.3 cannot get any closer to the exact value of 3/10, then pre-rounding with round() function cannot help:             
`round(.1, 1) + round(.1, 1) + round(.1, 1) == round(.3, 1)`
`False`           

Though the numbers cannot be made closer to their intended exact values, the round() function can be useful for post-rounding so that results with inexact values become comparable to one another:           
`round(.1 + .1 + .1, 10) == round(.3, 10)`
`True`
~~~
my_income_usd = 5000
rate = 480
my_income_kzt = my_income_usd * rate
tax_rate = 0.185
my_taxes = my_income_kzt * tax_rate
my_pureincome_kzt = my_income_kzt - my_taxes
# 1956000.0
~~~
## String
* Strings in Python are actually a sequence, which basically means Python keeps track of every element in the string as a sequence.
* \n - new line; \t - tab in print function
* len() function
* immutable. name='Almas' name[0]='R' - not correct
* object.method(parameters)
* methods. x.upper(); x.lower(); x.split() x.split('i') - a list of a string; methods does not affect original string.
~~~
mystring = 'abcdefghk'
mystring[::-1]
# khgfedcba
mystring[3:6]
# cdef
mystring[-1]
# k
~~~

~~~
name = 'Sam'
last_letters = name[1:]
'P' + last_letters
# Pam

letter = 'a'
letter*3
# aaa

x = 'Hi this is a string'
x.split('i')
# ['H', ' th', 's ', 's a str', 'ng']
~~~

~~~
print('This is a string {}'.format('INSERTED'))
# This is a string INSERTED

print('The {} {} {}'.format('fox','brown','quick'))
# The fox brown quick

print('The {2} {1} {0}'.format('fox','brown','quick'))
# The quick brown fox

print('The {q} {b} {f}'.format(f='fox',b='brown',q='quick'))
# The quick brown fox

# f fprmat string
name='Almas' 
print(f'Hello, Mr.{name}')

# float formatting;
# {value:width.precision f}
result = 100/777
print(f'The result was {result:10.4f}')
# The result was     0.1287
~~~

## Lists
* Get object by INDEXING;
* Lists are ordered sequences that can hold a variety of object types.
* Lists are constructed with brackets [] and commas separating every element in the list.
* Lists can actually hold different object types.
* Lists are MUTABLE.
* Indexing and Slicing.
* +; We can also use + to concatenate lists, just like we did for strings. Note: This doesn't actually change the original list.
* *; We can also use the * for a duplication method similar to strings.
* len(mylist) - length of the list.
* .append(var) - add an item to the list.
* .pop(index) . By default pop takes off the last index, but you can also specify which index to pop off.
* .sort() - it does not return anything;
* .reverse() - it does not return anything;
* Nesting Lists;
* List Comprehensions; first_col = [row[0] for row in matrix] [1, 4, 7];
* .split();

## Dictionaries
* Get object by KEY;
* STRING key;
* Dictionaries are MUTABLE;
* Dictionaries are unordered mappings for storing objects;
* Key-Value pairs;
* {'key1':'value1', 'key2':'value2'};
* Objects are retrieved by key name;
* d.keys() - to see all keys;
* d.values() - all values;
* d.items() - all pairs;
~~~
mydict = {'k1':1,'k2':2,'k3':3}
# call values by their key
mydict['key2']
# 2
my_dict['key1'] = my_dict['key1'] - 123

# nested dict
d = {'key1':{'nestkey':{'subnestkey':'value'}}}
d['key1']['nestkey']['subnestkey']

# add key, values to dict
d = {} 
d['animal'] = 'Dog' 
d['answer'] = 42
~~~

## Tuples
* Tuples are immutable;
* In Python tuples are very similar to lists, however, unlike lists they are immutable meaning they can not be changed.
* (1,2,3)
* You would use tuples to present things that shouldn't be changed, such as days of the week, or dates on a calendar.
* t.index('one') .index to enter a value and return the index
* t.count('one') .count to count the number of times a value appears

## Sets
* Sets are an unordered collection of unique elements. We can construct them by using the set() function
* myset = set(); {}
* x.add(1) We add to sets with the add() method
* Note the curly brackets. This does not indicate a dictionary! Although you can draw analogies as a set being a dictionary with only keys
~~~
list1 = [1,1,2,2,3,4,5,6,1,1]
set(list1)
# {1,2,3}
~~~


## I/O with Basic files in python FILES
* %%writefile test_file.txt can create files in jupyter notebook
~~~
pwd
# to show current directory in jupyter notebook

# open file in a specific location
myfile = open('C:\\Users\\00031730\\Desktop\\Python\\_Jupyter\\Complete-Python-3-Bootcamp-master\\00_own\\file_name.txt')

%%writefile file_name.txt
This is a first line
This is a second line
This is a third line
# created a file with a name file_name.txt
# and having 3 lines

myfile = open('file_name.txt') # to open file
myfile.read()
# show text from file
#'This is a first line\nThis is a second line\nThis is a third line\n'
# if again run myfile.read() code it will show ''. Because after reading goes to the end of file. You will need to reset cursor.
myfile.seek(0)
# reset a cursor
myfile.readlines()
# ['This is a first line\n', 'This is a second line\n', 'This is a third line\n']
myfile.close()
# close text file
~~~

~~~
with open('file_name.txt') as new_file_name:
    contents = new_file_name.read()
# 'This is a first line\nThis is a second line\nThis is a third line\n' 
~~~

* mode='r' is read only
* mode='w' is write only (will overwrite files or create new)
* mode='a' is append only (will add onto files)
* mode='r+' is reading and writing
* mode='w+' is writing and reading (will overwrite files or create new)
~~~
%%writefile test.txt
Hello, this is a quick test file.
my_file = open('test.txt')

with open('test_file.txt', mode='r') as f:
  print(f.read())
  
with open('test_file.txt', mode='a') as f:
    f.write('\nfour on fourth')
~~~

~~~
x = open('myfile.txt', 'w')
x.write('This is my file')
x.close()
~~~

~~~
with open('abc.txt', mode='w') as f:
  f.write('I earn $4000 every month')
  
with open('abc.txt', mode='r') as f:
  print(f.read())
# 'I earn $4000 every month'
~~~


## if elif else
* Python’s not operator allows you to invert the truth value of Boolean expressions and objects.
~~~
if some_cond:
  some_code
elif some_cond:
  some_code
else:
  some_code

hungry = True / False    # boolean value
if hungry:
    print('Feed me')
else:
    print("I'm not hungry")
# Feed me
# I'm not hungry
~~~

## Loops. for loops
* Many objects in Python are iterable, meaning we can iterate over every element in the object
~~~
my_iterable=[1,2,3]
for item_name in my_iterable:
  print(item_name)

====================================================
for num in mylist:
    if num%2==0:
        print(num)
    else:
        print(f'Odd number: {num}')
  
====================================================
# tuple unpacking
# duplicate structure of items
mylist = [(1,2),(3,4),(5,6)]  
for (a,b) in mylist:
  print(a)
  print(b)
# 1
# 2
# 3
# 4
# 5
# 6  
  
====================================================
d = {'k1':1,'k2':2,'k3':3}
for key,value in d.items():
  print(key, value)
# k1 1
# k2 2
# k3 3
~~~

## Loops. while loops
* while loops will to continue execute a block of code while some conditions remains True
~~~
while some_boolean_condition:
  # do_something
else:
  # do something different

====================================================
x = 50
while x < 5:
    print(f'x is {x}')
    x += 1
else:
    print('x is greater than 5')
~~~
  
### Loops. break; pass; continue;
* break: breaks out of the current closest enclosing loop
* continue: goes to the top of the closest enclosing loop
* pass: does nothing at all

~~~
x = [1,2,3]
for i in x:
    pass
# do nothing, just pass piece of code

====================================================
mystring = 'Almas'
for letter in mystring:
    if letter == 'm':
        continue
    print(f'The current letter is {letter}')
# The current letter is A
# The current letter is l
# The current letter is a
# The current letter is s

====================================================
mystring = 'Almas'
for letter in mystring:
    if letter == 'm':
        break
    print(f'{letter}')
# A
# l

====================================================
x = 0
while x < 5:
    if x == 2:
        break
    print(x)
    x += 1
~~~

## Useful Operators
* range  - generator function, range(start, stop, step).
* list(range(2,8,2)) - to create a list from list
* enumerate - cant take an iterable object.
* zip - zip together two lists.
* in - operator
### range
~~~
for num in range(2,9,2):
    print(num)
# 2
# 4
# 6
# 8
~~~

### list
~~~
list(range(0,9,2))
# [0, 2, 4, 6, 8]
~~~

### enumerate
~~~
index_count = 0
for letter in 'abc':
    print(f'At index count {index_count} the letter is {letter}')
    index_count += 1
# At index count 0 the letter is a
# At index count 1 the letter is b
# At index count 2 the letter is c

___________________________________________________
index_count = 0
word = 'abc'
for letter in word:
    print(f'{word[index_count]}')
    index_count += 1
# a
# b
# c

___________________________________________________
word = 'abc'
for item in enumerate(word):
    print(item)
# (0, 'a')
# (1, 'b')
# (2, 'c')
~~~

### zip
~~~
list(zip(mylist1, mylist2))
# [(1, 'a'), (2, 'b'), (3, 'c')]
~~~

### in 
~~~
___________________________________________________
'x' in ['a','b','x','x']
# True

___________________________________________________
'Almas' in 'Almas is wealthy!'
# True

___________________________________________________
'k1' in {'k1':123, 'k2':['abc']}
# True

___________________________________________________
d = {'k1':345}
345 in d.values()
# True

___________________________________________________
d = {'k1':3456}
3456 in d.items()
# False
~~~

### in, max, min, random
* max - python standard function
* min - python standard function
~~~
mylist = [10,20,30,40,50]
min(mylist)
# 10

___________________________________________________
mylist = [10,20,30,40,50]
max(mylist)
# 50
~~~

### random library
* shuffle() - does not return anything, its inplace operator.
* randint(lower_range, upper_range) - quickly grab random integer. can save it
~~~
from random import shuffle
mylist = [1,2,3,4,5,6,7,8,9,10]
shuffle(mylist)
# [9, 7, 6, 3, 5, 1, 10, 4, 2, 8]

___________________________________________________
from random import randint
ri = randint(0,100)
ri
# 11
~~~

### input
* Remember! input - always get an input as string.
~~~
result = input('what is your age?')
int(result)
~~~


## List Comprehensions
* List comprehension are a unique way of quickly creating a list with Python.
* If you find yourself using a for loop along with .append() to create a list, LC are a good alternative.
~~~
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

#### Methods
* python documentation
~~~
# help function, description of method
help(mylist.insert)
~~~

## Functions
* Creating clean repeatable code is a key part of becoming an effective programmer
* Functions allow us to create blocks of code that can be easily executed many times, without needing constantly rewrite the entire block od code
~~~
def name_of_function(name):
  print(Hello + ' ' +'Mr.'name)
name_of_function('Almas')  

# if name is not provided use default value
def say_hello(name='Default'):
  print(f'Hello {name}')

# return
def add_num(a,b):
  return a+b
result = add_num(10,20)  

def check_even_list(num_list):
    for num in num_list:
        if num%2==0:
            return True
        else:
            pass
    return False
    
# return only even numbers
def check_even_numbers(num_list):
    even_numbers=[]
    for num in num_list:
        if num%2==0:
            even_numbers.append(num)
        else:
            pass
    return even_numbers
~~~

### tuple unpacking in functions
~~~
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

### multiple functions
~~~
from random import shuffle
mylist = ['','O','']

def shuffle_list(mylist):
    shuffle(mylist)
    return mylist

def player_guess():
    user_guess=''
    while user_guess not in ['0','1','2']:
        user_guess = input('Choose 0, 1 or 2: ')
    return int(user_guess)

def check_guess(mylist, user_guess):
    if mylist[user_guess] == 'O':
        print('correct')
    else:
        print('wrong')
    print(mylist)

mixedup_list = shuffle_list(mylist)
guess = player_guess()
check_guess(mixedup_list, guess)
~~~

#### shuffle game
~~~
from random import shuffle

mylist = ['','O','']

def shuffle_list(mylist):
    shuffle(mylist)
    return mylist

def player_guess():
    user_guess=''
    while user_guess not in ['0','1','2']:
        user_guess = input('Choose 0, 1 or 2: ')
    return int(user_guess)

def check_guess(mylist):
    while True:
        guess = player_guess()
        if mylist[guess] == 'O':
            print('correct')
            break
        else:
            print('wrong')
    print(mylist)
mixedlist = shuffle_list(mylist)
check_guess(mixedlist)
~~~

# ARGS and KWARGS
~~~
*args - arguments
*kwargs - keyword arguments
~~~
* args
* by default python will take all the parameters that are passed in and set them to be inside a tuple.
* returns back tuple
~~~
def myfunc(a,b,c=0,d=0,e=0):
    return sum((a,b)) * 0.05

def myfunc(*args):
    return sum(args) * 0.05
    
def myfunc(*args):
    return print(args)
# myfunc(1,2,3,4,5)    
# (1, 2, 3, 4, 5)
~~~

* kwargs
* builds a dictionary of key value pairs
~~~
def myfunc(**kwargs):
    if 'fruits' in kwargs:
        print(f'My fruit of choice is {kwargs["fruits"]}')
    else:
        print(f'I did not find any fruit here. I found {kwargs["chocolate"]}')
~~~

~~~
def myfunc(*args, **kwargs):
    print(args)
    print(kwargs)
    print(f'I would like {args[0]} {kwargs["food"]}')
myfunc(10,20,30,40,fruit='apple', lady='sex', food='sushi')
(10, 20, 30, 40)
{'fruit': 'apple', 'lady': 'sex', 'food': 'sushi'}
I would like 10 sushi
~~~

~~~
def myfunc(*args):
    even_nums=[]
    for num in args:
        if num%2==0:
            even_nums.append(num)
    return even_nums
~~~



