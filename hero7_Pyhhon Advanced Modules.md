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

# Math and Random - modules
### Useful math functions
~~~
## rounding numbers
import math
help(math)
value = 4.5
math.floor(value)
# 4
math.ceil(value)
# 5
round(value)
4
~~~

~~~
## mathematical constants
math.pi
# 3.141592653589793
math.e
# 2.718281828459045
math.tau
# 6.283185307179586
math.inf
# inf
math.nan
# nan
math.log(math.e)
# 1
~~~

### random module
Random Module allows us to create random numbers. We can even set a seed to produce the same random set every time.
#### Understanding a seed
Setting a seed allows us to start from a seeded psuedorandom number generator, which means the same random numbers will show up in a series. Note, you need the seed to be in the same cell if your using jupyter to guarantee the same results each time. Getting a same set of random numbers can be important in situations where you will be trying different variations of functions and want to compare their performance on random values, but want to do it fairly (so you need the same set of random numbers each time).
~~~
import random
random.randint(0,100)
# 55
~~~

~~~
## The value 101 is completely arbitrary, you can pass in any number you want
random.seed(101)
random.randint(0,100)
# 74
~~~

#### Random with Sequences
~~~
mylist = list(range(0,20))
random.choice(mylist)
# 12
~~~

#### Sample with Replacement
Take a sample size, allowing picking elements more than once. Imagine a bag of numbered lottery balls, you reach in to grab a random lotto ball, then after marking down the number, you place it back in the bag, then continue picking another one.
~~~
random.choices(population=mylist,k=10)
# [15, 14, 17, 8, 17, 2, 19, 17, 6, 1]
~~~

#### Sample without Replacement
Once an item has been randomly picked, it can't be picked again. Imagine a bag of numbered lottery balls, you reach in to grab a random lotto ball, then after marking down the number, you leave it out of the bag, then continue picking another one.
~~~
random.sample(population=mylist,k=10)
# [17, 19, 11, 14, 1, 3, 4, 10, 5, 15]
~~~

#### Shuffle a list
Note: This effects the object in place!
~~~
## Don't assign this to anything!
random.shuffle(mylist)
mylist
# [9, 11, 7, 12, 10, 16, 0, 2, 18, 13, 3, 5, 17, 1, 15, 6, 14, 19, 4, 8]
~~~

# Python debugger
You've probably used a variety of print statements to try to find errors in your code. A better way of doing this is by using Python's built-in debugger module (pdb). The pdb module implements an interactive debugging environment for Python programs. It includes features to let you pause your program, look at the values of variables, and watch program execution step-by-step, so you can understand what your program actually does and find bugs in the logic.
~~~
import pdb

x = [1,3,4]
y = 2
z = 3

result = y + z
print(result)

# Set a trace using Python Debugger
pdb.set_trace()

result2 = y+x
print(result2)
~~~

# Regular Expressions
Regular Expressions (sometimes called regex for short) allows a user to search for strings using almost any sort of rule they can come up. For example, finding all capital letters in a string, or finding a phone number in a document.
### Searching for Basic Patterns
~~~
text = "The person's phone number is 408-555-1234. Call soon!"
'phone' in text
# True
~~~
But let's show the format for regular expressions, because later on we will be searching for patterns that won't have such a simple solution.\
Now we've seen that re.search() will take the pattern, scan the text, and then returns a Match object. If no pattern is found, a None is returned
~~~
import re
pattern = 'phone'
re.search(pattern,text)
# <_sre.SRE_Match object; span=(13, 18), match='phone'>
pattern = "NOT IN TEXT"
re.search(pattern,text)
~~~

#### span
~~~
pattern = 'phone'
match = re.search(pattern,text)
match
# <_sre.SRE_Match object; span=(13, 18), match='phone'>
match.span()
## start and end position
# (13, 18)
match.start()
match.end()
~~~
But what if the pattern occurs more than once?\
Notice it only matches the first instance.
~~~
text = "my phone is a new phone"
match = re.search("phone",text)
match.span()
~~~
findall('match text', 'search text'). If we wanted a list of all matches, we can use .findall() method:
~~~
matches = re.findall("phone",text)
matches
# ['phone', 'phone']
len(matches)
# 2
~~~
finditer('match text', 'search text'). To get actual match objects, use the iterator:
~~~
for match in re.finditer("phone",text):
    print(match.span())
(3, 8)
(18, 23)
~~~
If you wanted the actual text that matched, you can use the .group() method.
~~~
match.group()
# 'phone'
~~~
## Patterns
We could just use search method if we know the exact phone or email, but what if we don't know it? We may know the general format, and we can use that along with regular expressions to search the document for strings that match a particular pattern.
### Identifiers for Characters in Patterns
Characters such as a digit or a single string have different codes that represent them. You can use these to build up a pattern string. Notice how these make heavy use of the backwards slash \ . Because of this when defining a pattern string for regular expression we use the format.\
placing the r in front of the string allows python to understand that the \ in the pattern string are not meant to be escape slashes.
~~~
r'mypattern'
~~~

~~~
Character	Description	        Example Pattern Code	Exammple Match
\d	        A digit	            file_\d\d	            file_25
\w	        Alphanumeric	    \w-\w\w\w	            A-b_1
\s	        White space	        a\sb\sc	                a b c
\D	        A non digit	        \D\D\D	                ABC
\W	        Non-alphanumeric	\W\W\W\W\W	            *-+=)
\S	        Non-whitespace	    \S\S\S\S	            Yoyo
~~~
Example:\
Notice the repetition of \d. That is a bit of an annoyance, especially if we are looking for very long strings of numbers. Let's explore the possible quantifiers.
~~~
text = "My telephone number is 408-555-1234"
phone = re.search(r'\d\d\d-\d\d\d-\d\d\d\d',text)
phone.group()
# '408-555-1234'
~~~

### Quantifiers
Now that we know the special character designations, we can use them along with quantifiers to define how many we expect.
~~~
Character	Description	                Example Pattern Code	Exammple Match
+	        Occurs one or more times	Version \w-\w+	        Version A-b1_1
{3}	        Occurs exactly 3 times	    \D{3}	                abc
{2,4}	    Occurs 2 to 4 times	        \d{2,4}	                123
{3,}	    Occurs 3 or more	        \w{3,}	                anycharacters
\*	        Occurs zero or more times	A\*B\*C*	            AAACC
?	        Once or none	            plurals?	            plural
~~~
Let's rewrite our pattern using these quantifiers:
~~~
re.search(r'\d{3}-\d{3}-\d{4}',text)
# <_sre.SRE_Match object; span=(23, 35), match='408-555-1234'>
~~~

### Groups
What if we wanted to do two tasks, find phone numbers, but also be able to quickly extract their area code (the first three digits). We can use groups for any general task that involves grouping together regular expressions (so that we can later break them down).\
Using the phone number example, we can separate groups of regular expressions using parenthesis:
~~~
phone_pattern = re.compile(r'(\d{3})-(\d{3})-(\d{4})')
results = re.search(phone_pattern,text)
## The entire result
results.group()
# '408-555-1234'
~~~
Can then also call by group position. remember groups were separated by parenthesis (). Something to note is that group ordering starts at 1. Passing in 0 returns everything
~~~
results.group(1)
# 555
results.group(3)
# 1234
# We only had three groups of parenthesis
results.group(4)
# IndexError: no such group
~~~

## Additional Regex Syntax or | operator
Use the pipe operator to have an or statment.
~~~
re.search(r"man|woman","This man was here.")
# <_sre.SRE_Match object; span=(5, 8), match='man'>
re.search(r"man|woman","This woman was here.")
# <_sre.SRE_Match object; span=(5, 10), match='woman'>
~~~

### The Wildcard Character
Use a "wildcard" as a placement that will match any character placed there. You can use a simple period . for this.
~~~
re.findall(r".at","The cat in the hat sat here.")
# ['cat', 'hat', 'sat']
re.findall(r".at","The bat went splat")
#  ['bat', 'lat']
~~~
Notice how we only matched the first 3 letters, that is because we need a . for each wildcard letter. Or use the quantifiers described above to set its own rules.
~~~
re.findall(r"...at","The bat went splat")
# ['e bat', 'splat']
~~~
However this still leads the problem to grabbing more beforehand. Really we only want words that end with "at".
~~~
# One or more non-whitespace that ends with 'at'
re.findall(r'\S+at',"The bat went splat")
~~~
### Starts with and Ends With
We can use the ^ to signal starts with, and the $ to signal ends with:\
Note that this is for the entire string, not individual words!
~~~
## Ends with a number
re.findall(r'\d$','This ends with a number 2')
# ['2']
## Starts with a number
re.findall(r'^\d','1 is the loneliest number.')
# ['1']
~~~

### Exclusion
To exclude characters, we can use the ^ symbol in conjunction with a set of brackets []. Anything inside the brackets is excluded.\
To get the words back together, use a + sign
~~~
phrase = "there are 3 numbers 34 inside 5 this sentence."
re.findall(r'[^\d]',phrase)
re.findall(r'[^\d]+',phrase)
# ['there are ', ' numbers ', ' inside ', ' this sentence.']
~~~
We can use this to remove punctuation from a sentence.
~~~
test_phrase = 'This is a string! But it has punctuation. How can we remove it?'
re.findall('[^!.? ]+',test_phrase)
clean = ' '.join(re.findall('[^!.? ]+',test_phrase))
clean
# 'This is a string But it has punctuation How can we remove it'
~~~

### Brackets for Grouping
As we showed above we can use brackets to group together options, for example if we wanted to find hyphenated words:
~~~
text = 'Only find the hypen-words in this sentence. But you do not know how long-ish they are'
re.findall(r'[\w]+-[\w]+',text)
# ['hypen-words', 'long-ish']
~~~

### Parenthesis for Multiple Options
If we have multiple options for matching, we can use parenthesis to list out these options. For Example:
~~~
# Find words that start with cat and end with one of these options: 'fish','nap', or 'claw'
text = 'Hello, would you like some catfish?'
texttwo = "Hello, would you like to take a catnap?"
textthree = "Hello, have you seen this caterpillar?"
re.search(r'cat(fish|nap|claw)',text)
re.search(r'cat(fish|nap|claw)',texttwo)
re.search(r'cat(fish|nap|claw)',textthree)
# <_sre.SRE_Match object; span=(27, 34), match='catfish'>
# <_sre.SRE_Match object; span=(32, 38), match='catnap'>
# # None returned
~~~
