## Statements Assessment
### Use for, .split(), and if to create a Statement that will print out words that start with 's':
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

### Use range() to print all the even numbers from 0 to 10.
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

### Use List comprehension to create a list of all numbers between 1 and 50 that are divisible by 3
~~~
mylist = [x for x in range(1,50) if x%3==0]
# [3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48]
~~~

### Go through the string below and if the length of a word is even print "even!"
~~~
st = 'Print every word in this sentence that has an even number of letters'
mylist = []
for item in st.split():
    if len(item)%2==0:
        mylist.append(item)

mylist = [x for x in st.split() if len(x)%2==0]
# ['word', 'in', 'this', 'sentence', 'that', 'an', 'even', 'number', 'of']
~~~

### Write a program that prints the integers from 1 to 100. But for multiples of three print "Fizz" instead of the number, and for the multiples of five print "Buzz". For numbers which are multiples of both three and five print "FizzBuzz"
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

### Use List Comprehension to create a list of the first letters of every word in the string below
~~~
st = 'Create a list of the first letters of every word in this string'
result = [letter[0] for letter in st.split()]
# ['C', 'a', 'l', 'o', 't', 'f', 'l', 'o', 'e', 'w', 'i', 't', 's']
~~~

### ANIMAL CRACKERS: Write a function takes a two-word string and returns True if both words begin with same letter
~~~
def animal_crackers(text):
    wordlist = text.split()
    return wordlist[0][0] == wordlist[1][0]
# animal_crackers('Levelheaded Llama')
# True
~~~

### OLD MACDONALD: Write a function that capitalizes the first and fourth letters of a name
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

### MASTER YODA: Given a sentence, return a sentence with the words reversed
~~~
def master_yoda(text):
    return text[::-1]

def master_yoda2(text):
    reversed_list = []
    for i in text:
        reversed_list = [i] + reversed_list
    return ''.join(reversed_list)

# master_yoda2('I am home')
# 'emoh ma I'
~~~

### ALMOST THERE: Given an integer n, return True if n is within 10 of either 100 or 200
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
    total_sum=0
    omit=False
    for i in arr:
        if omit:
            if i==9:
                omit=False
        elif i==6:
            omit=True
        else:
            total_sum += i
    return total_sum

def summer_69_v2(arr):
    total_sum = 0
    it = iter(arr)
    for i in arr:
        if i == 6:
            9 in it
        else:
            total_sum += i
    return total_sum
# summer_69([2, 1, 6, 9, 11])
# 14
~~~

### 
