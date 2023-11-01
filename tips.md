## Tuple unpacking
~~~
# list of tuples
stock_prices = [('APPL',100),('GOOG',200),('MSFT',300)]
for ticker, price in stock_prices:
    print(ticker, price)
APPL 100
GOOG 200
MSFT 300
~~~

## Work Hours
~~~
work_hours_list = [('A',500),('B',550),('C',450),('D',700),('E',100)]
def check(work_hours):
    
    current_max = 0
    employee_name = ''
    
    for name, hours in work_hours:
        if hours > current_max:
            current_max = hours
            employee_name = name
        else:
            pass
    
    return (employee_name, current_max)

name, hours = check(work_hours_list)
~~~

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

## multiple functions
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

def check_guess(mylist, user_guess):
    if mylist[user_guess] == 'O':
        print('correct')
    else:
        print('wrong')
    print(mylist)

mixedup_list = shuffle_list(mylist)
guess = player_guess()
check_guess(mixedup_list, guess)
~~~

### shuffle game
~~~
from random import shuffle

mycup = ['','','','','','','','','','','O']

def shuffle_cup(mycup):
    shuffle(mycup)
    return mycup

def player_guess():
    user_guess=''
    while user_guess not in ['0','1','2']:
        user_guess = input('Choose 0, 1 or 2: ')
    return int(user_guess)

def player_guess():
    while True:
        try:
            guess = int(input('pick a number between 0 - 10:\n'))
            if guess>=0 and guess<=10:
                break
            print('pick correct number.')
        except ValueError:
            print('give a number')
    return guess

cup_game()
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

~~~
from random import shuffle
mylist=[' ', 'O', ' ']
def shuffle_list(mylist):
    shuffle(mylist)
    return mylist

def player_guess():
    guess=''
    while guess not in ['0','1','2']:
        guess = input('Pick 0, 1 or 2:  ')
    return int(guess)

def cup_game():
    mixed_list = shuffle_list(mylist)
    while True:
        if mixed_list[player_guess()] == 'O':
            print('Congratulations! You Won!')
            break
        else:
            print('\n Try again')
            pass
cup_game()
~~~

## Anthropomorphism
~~~
_______________________________________________________________
def myfunc(mystring):
    mylist = [x[1].upper() if x[0]%2==0 else x[1].lower()  for x in enumerate(mystring)]
    return ''.join(mylist)

_______________________________________________________________
def myfunc(mystring):
    mylist=[]
    for i in enumerate(mystring):
        if i[0]%2==0:
            mylist.append(i[1].upper())
        else:
            mylist.append(i[1].lower())
    return ''.join(mylist)

_______________________________________________________________
def myfunc(mystring):
    modstring=''
    for index in range(len(mystring)):
        if index%2==0:
            modstring += mystring[index].lower()
        else:
            modstring += mystring[index].upper()
    return modstring

_______________________________________________________________    
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

## Summer 69
SUMMER OF '69: Return the sum of the numbers in the array, except ignore sections of numbers starting with a 6 and extending to the next 9 (every 6 will be followed by at least one 9). Return 0 for no numbers.
~~~
def summer_69(arr):
    it = iter(arr)
    total_sum = 0
    for i in arr:
        if i==6:
            9 in it
        else:
            total_sum += i
    return total_sum


def summer69_v2(arr):
    total_sum = 0
    omit = False
    for i in arr:
        if omit:
            if i==9:
                omit = False
        elif i==6:
            omit = True
        else:
            total_sum += i
    return total_sum
~~~

## Spy game
SPY GAME: Write a function that takes in a list of integers and returns True if it contains 007 in order.
~~~
def spy_game(nums):
    agent_code = [0,0,7]
    for i in nums:
        if i == agent_code[0]:
            print(agent_code)
            agent_code.pop(0)
    return len(agent_code)==0


def spy_game2(nums):
    check = []
    for i in nums:
        if i==0:
            if len(check)<=1:
                check.append(i)
        elif i==7:
            if len(check)==2:
                check.append(i)
    print(check)
    return check==[0,0,7]
~~~

## Count primes
COUNT PRIMES: Write a function that returns the number of prime numbers that exist up to and including a given number
~~~
def count_primes(num):
    primes = []
    for i in range(2,num+1):
        for p in primes:
            if i%p == 0:
                break
        else:
            primes.append(i)
    return len(primes)


def count_primes_v2(start, end):
    primes = []
    ctr = 0
    for i in range(2, end+1):
        for p in primes:
            if i%p == 0:
                break
        else:
            primes.append(i)
            if i>=start:
                ctr += 1
    return (ctr, primes)
~~~


