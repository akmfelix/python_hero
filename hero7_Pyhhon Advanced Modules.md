# Collections Module
The collections module is a built-in module that implements specialized container data types providing alternatives to Python’s general purpose built-in containers. We've already gone over the basics: dict, list, set, and tuple.
## Counter
Counter is a dict subclass which helps count hashable objects. Inside of it elements are stored as dictionary keys and the counts of the objects are stored as the value.
~~~
from collections import Counter
lst = [1,2,2,2,2,3,3,3,1,2,1,12,3,2,32,1,21,1,223,1]
Counter(lst)
# Counter({1: 6, 2: 6, 3: 4, 12: 1, 21: 1, 32: 1, 223: 1})

Counter('aabsbsbsbhshhbbsbs')
# Counter({'a': 2, 'b': 7, 'h': 3, 's': 6})

c = Counter('hellloo')
c.most_common()
# [('l', 3), ('o', 2), ('h', 1), ('e', 1)]
c.most_common(2)
# [('l', 3), ('o', 2)]
~~~

Common patterns when using the Counter() object
~~~
sum(c.values())                 # total of all counts
c.clear()                       # reset all counts
list(c)                         # list unique elements
set(c)                          # convert to a set
dict(c)                         # convert to a regular dictionary
c.items()                       # convert to a list of (elem, cnt) pairs
Counter(dict(list_of_pairs))    # convert from a list of (elem, cnt) pairs
c.most_common()[:-n-1:-1]       # n least common elements
c += Counter()                  # remove zero and negative counts
~~~

## defaultdict
defaultdict is a dictionary-like object which provides all methods provided by a dictionary but takes a first argument (default_factory) as a default data type for the dictionary. Using defaultdict is faster than doing the same using dict.set_default method.\
A defaultdict will never raise a KeyError. Any key that does not exist gets the value returned by the default factory.
~~~
from collections import defaultdict
d = {}
d['one']
# KeyError: 'one'

d  = defaultdict(object)
d['one']
# <object at 0x216de27bcf0>

for item in d:
    print(item)
# one

## Can also initialize with default values:
d = defaultdict(lambda: 0)
d['one']
# 0
~~~

## namedtuple
The standard tuple uses numerical indexes to access its members.\
\
For simple use cases, this is usually enough. On the other hand, remembering which index should be used for each value can lead to errors, especially if the tuple has a lot of fields and is constructed far from where it is used. A namedtuple assigns names, as well as the numerical index, to each member.\
\
Each kind of namedtuple is represented by its own class, created by using the namedtuple() factory function. The arguments are the name of the new class and a string containing the names of the elements.\
You can basically think of namedtuples as a very quick way of creating a new object/class type with some attribute fields.
~~~
t = (12,13,14)
t[0]
# 12

from collections import namedtuple
Dog = namedtuple('Dog',['age','breed','name'])
sam = Dog(age=2,breed='Lab',name='Sammy')
frank = Dog(age=2,breed='Shepard',name="Frankie")

## We construct the namedtuple by first passing the object type name
## (Dog) and then passing a string with the variety of fields as a
## string with spaces between the field names. We can then call on
## the various attributes

sam
# Dog(age=2, breed='Lab', name='Sammy')
sam.age
# 2
sam[0]
# 2
~~~

# Opening and Reading files and folders
# OS and shutil - module
### Create practice file
We will begin by creating a practice text file that we will be using for demonstration.
~~~
f = open('practice.txt','w+')
f.write('test')
f.close()
~~~

### Getting directories
Python has a built-in os module that allows us to use operating system dependent functionality.
~~~
## to get current directory
import os
os.getcwd()
# 'C:\\Users\\Marcial\\Pierian-Data-Courses\\Complete-Python-3-Bootcamp\\12-Advanced Python Modules'
~~~

### Listing Files in a directory
~~~
os.listdir()
['.ipynb_checkpoints',
 '00-Collections-Module.ipynb',
 '01-Datetime-Module.ipynb',
 '01-Opening-and-Reading-Files.ipynb',
 '02-Math-and-Random-Module.ipynb',...]

## In any directory you pass
os.listdir("C:\\Users")
~~~

### Moving Files
You can use the built-in shutil module to to move files to different locations. Keep in mind, there are permission restrictions, for example if you are logged in a User A, you won't be able to make changes to the top level Users folder without the proper permissions.
~~~
import shutil
shutil.move('practice.txt','C:\\Users\\Marcial')
# 'C:\\Users\\Marcial\\practice.txt'

shutil.move('C:\\Users\\Marcial\practice.txt',os.getcwd())
~~~

### Deleting Files
NOTE: The os module provides 3 methods for deleting files:
* os.unlink(path) which deletes a file at the path your provide
* os.rmdir(path) which deletes a folder (folder must be empty) at the path your provide
* shutil.rmtree(path) this is the most dangerous, as it will remove all files and folders contained in the path. All of these methods can not be reversed! Which means if you make a mistake you won't be able to recover the file. Instead we will use the send2trash module. A safer alternative that sends deleted files to the trash bin instead of permanent removal.

~~~
import send2trash
~~~

### Walking through a directory
Often you will just need to "walk" through a directory, that is visit every file or folder and check to see if a file is in the directory, and then perhaps do something with that file. Usually recursively walking through every file and folder in a directory would be quite tricky to program, but luckily the os module has a direct method call for this called os.walk(). Let's explore how it works.
~~~
os.getcwd()
for folder , sub_folders , files in os.walk("Example_Top_Level"):
    
    print("Currently looking at folder: "+ folder)
    print('\n')
    print("THE SUBFOLDERS ARE: ")
    for sub_fold in sub_folders:
        print("\t Subfolder: "+sub_fold )
    
    print('\n')
    
    print("THE FILES ARE: ")
    for f in files:
        print("\t File: "+f)
    print('\n')
    
    # Now look at subfolders
~~~

# datetime - module
Python has the datetime module to help deal with timestamps in your code. Time values are represented with the time class. Times have attributes for hour, minute, second, and microsecond. They can also include time zone information. The arguments to initialize a time instance are optional, but the default of 0 is unlikely to be what you want.

### time
Let's take a look at how we can extract time information from the datetime module. We can create a timestamp by specifying datetime.time(hour,minute,second,microsecond)
~~~
import datetime
t = datetime.time(4, 20, 1)
## Let's show the different components
print(t)
print('hour  :', t.hour)
print('minute:', t.minute)
print('second:', t.second)
print('microsecond:', t.microsecond)
print('tzinfo:', t.tzinfo)
# 04:20:01
# hour  : 4
# minute: 20
# second: 1
# microsecond: 0
# tzinfo: None
~~~

We can also check the min and max values a time of day can have in the module\
The min and max class attributes reflect the valid range of times in a single day.
~~~
print('Earliest  :', datetime.time.min)
print('Latest    :', datetime.time.max)
print('Resolution:', datetime.time.resolution)
# Earliest  : 00:00:00
# Latest    : 23:59:59.999999
# Resolution: 0:00:00.000001
~~~

### dates
datetime (as you might suspect) also allows us to work with date timestamps. Calendar date values are represented with the date class. Instances have attributes for year, month, and day. It is easy to create a date representing today’s date using the today() class method.
~~~
today = datetime.date.today()
print(today)
print('ctime:', today.ctime())
print('tuple:', today.timetuple())
print('ordinal:', today.toordinal())
print('Year :', today.year)
print('Month:', today.month)
print('Day  :', today.day)
# 2020-06-10
# ctime: Wed Jun 10 00:00:00 2020
# tuple: time.struct_time(tm_year=2020, tm_mon=6, tm_mday=10, tm_hour=0, tm_min=0, tm_sec=0, tm_wday=2, tm_yday=162, tm_isdst=-1)
# ordinal: 737586
# Year : 2020
# Month: 6
# Day  : 10
~~~

As with time, the range of date values supported can be determined using the min and max attributes.
~~~
print('Earliest  :', datetime.date.min)
print('Latest    :', datetime.date.max)
print('Resolution:', datetime.date.resolution)
# Earliest  : 0001-01-01
# Latest    : 9999-12-31
# Resolution: 1 day, 0:00:00
~~~

Another way to create new date instances uses the replace() method of an existing date. For example, you can change the year, leaving the day and month alone.\
This gives us the difference in days between the two dates. You can use the timedelta method to specify various units of times (days, minutes, hours, etc.)
~~~
d1 = datetime.date(2015, 3, 11)
print('d1:', d1)

d2 = d1.replace(year=1990)
print('d2:', d2)
# d1: 2015-03-11
# d2: 1990-03-11
~~~

### Arithmetic
We can perform arithmetic on date objects to check for time differences.
~~~
d1 = datetime.date(2015, 3, 11)
d2 = datetime.date(1990, 3, 11)
d1-d2
# datetime.timedelta(9131)
~~~

