# Errors and Exceptions Handling
~~~
print('Hello)
File "<ipython-input-1-db8c9988558c>", line 1
    print('Hello)
                 ^
SyntaxError: EOL while scanning string literal
~~~
Note how we get a SyntaxError, with the further description that it was an EOL (End of Line Error) while scanning the string literal. This is specific enough for us to see that we forgot a single quote at the end of the line. Understanding these various error types will help you debug your code much faster.
\
\
This type of error and description is known as an Exception. Even if a statement or expression is syntactically correct, it may cause an error when an attempt is made to execute it. Errors detected during execution are called exceptions and are not unconditionally fatal.            

## try and except
The basic terminology and syntax used to handle errors in Python are the **try** and **except** statements. The code which can cause an exception to occur is put in the **try** block and the handling of the exception is then implemented in the **except** block of code. The syntax follows:
~~~
try:
   You do your operations here...
   ...
except ExceptionI:
   If there is ExceptionI, then execute this block.
except ExceptionII:
   If there is ExceptionII, then execute this block.
   ...
else:
   If there is no exception then execute this block. 
~~~
* Example 1
~~~
___________________________________________________
try:
    result = 10 + '10'
except:
    print('Add only proper numbers')
# Add only proper numbers

___________________________________________________
try:
    result = 10 + 10
except:
    print('Add only proper numbers.')
else: # else if there is no error
    print(result)
    print('Add went well')
# 20
# Add went well
~~~

* Example 2 for raising specific errors
~~~
___________________________________________________
try:
    f = open('testfile.txt', 'w')
    f.write('Write a test line')
except TypeError:
    print('There was a Type Error')
except OSError:
    print('There was a OS Error')
finally:
    print('I always run')
# I always run
## testfile was created

___________________________________________________
try:
    f = open('testfile.txt', 'r')
    f.write('Write a test line')
except TypeError:
    print('There was a Type Error')
except OSError:
    print('There was a OS Error')
finally:
    print('I always run')
# There was a OS Error
# I always run
~~~
* Example 3 get a number from a user
~~~
___________________________________________________
def ask_for_int():
    while True:
        try:
            result = int(input('Provide a number:   '))
            break
        except:
            print('That is not a number')
            continue
        finally:
            print('End of try/except/finally]')

___________________________________________________
while True:
  try:
    num = int(input('Integer between 1 and 100: '))
    print(num)
    if num < 1 or num > 100:
      raise ValueError
    break
  except ValueError:
    print('Please enter an integer between 1 and 100.')
~~~

# pylit
Style and Error checking
* pip install pylit
~~~
___________________________________________________
# in PyCharm
'''
I am commenting
'''

def myfunc():
    '''
    A simple function
    '''
    first = 1
    second = 2
    print(first)
    print(second)
myfunc()

### Open the PyCharm settings window with menu File → Settings, then navigate to menu Tools → External Tools in the sidebar. (Or search "external tools")
### Set up an external tool by clicking on the + sign and filling in the fields accordingly. In Program use the path you got when running which pylint. For the other values, you can use the same from the image.
### Run pylint from menu Tools → External Tools → pylint:
## in Pycharm
## Tools -> pylit
# Your code has been rated at 10.00/10 (previous run: 8.33/10, +1.67)
~~~

# Unit testing
There are dozens of good testing libraries out there. Most are third-party packages that require an install. These are simple tools that merely look at your code, and they'll tell you if there are style issues or simple problems like variable names being called before assignment.
* pylit
* pyflakes
* pep8
A far better way to test your code is to write tests that send sample data to your program, and compare what's returned to a desired outcome. Two such tools are available from the standard library:
* unittest
* doctest

## pylist
pylint tests for style as well as some very basic program logic.\
First you should install module.
~~~
pip install pylist
~~~
