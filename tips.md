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
