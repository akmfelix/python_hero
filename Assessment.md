## Statements Assessment
## Print out words that start with 's'
Use for, .split(), and if to create a Statement that will print out words that start with 's':
~~~
# method 1
st = 'Print only the words that start with s in this sentence'
for word in st.split():
  if word[0]=='s':
    print(word)

# method 2
mylist = [item for item in st.split() if item[0]=='s']        
mylist
~~~

## Print all the even numbers from 0 to 10.
Use range() to print all the even numbers from 0 to 10.
~~~
list(range(0,10,2))
# [0, 2, 4, 6, 8]

mylist=[]
for i in range(0,10):
    if i%2==0:
        mylist.append(i)
# [0, 2, 4, 6, 8]

mylist = [x*y for x in [2,4,6] for y in [1,10,1000]]
# [0, 2, 4, 6, 8]
 
~~~

## Create a list of all numbers between 1 and 50 that are divisible by 3.
Use List comprehension to create a list of all numbers between 1 and 50 that are divisible by 3.
~~~
mylist = [x for x in range(1,50) if x%3==0]
# [3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48]
~~~

## Print "even!".
Go through the string below and if the length of a word is even print "even!".
~~~
st = 'Print every word in this sentence that has an even number of letters'
mylist = []
for item in st.split():
    if len(item)%2==0:
        mylist.append(item)

mylist = [x for x in st.split() if len(x)%2==0]
# ['word', 'in', 'this', 'sentence', 'that', 'an', 'even', 'number', 'of']
~~~

## FizzBuzz
Write a program that prints the integers from 1 to 100. But for multiples of three print "Fizz" instead of the number, and for the multiples of five print "Buzz". For numbers which are multiples of both three and five print "FizzBuzz".
~~~
for num in range(1,101):
  if num%5==0 and num%3==0:
    print('FizzBuzz')
  if num%5==0:
    print('Buzz')
  if num%3==0:
    print('Fizz')
  else:
    print(num)
~~~

## List Comprehension.
Use List Comprehension to create a list of the first letters of every word in the string below.
~~~
st = 'Create a list of the first letters of every word in this string'
result = [letter[0] for letter in st.split()]
# ['C', 'a', 'l', 'o', 't', 'f', 'l', 'o', 'e', 'w', 'i', 't', 's']
~~~

## ANIMAL CRACKERS.
Write a function takes a two-word string and returns True if both words begin with same letter.
~~~
def animal_crackers(text):
    wordlist = text.split()
    return wordlist[0][0] == wordlist[1][0]
# animal_crackers('Levelheaded Llama')
# True
~~~

## OLD MACDONALD.
Write a function that capitalizes the first and fourth letters of a name.
~~~
def old_macdonald(name):
    text = name[0].upper()+name[1:3]+name[3].upper()+name[4:]
    return text

def old_macdonald2(name):
    if len(name)>3:
        return name[:3].capitalize() + name[3:].capitalize()
    else:
        return 'give more than 3 symbols'
~~~

## MASTER YODA.
Given a sentence, return a sentence with the words reversed.
~~~
def master_yoda(text):
    return text[::-1]

def master_yoda2(text):
    reversed_list = []
    for i in text:    # .SPLIT()   !!!!
        reversed_list = [i] + reversed_list
    return ''.join(reversed_list)

# master_yoda2('I am home')
# 'emoh ma I'
~~~

## ALMOST THERE.
Given an integer n, return True if n is within 10 of either 100 or 200.
~~~
def almost_there(n):
    return abs(n-100)<=10 or abs(n-200)<=10

# almost_there(105)
# True
~~~

### FIND 33
~~~
def has_33(nums):
    for i in range(len(nums)-1):
        if nums[i]==3 and nums[i+1]==3:
            return True
    return False

# has_33([1, 3, 3])
# True
~~~

### PAPER DOLL: Given a string, return a string where for every character in the original there are three characters
~~~
def paper_doll(text):
    triple_string =''
    for i in text:
        triple_string += i*3
    return triple_string

def paper_doll(text):
    mylist = [x*3 for x in text]        
    return ''.join(mylist)

# paper_doll('Hello')
# 'HHHeeellllllooo'
~~~

### BLACKJACK: Given three integers between 1 and 11, if their sum is less than or equal to 21, return their sum. If their sum exceeds 21 and there's an eleven, reduce the total sum by 10. Finally, if the sum (even after adjustment) exceeds 21, return 'BUST'
~~~
def blackjack(a,b,c):
    if sum((a,b,c))<=21:
        return sum((a,b,c))
    elif sum((a,b,c))>21 and 11 in (a,b,c):
        return sum((a,b,c))-10
    else:
        return 'BUST'
~~~

### SUMMER OF '69: Return the sum of the numbers in the array, except ignore sections of numbers starting with a 6 and extending to the next 9 (every 6 will be followed by at least one 9). Return 0 for no numbers.

~~~
def summer_69(arr):
    omit = False
    total_sum = 0
    for i in arr:
        if omit:
            if i==9:
                omit=False
            else:
                continue
        elif i==6:
            omit = True
        else:
            total_sum += i
    return total_sum

def summer_69_v2(arr):
    total_sum = 0
    it = iter(arr)
    for i in it:
        if i == 6:              # if i!=6 or 9 not in it:
            9 in it             # tot += i
        else:
            total_sum += i
    return total_sum

def summer_69(arr):
    it = iter(arr)
    mylist = [x for x in it 
             if x!=6 or 9 not in it]
    return sum(mylist)

# summer_69([2, 1, 6, 9, 11])
# 14
~~~

## SPY GAME.
Write a function that takes in a list of integers and returns True if it contains 007 in order.
~~~
def spy_game(nums):
    agent_team = [0,0,7, 'spy']
    for i in nums:
        if i == agent_team[0]:
            agent_team.pop(0)
    return len(agent_team)==1

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
~~~

## Print Big
PRINT BIG: Write a function that takes in a single letter, and returns a 5x5 representation of that letter.
~~~
mydict1 = {1:'  *  ',
           2:' * * ',
           3:'*   *',
           4:'*****',
           5:'**** '}
mydict2 = {'A':[1,2,3,4,5]}
for i in mydict2['A']:
    print(mydict1[i])

def print_big(letter):
    patterns = {1:'  *  ',
                2:' * * ',
                3:'*   *',
                4:'*****',
                5:'**** ',
                6:'   * ',
                7:' *   ',
                8:'*   * ',
                9:'*    '}
    alphabet = {'A':[1,2,4,3,3],
                'B':[5,3,5,3,5],
                'C':[4,9,9,9,4],
                'D':[5,3,3,3,5],
                'E':[4,9,4,9,4]}
    for pattern in alphabet[letter.upper()]:
        print(patterns[pattern])
~~~

# Functions Homework
## Volume
Write a function that computes the volume of a sphere given its radius.
~~~
___________________________________________________
def cube_rad(rad):
    return rad**3

def vol():
    #x = cube_rad(rad)
    pi = 3.14
    return (4/3) * pi * cube_rad(rad)

rad = 2
vol()
# 33.49333333333333

___________________________________________________
pi = 3.14
def vol(rad):
    return (4/3)*pi*rad**3
# 33.49333333333333
~~~

## Range
Write a function that checks whether a number is in a given range (inclusive of high and low)
~~~
___________________________________________________
def ran_check(num,low,high):
    return num in range(low, high+1)
ran_check(5,2,7)
# True

def ran_check(num, low, high):
    if num in range(low, high+1):
        return print(f'{num} is in range between {low} and {high}')
    else:
        return print(f'{num} is not in a given range')
ran_check(5,2,7)
# 5 is in range between 2 and 7
~~~

## Count strings
Write a Python function that accepts a string and calculates the number of upper case letters and lower case letters.
~~~
___________________________________________________
def up_low(s):
    str_list = [x for x in s if x not in ['.','?',',','"',' ']]
    str_low = []
    str_up = []
    for i in str_list:
        if i.isupper():
            str_up.append(i)
        else:
            str_low.append(i)
    print(f'Original string: {s}')
    print(f'No. of Upper case characters :  {len(str_up)}')
    print(f'No. of Lower case characters :  {len(str_low)}')
up_low('Hello Mr. Rogers, how are you this fine Tuesday?')
# Original string: Hello Mr. Rogers, how are you this fine Tuesday?
# No. of Upper case characters :  4
# No. of Lower case characters :  33

___________________________________________________
def up_low(s):
    d = {'upper':0, 'lower':0}
    for i in s:
        if i.isupper():
            d['upper'] += 1
        elif i.islower():
            d['lower'] += 1
        else:
            pass
    print(f'Original String :  {s}')
    print(f"No. of Upper case characters :  {d['upper']}")
    print(f"No. of Lower case Characters :  {d['lower']}")
up_low('Hello Mr. Rogers, how are you this fine Tuesday?')
# Original string: Hello Mr. Rogers, how are you this fine Tuesday?
# No. of Upper case characters :  4
# No. of Lower case characters :  33
~~~

## Unique elements
Write a Python function that takes a list and returns a new list with unique elements of the first list.
~~~
___________________________________________________
def unique_list(lst):
    return list(set(lst))

unique_list([1,1,1,1,2,2,3,3,3,3,4,5])
# {1, 2, 3, 4, 5}

___________________________________________________
def unique_list(lst):
    unique = []
    for i in lst:
        if i not in unique:
            unique.append(i)
    return unique
unique_list([1,1,1,1,2,2,3,3,3,3,4,5])
# {1, 2, 3, 4, 5}
~~~

## Total multiply
Write a Python function to multiply all the numbers in a list.
~~~
___________________________________________________
def multiply(numbers):  
    total_multiply = 1
    for i in numbers:
        total_multiply *= i
    return total_multiply
multiply([1,2,3,-4])
# -24
~~~

## Palindrom
Write a Python function that checks whether a word or phrase is palindrome or not.
~~~
___________________________________________________
def palindrome(s):
    reverse = []
    for i in s.replace(' ',''):
        reverse = [i]+reverse
    return ''.join(reverse)==s.replace(' ','')

def palindrom(s):
    return s.replace(' ','') == s.replace(' ','')[::-1]

palindrome('nurses run')
# True
~~~

## Pangram
Write a Python function to check whether a string is pangram or not. (Assume the string passed in does not have any punctuation)
~~~
import string
def ispangram(str1, alphabet=string.ascii_lowercase):
    str1 = str1.replace(' ','').lower()
    myalphabet = set(str1)
    return myalphabet==set(alphabet)

ispangram("The quick brown fox jumps over the lazy dog")
# True
~~~

# Object Oriented Programming
## Problem 1
Fill in the Line class methods to accept coordinates as a pair of tuples and return the slope and distance of the line.
~~~
___________________________________________________
# method 1
import math
class Line:
    def __init__(self,coor1,coor2):
        self.coor1 = coor1
        self.coor2 = coor2
    def distance(self):
        return math.sqrt( (self.coor2[0]-self.coor1[0])**2 + (self.coor2[1]-self.coor1[1])**2 )
    def slope(self):
        return (self.coor2[1]-self.coor1[1]) / (self.coor2[0]-self.coor1[0])
___________________________________________________
# method 2
class Line(object):
    def __init__(self,coor1,coor2):
        self.coor1 = coor1
        self.coor2 = coor2
    def distance(self):
        x1,y1 = self.coor1
        x2,y2 = self.coor2
        return ((x2-x1)**2 + (y2-y1)**2)**0.5
    def slope(self):
        x1,y1 = self.coor1
        x2,y2 = self.coor2
        return (y2-y1)/(x2-x1)

coordinate1 = (3,2)
coordinate2 = (8,10)
li = Line(coordinate1,coordinate2)
li.distance()
# 9.433981132056603
li.slope()
# 1.6
~~~

## Problem 2
For this challenge, create a bank account class that has two attributes:
* owner
* balance
and two methods:
* deposit
* withdraw
As an added requirement, withdrawals may not exceed the available balance.                
Instantiate your class, make several deposits and withdrawals, and test to make sure the account can't be overdrawn.
~~~
class Account:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance

    def __str__(self):
        return f'Account owner:     {self.owner} \nAccount balance:   ${self.balance}'
        
        
    def deposit(self, deposited_sum):
        self.balance = self.balance + deposited_sum
        print('Deposit accepted')
    
    def withdraw(self, withdraw_sum):
        if self.balance - withdraw_sum>0:
            self.balance = self.balance - withdraw_sum
            print('Withdrawal Accepted')
        else:
            print('Funds Unavailable!')
## 1. Instantiate the class
acct1 = Account('Jose',100)

## 2. Print the object
print(acct1)
# Account owner:     Jose 
# Account balance:   $100

## 3. Show the account owner attribute
acct1.owner
# 'Jose'

## 4. Show the account balance attribute
acct1.balance
# 100

## 5. Make a series of deposits and withdrawals
acct1.deposit(50)
# Deposit accepted

acct1.withdraw(75)
# Withdrawal Accepted

## 6. Make a withdrawal that exceeds the available balance
acct1.withdraw(500)
Funds Unavailable!
~~~






