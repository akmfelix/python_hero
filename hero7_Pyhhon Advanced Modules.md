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
The standard tuple uses numerical indexes to access its members.\\
For simple use cases, this is usually enough. On the other hand, remembering which index should be used for each value can lead to errors, especially if the tuple has a lot of fields and is constructed far from where it is used. A namedtuple assigns names, as well as the numerical index, to each member.\
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
