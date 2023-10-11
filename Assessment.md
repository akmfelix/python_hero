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
