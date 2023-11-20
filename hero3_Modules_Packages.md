# Modules and Packages

## Pip Install and PyPi
* pip install.
* pip is a simple way to download packages at your command line directly from the PyPi repository.
~~~
from colorama import init
init()
from colorama import Fore
print('yellow submarine')
## text in yellow colour
#yellow submarine
~~~

## Modules
* Modules in Python are simply Python files with the .py extension, which implement a set of functions.
* To import a module, we use the import command.
* The first time a module is loaded into a running Python script, it is initialized by EXECUTING THE CODE in the module once.
* If another module in your code imports the same module again, it will not be loaded twice but once only - so local variables inside the module act as a "singleton" - they are initialized only once.
* If we want to import the math module, we simply import the name of the module:
~~~
import math
math.ceil(2.4)
# 3
~~~

### Exploring built-in modules
* Two very important functions come in handy when exploring modules in Python - the dir and help functions.
* We can look for which functions are implemented in each module by using the dir function:
~~~
print(dir(math))
# ['__doc__', '__loader__', '__name__', '__package__', '__spec__', 'acos', 'acosh', 'asin', 'asinh', 'atan', 'atan2', 'atanh', 'ceil', 'copysign', 'cos', 'cosh', 'degrees', 'e', 'erf', 'erfc', 'exp', 'expm1', 'fabs', 'factorial', 'floor', 'fmod', 'frexp', 'fsum', 'gamma', 'gcd', 'hypot', 'inf', 'isclose', 'isfinite', 'isinf', 'isnan', 'ldexp', 'lgamma', 'log', 'log10', 'log1p', 'log2', 'modf', 'nan', 'pi', 'pow', 'radians', 'sin', 'sinh', 'sqrt', 'tan', 'tanh', 'tau', 'trunc']
~~~

* When we find the function in the module we want to use, we can read about it more using the help function, inside the Python interpreter:
~~~
help(math.ceil)
Help on built-in function ceil in module math:

ceil(...)
    ceil(x)
    
    Return the ceiling of x as an Integral.
    This is the smallest integer >= x.
~~~

### Writing modules
* Writing Python modules is very simple. To create a module of your own, simply create a new .py file with the module name, and then import it using the Python file name (without the .py extension) using the import command.

## Packages
* Packages are name-spaces which contain multiple packages and modules themselves. They are simply directories, but with a twist.
* Each package in Python is a directory which MUST contain a special file called _init_.py. This file can be empty, and it indicates that the directory it contains is a Python package, so it can be imported the same way a module can be imported.
### Writing packages
* If we create a directory called foo, which marks the package name, we can then create a module inside that package called bar. We also must not forget to add the _init_.py file inside the foo directory.
* To use the module bar, we can import it in two ways.
* In the first method, we must use the foo prefix whenever we access the module bar. In the second method, we don't, because we import the module to our module's name-space.
~~~
import foo.bar
OR
from foo import bar
~~~

* The _init_.py file can also decide which modules the package exports as the API, while keeping other modules internal, by overriding the _all_ variable, like so:
~~~
__init__.py:
__all__ = ["bar"]
~~~

# __name__ == '__main__'
* Sometimes when you are importing from a module, you would like to know whether a modules function is being used as an import, or if you are using the original .py file of that module. In this case we can use the:
~~~
__name__ == '__main__'
~~~
* When your script is run by passing it as a command to the Python interpreter python myscript.py all of the code that is at indentation level 0 gets executed. Functions and classes that are defined are, well, defined, but none of their code gets ran. Unlike other languages, there's no main() function that gets run automatically - the main() function is implicitly all the code at the top level.
* In this case, the top-level code is an if block.  __name__ is a built-in variable  which evaluate to the name of the current module. However, if a module is being  run directly (as in myscript.py above), then __name__ instead is set to the  string "__main__". Thus, you can test whether your script is being run directly   or being imported by something else by testing:
~~~
if __name__ == "__main__":
    func()
    func2()
    ...    
~~~
#### Example
* If that code is being imported into another module, the various function and class definitions will be imported, but the main() code won't get run. As a basic example, consider the following two scripts:
~~~
# file one.py
def func():
    print("func() in one.py")

    print("top-level in one.py")

if __name__ == "__main__":
    print("one.py is being run directly")
else:
    print("one.py is being imported into another module")
~~~
and then:
~~~
# file two.py
import one

print("top-level in two.py")
one.func()

if __name__ == "__main__":
    print("two.py is being run directly")
else:
    print("two.py is being imported into another module")
~~~
Now, if you invoke the interpreter as python one.py
~~~
# top-level in one.py
# one.py is being run directly
~~~
python two.py:
~~~
top-level in one.py
one.py is being imported into another module
top-level in two.py
func() in one.py
two.py is being run directly
~~~
