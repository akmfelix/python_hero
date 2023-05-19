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

# Python
* Python uses dynamic typing, meaning you can reassign variables to different data types. This makes Python very flexible in assigning data types; it differs from other languages that are statically typed.
* Variable assignment follows name = object, where a single equals sign = is an assignment operator

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

## String
* Strings in Python are actually a sequence, which basically means Python keeps track of every element in the string as a sequence.
* index. string[5]
* slice. string[start:stop:step]. string[::-1] reverse
* len() function
* immutable. name='Almas' name[0]='R' - not correct
* concatenation. last_letter= name[-1] name+last_letter -> Almass; letter='z' letter*3 -> zzz
* methods. x.upper(); x.lower(); x.split() x.split('i')
* .format(); 'String here {} then also {}'.format('smth1 or var','smth2'); print('The {2} {1} {0}'.format('fox','brown','quick')); print('The {q} {b} {f}'.format(f='fox',b='brown',q='quick')); x='The {1} {2} {0}'.format(f,q,b)
* float formatting; {value:width.precision f}; print('the result was {r:1.2f}'.format(r=reuslt))
* f format string; name='Jose' print(f'Hello, his name is {name}')
~~~
print('The {q} {b} {f}'.format(f='fox',b='brown',q='quick'))

# f format string
name='Almas' 
print(f'Hello, Mr.{name}')
~~~

## Lists
* Lists are constructed with brackets [] and commas separating every element in the list.
* Lists can actually hold different object types
* Indexing and Slicing
* We can also use + to concatenate lists, just like we did for strings. Note: This doesn't actually change the original list.
* We can also use the * for a duplication method similar to strings
* Use the append method to permanently add an item to the end of a list
* Use pop to "pop off" an item from the list. By default pop takes off the last index, but you can also specify which index to pop off
* We can use the sort method and the reverse methods to also effect your lists
* Nesting Lists
* List Comprehensions; first_col = [row[0] for row in matrix] [1, 4, 7]
* .split()

## Dictionaries
* Mappings are a collection of objects that are stored by a key, unlike a sequence that stored objects by their relative position. This is an important distinction, since mappings won't retain order since they have objects defined by a key. A Python dictionary consists of a key and then an associated value. That value can be almost any Python object.
~~~
mydict = {'k1':1,'k2':2,'k3':3}
mydict['key2']  # call values by their key
my_dict['key1'] = my_dict['key1'] - 123

# nested dict
d = {'key1':{'nestkey':{'subnestkey':'value'}}}
d['key1']['nestkey']['subnestkey']

# add key, values to dict
d = {} 
d['animal'] = 'Dog' 
d['answer'] = 42

# dict methods
d.keys()
d.values()
d.items()
~~~

## Tuples
* In Python tuples are very similar to lists, however, unlike lists they are immutable meaning they can not be changed. You would use tuples to present things that shouldn't be changed, such as days of the week, or dates on a calendar.
* t.index('one') .index to enter a value and return the index
* t.count('one') .count to count the number of times a value appears

## Sets
* Sets are an unordered collection of unique elements. We can construct them by using the set() function
* x.add(1) We add to sets with the add() method
* Note the curly brackets. This does not indicate a dictionary! Although you can draw analogies as a set being a dictionary with only keys
~~~
list1 = [1,1,2,2,3,4,5,6,1,1]
set(list1)
~~~


## I/O with Basic files in python FILES
* %%writefile test_file.txt can create files in jupyter notebook
~~~
myfile = open('test.txt')
myfile.seek(0)
myfile.read()
myfile.readlines()
myfile.close()
~~~

* mode='r' is read only
* mode='w' is write only (will overwrite files or create new)
* mode='a' is append only (will add onto files)
* mode='r+' is reading and writing
* mode='w+' is writing and reading (will overwrite files or create new)
~~~
with open('test.txt') as my_variable_name:
  contents = my_variable_name.read()
contents  
~~~

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
with open('abc', mode='w') as f:
  f.write('I earn $4000 every month')
  
with open('abc', mode='r') as f:
  print(f.read())
~~~

~~~
x = open('myfile.txt', 'w')
x.write('This is my file')
x.close()
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
~~~

## for loops
* Many objects in Python are iterable, meaning we can iterate over every element in the object
~~~
my_iterable=[1,2,3]
for item_name in my_iterable:
  print(item_name)
  
# tuple unpacking
# duplicate structure of items
mylist = [(1,2),(3,4),(5,6)]  
for (a,b) in mylist:
  print(a)
  print(b)
  
for a,b in mylist:
  print(a)
  print(b)  
  
d = {'k1':1,'k2':2,'k3':3}
for key,value in d.items():
  print(key, value)
~~~

## while loops
* while loops will to continue execute a block of code while some conditions remains True
* break: breaks out of the current closest enclosing loop
* continue: goes to the top of the closest enclosing loop
* pass: does nothing at all

~~~
x=0
while x<5:
  if x==2:
    break
  print(x)
  x+=1

x=0
while x<10:
    print('x is equal to: {}'.format(x))
    x+=1
    if x==4:
        continue

x=[1,2,3]
for item in x:
  pass

mystring='Almas'
for letter in mystring:
  if letter == 'a':
    continue
  print(letter)
  
for letter in mystring:
  if letter == 'a':
    break
  print(letter)  
~~~

## useful operators

~~~
for num in range(0,11,2):
  print(num)
  
list(range(0,11,2))  
~~~

#### enumerate
* can take any iterable object
~~~
counter=0
for letter in 'abcde':
    print(f'at index position {counter} the letter is {letter}')
    counter+=1
at index position 0 the letter is a
at index position 1 the letter is b
at index position 2 the letter is c
at index position 3 the letter is d
at index position 4 the letter is e    

counter=0
word='abcde'
for letter in word:
  print(word[counter])
  counter += 1
a
b
c
d
e  
  
for item in enumerate(word):
  print(item)
(0,'a')  
(1,'b')
~~~

#### zip function
* zips together two function
* will zip only the shortest list
~~~
mylist1 = [1,2,3]
mylist2 = ['a','b','c']
for item in zip(mylist1,mylist2):
  print(item)
  
list(zip(mylist1,mylist2))
~~~  
# (1,'a')  
# (2,'b')
# (3,'c')

#### in, max, min, random
~~~
x in [1,3,'a','b','x']
'mykey' in {'mykey':1}

# Quickly check the minimum or maximum of a list with these functions
max(mylist)
min(mylist)

from random import shuffle
mylist=[1,2,3,4,5,6,7,8,9,10]
shuffle(mylist)

# random integer
from random import randint
randint(0,100)
~~~

#### input
~~~
result = input('what is your age?')
int(result)
~~~


## List comprehension
~~~
mystring = 'hello'
mylist=[]
for letter in mystring:
  mylist.append(letter)
  
mylist = [letter for letter in mystring]  # element for elemen in ...
mylist = [num**2 for num in range(0,10,2)]
mylist = [x for x in range(0,11) if x%2==0] # [0,2,4,6,8]
result = [x if x%2==0 else 'odd' for x in range(0,11)]

celcius = [10,20,30,32.4]
fahrenheit = [((9/5)*temp+32) for temp in celcius]

celcius=[0,10,15,20,25,30]
fahrenheit=[]
for temp in celcius:
    fahrenheit.append((9/5)*temp+32)
~~~

#### nested loop
~~~
mylist=[]
for x in [1,2,3]:
    for y in ['a','b','c']:
        mylist.append(x*y)
['a', 'b', 'c', 'aa', 'bb', 'cc', 'aaa', 'bbb', 'ccc']
    
mylist=[]
for x in ['a','b','c']:
    for y in [1,2,3]:
        mylist.append(x*y)
['a', 'aa', 'aaa', 'b', 'bb', 'bbb', 'c', 'cc', 'ccc']       

mylist = [x*y for x in [2,4,6] for y in [10,100,1000]]
[20, 200, 2000, 40, 400, 4000, 60, 600, 6000]

mylist = [x*y for x in ['a','b','c'] for y in [1,2,3]]
['a', 'aa', 'aaa', 'b', 'bb', 'bbb', 'c', 'cc', 'ccc']
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



