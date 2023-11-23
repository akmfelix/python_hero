# Iterators and Generators
Generator functions allow us to write a function that can send back a value and then later resume to pick up where it left off. This type of function is a generator in Python, allowing us to generate a sequence of values over time. The main difference in syntax will be the use of a yield statement.\
\
In most aspects, a generator function will appear very similar to a normal function. The main difference is when a generator function is compiled they become an object that supports an iteration protocol. That means when they are called in your code they don't actually return a value and then exit. Instead, generator functions will automatically suspend and resume their execution and state around the last point of value generation. The main advantage here is that instead of having to compute an entire series of values up front, the generator computes one value and then suspends its activity awaiting the next instruction. This feature is known as state suspension.
~~~
# Generator function for the cube of numbers (power of 3)
def gencubes(n):
    for num in range(n):
        yield num**3

for x in gencubes(5):
    print(x)
# 0
# 1
# 8
# 27
# 64
~~~
Generators are best for calculating large sets of results (particularly in calculations that involve loops themselves) in cases where we don’t want to allocate the memory for all of the results at the same time.
~~~
def genfibon(n):
    """
    Generate a fibonnaci sequence up to n
    """
    a = 1
    b = 1
    for i in range(n):
        yield a
        a,b = b,a+b

for num in genfibon(10):
    print(num)
# 1
# 1
# 2
# 3
# 5
# 8
# 13
# 21
# 34
# 55
~~~
What if this was a normal function, what would it look like?
~~~
def fibon(n):
    a = 1
    b = 1
    output = []
    for i in range(n):
        output.append(a)
        a,b = b,a+b
    return output
fibon(10)
# [1, 1, 2, 3, 5, 8, 13, 21, 34, 55]
~~~

## next() and iter() built-in functions
The next() function allows us to access the next element in a sequence.
~~~
def simple_gen():
    for x in range(3):
        yield x
# Assign simple_gen 
g = simple_gen()
print(next(g))
# 0
print(next(g))
# 1
print(next(g))
# 2
print(next(g))
StopIteration: 
~~~
You might be wondering that why don’t we get this error while using a for loop? A for loop automatically catches this error and stops calling next().\
\
Let's go ahead and check out how to use iter().
~~~
s = 'hello'
s_iter = iter(s)
next(s_iter)
# 'h'
~~~
