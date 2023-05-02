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




