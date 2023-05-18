## Take integer user input in Python
~~~
try:
  user_input = int(input('Enter a number: '))
  print(user_input)
except ValueError:
  print('Enter a valid integer')
~~~

## Only allow Integer user input in Python
~~~
while True:
  try:
    user_input = int(input('Enter a number: '))
    print(user_input)
    break
  except ValueError:
    print('Enter a valid digit')
~~~

## Only allow integer user input in a given range
~~~
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


## Guess Game
~~~
import random
guess_number = random.randint(0,100)
guesses_list=[0]
while True:
    try:
        user_guess = int(input('Enter a guessing number: '))
        if user_guess<1 or user_guess>100:
            print('OUT OF BONDS')
            continue
        if user_guess==guess_number:
            print(f'CONGRATULATIONS YOU HAVE WON IN {len(guesses_list)} ROUNDS')
            break
        guesses_list.append(user_guess)
        if guesses_list[-2]:
            if abs(guess_number - user_guess) < abs(guess_number - guesses_list[-2]):
                print('WARMER')
            else:
                print('COLDER')
        else:
            if abs(guess_number - user_guess) < 11:
                print('WARM')
            else:
                print('COLD')
    except ValueError:
        print('Enter a valid number')
~~~

## Cups shuffle game
~~~
from random import shuffle
mylist = ['','O','']
def shuffle_list(mylist):
    shuffle(mylist)
    return mylist
def player_guess():
    user_guess=''
    while user_guess not in ['0','1','2']:
        user_guess = input('Choose 0, 1 or 2: ')
    return int(user_guess)
def check_guess(mylist):
    while True:
        guess = player_guess()
        if mylist[guess] == 'O':
            print('correct')
            break
        else:
            print('wrong')
    print(mylist)
mixedlist = shuffle_list(mylist)
check_guess(mixedlist)
~~~

## Anthropomorphism
~~~
def myfunc(mystring):
    modstring=''
    for index in range(len(mystring)):
        if index%2==0:
            modstring += mystring[index].lower()
        else:
            modstring += mystring[index].upper()
    return modstring
    
def myfunc(mystring):
    string = ''
    for index, letter in enumerate(mystring):
        if index%2==0:
            string += letter.lower()
        else:
            string += letter.upper()
    return string  
~~~

## Lesser of two evens
LESSER OF TWO EVENS: Write a function that returns the lesser of two given numbers if both numbers are even, but returns the greater if one or both numbers are odd
~~~
def lesser_of_two_evens(a,b):
    if a%2==0 and b%2==0:
        if a<b:
            return a
        elif a>b:
            return b
    else:
        if a<b:
            return b
        elif a>b:
            return a
~~~

## Animal crackers
ANIMAL CRACKERS: Write a function takes a two-word string and returns True if both words begin with same letter
~~~
def animal_crackers(text):
    mylist=text.split()
    if len(mylist)>1:
        if mylist[0][0]==mylist[1][0]:
            return True
        else:
            return False
    else:
        return print('list is out of range')
~~~

## Makes twenty
MAKES TWENTY: Given two integers, return True if the sum of the integers is 20 or if one of the integers is 20. If not, return False
~~~
def makes_twenty(n1,n2):
    if sum((n1,n2))==20:
        return True
    elif n1==20 and n2==20:
        return False
    elif n1==20 or n2==20:
        return True
    else:
        return False
~~~

## Old MacDonald
OLD MACDONALD: Write a function that capitalizes the first and fourth letters of a name
~~~
def old_macdonald(name):
    newstring=''
    for index, letter in enumerate(name):
        if index==0 or index==3:
            newstring += letter.capitalize()
        else:
            newstring += letter
    return newstring
~~~

## Master Yoda
MASTER YODA: Given a sentence, return a sentence with the words reversed
~~~
def master_yoda(text):
    text_list = text.split()
    return ' '.join(text_list[::-1])
    
def master_yoda(text):
    return ' '.join(text.split()[::-1])
    
def master_yoda(text):
    mylist=[]
    for item in text.split():
        mylist = [item] + mylist
    return ' '.join(mylist)    
~~~    

## Almost there
ALMOST THERE: Given an integer n, return True if n is within 10 of either 100 or 200
~~~
def almost_there(n):
    if abs(100-n)<=10 or abs(200-n)<=10:
        return True
    else:
        return False
~~~

## Find 33
Given a list of ints, return True if the array contains a 3 next to a 3 somewhere.
~~~
def has33(nums):
    for i in range(0,len(nums)-1):
        if nums[i]==3 and nums[i+1]==3:
            return True
    return False
    
def has33(nums):
    for i in range(0,len(nums)-1):
        if nums[i:i+2] == [3,3]:
            return True
    return False
~~~

## Blackjack
BLACKJACK: Given three integers between 1 and 11, if their sum is less than or equal to 21, return their sum. If their sum exceeds 21 and there's an eleven, reduce the total sum by 10. Finally, if the sum (even after adjustment) exceeds 21, return 'BUST'
~~~
def blackjack(a,b,c):
    if sum((a,b,c))<=21:
        return sum((a,b,c))
    elif sum((a,b,c))>21 and (11 in (a,b,c)):
        return sum((a,b,c))-10
    elif sum((a,b,c))>21:
        return 'BUST'
~~~

