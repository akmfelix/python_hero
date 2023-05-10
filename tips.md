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
