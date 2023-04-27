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

