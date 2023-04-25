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

## Data structures
* int. Integers
* float. Floating points
* str. Strings
* list. Lists ordered sequence of objects ['10', 'hello', '10.5']
* dict. Dictionaries. Unordered key:value pairs {'mykey':'value'}
* tup. Tuples. Ordered immutable sequence of objects ('10', 'hello', '10.5')
* set. Sets. Unordered collection of unique objects {'10', 'b'}
* bool. Booleans. True or False

One illusion may beget another. For example, since 0.1 is not exactly 1/10, summing three values of 0.1 may not yield exactly 0.3, either:          
`.1 + .1 + .1 == .3`     
`False`

Since the 0.1 cannot get any closer to the exact value of 1/10 and 0.3 cannot get any closer to the exact value of 3/10, then pre-rounding with round() function cannot help:             
`round(.1, 1) + round(.1, 1) + round(.1, 1) == round(.3, 1)`
`False`           

Though the numbers cannot be made closer to their intended exact values, the round() function can be useful for post-rounding so that results with inexact values become comparable to one another:           
`round(.1 + .1 + .1, 10) == round(.3, 10)`
`True`

