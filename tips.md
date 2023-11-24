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

## Game List

~~~
game_list = [0,1,2,3,4,5]

def display_game(game_list):
    print(f'Here is the current list: {game_list}')

def position_choice():
    while True:
        try:
            position_choice = int(input('Pick a postition (0-5): '))
            if position_choice<0 or position_choice>5:
                print('Sorry, invalid choice!')
                continue
            break
        except ValueError:
            print('Input must be a digit!')
    return int(position_choice)

def replacement_value(game_list, index_position):
        user_placement = input('Type a string to place at position:  ')
        game_list[index_position] = user_placement
        return game_list

def game_on():
    keep_playing = True
    display_game(game_list)
    while keep_playing:
        index_position = position_choice()
        replacement_value(game_list, index_position)
        display_game(game_list)
        user_answer=''
        while user_answer not in ['Y', 'N']:
            user_answer = input('Keep playing?  ')
            if user_answer not in ['Y','N']:
                print('Sorry, acceptable answers are only Y or N!')
            elif user_answer == 'Y':
                continue
            elif user_answer == 'N':
                keep_playing = False
    return game_list

game_on()
~~~

# Count instances of unique items in a list
~~~
mylist = [1,1,1,1,1,1,2,2,2,2,2,23,3,3,3,3,3,3]
## method 1
d ={}
for i in mylist:
    if i in d:
        d[i] += 1
    else:
        d[i] = 1

## method 2
d = {}
for i in mylist:
    d[i] = d.get(i, 0) + 1

# {1: 6, 2: 5, 23: 1, 3: 6}
~~~
