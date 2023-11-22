# Decorators
Remember that in Python everything is an object. That means functions are objects which can be assigned labels and passed into other functions.
~~~
__________________________________
def hello(name='Jose'):
    return 'Hello '+name
hello()
# 'Hello Jose'
~~~
Assign another label to the function. Note that we are not using parentheses here because we are not calling the function hello, instead we are just passing a function object to the greet variable.
~~~
greet = hello
greet
# <function __main__.hello(name='Jose')>
greet()
# 'Hello Jose'
~~~
Even though we deleted the name hello, the name greet still points to our original function object. It is important to know that functions are objects that can be passed to other objects!
~~~
del hello
hello()
# NameError: name 'hello' is not defined
greet()
# 'Hello Jose'
~~~

## Functions within functions
Great! So we've seen how we can treat functions as objects, now let's see how we can define functions inside of other functions.\
Note how due to scope, the welcome() function is not defined outside of the hello() function.
~~~
__________________________________
def hello(name='Jose'):
    print('The hello() function has been executed')
    
    def greet():
        return '\t This is inside the greet() function'
    
    def welcome():
        return "\t This is inside the welcome() function"
    
    print(greet())
    print(welcome())
    print("Now we are back inside the hello() function")
hello()
# The hello() function has been executed
# 	 This is inside the greet() function
# 	 This is inside the welcome() function
# Now we are back inside the hello() function
welcome()
# NameError: name 'welcome' is not defined
~~~

## Returning Functions
Returning functions from within functions.
* In the if/else clause we are returning greet and welcome, not greet() and welcome().
* This is because when you put a pair of parentheses after it, the function gets executed; whereas if you don’t put parentheses after it, then it can be passed around and can be assigned to other variables without executing it.
* When we write x = hello(), hello() gets executed and because the name is Jose by default, the function greet is returned. If we change the statement to x = hello(name = "Sam") then the welcome function will be returned. We can also do print(hello()()) which outputs This is inside the greet() function.
~~~
__________________________________
def hello(name='Almas'):
    def greet():
        return '\t This is inside greet() function'
    def welcome():
        return '\t This is inside welcome() function'
    if name=='Almas':
        return greet
    else:
        return welcome
x = hello()
x
<function __main__.hello.<locals>.greet()>
print(x())
#	   This is inside the greet() function
~~~

