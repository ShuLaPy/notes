#### Data Types:

-   **Numeric data types**: _int, float, complex_
-   **String data types**: _str_
-   **Sequence types**: _list, tuple, range_
-   **Binary types**: _bytes, bytearray, memoryview_
-   **Mapping data type**: _dict_
-   **Boolean type**: _bool_
-   **Set data types**: _set, frozenset_

Check data type with `type()`

```python
>>> print(type(10 + 5.7))
<class 'float'>
```

#### Arithmetic Operators
| Operator | Description | Syntax |
| ----     | ---- | ---- |
| +        | Addition: adds two operands | x + y |
| –        | Subtraction: subtracts two operands | x – y |
| *        | Multiplication: multiplies two operands | x * y |
| /        | Division (float): divides the first operand by the second | x / y |
| //       | Division (floor): divides the first operand by the second | x // y |
| %        | Modulus: returns the remainder when first operand is divided by the second | x % y |
| **       | Power : Returns first raised to power second | x ** y |

```python
# Arithmetic
10 + 3  # 13
10 - 3  # 7
10 * 3  # 30
10 ** 3 # 1000
10 / 3  # 3.3333333333333335
10 // 3 # 3 --> floor division - no decimals and returns an int
10 % 3  # 1 --> modulo operator - return the reminder. Good for deciding if number is even or odd
```

```python
# Converting Strings to Numbers
age = input("How old are you?")
age = int(age)
pi = input("What is the value of pi?")
pi = float(pi)
```

**Augmented Assignment Operators**
`+=`,  `-=`,  `/=`,  `*=`,  `//=`


#### Python Math Functions

```python
# Basic Functions
pow(5, 2)      # 25 --> like doing 5**2
abs(-50)       # 50
round(5.46)    # 5
round(5.468, 2)# 5.47 --> round to nth digit
bin(512)       # '0b1000000000' -->  binary format
hex(512)       # '0x200' --> hexadecimal format
```

https://www.w3schools.com/python/module_math.asp


#### Operator Precedence 

`() --> ** --> * or / --> + or -`

#### Tips
- `bin()` return binary representation
- `int('0b101', 2)` will convert to integer
- follow snake_case and it's case sensitive
- `_` signifies private in python (ex: `_user_id`)


#### String
use three \` to write multiline string

**String Concatenation**
This only works with strings

```python
first_name = "Shubham"
last_name = "Lad"
print(first_name + ' ' + last_name)

print("Shubham" + 5) # This line will give error

# We can use Type Conversion though

print("Shubham" + str(5))
```

**Formatted String**
```python
age = 26

print("Hi " + first_name + ' ' + last_name ", You are " + str(age) + " years old")

# Formatted String - write f
print(f'hi {first_name} {last_name}, You are {age} years old')
```

**String Indexes**
`[start:stop:stepover]`

```python
# [start:stop:stepover]
>>> ek_string = "0123456789"
>>> ek_string[5]
'5'
>>> ek_string[0:]
'0123456789'
>>> ek_string[:7]
'0123456'
>>> ek_string[4:7]
'456'
>>> ek_string[0:7]
'0123456'
>>> ek_string[0::2]
'02468'
>>> ek_string[-1]
'9'
>>> ek_string[::-1]
'9876543210'
```

reverse string `ek_string[::-1]`
length of string `len(string)`

Strings are immutable

**Python String Method**
https://www.w3schools.com/python/python_ref_string.asp

```python
# Basic Methods
'  I am alone '.strip()               # 'I am alone' --> Strips all whitespace characters from both ends.
'On an island'.strip('d')             # 'On an islan' --> # Strips all passed characters from both ends.
'but life is good!'.split()           # ['but', 'life', 'is', 'good!']
'Help me'.replace('me', 'you')        # 'Help you' --> Replaces first with second param
'Need to make fire'.startswith('Need')# True
'and cook rice'.endswith('rice')      # True
'bye bye'.index('e')                  # 2
'still there?'.upper()                # STILL THERE?
'HELLO?!'.lower()                     # hello?!
'ok, I am done.'.capitalize()         # 'Ok, I am done.'
'oh hi there'.find('i')               # 4 --> returns the starting index position of the first occurrence
'oh hi there'.count('e')              # 2
```

**Input**
input return string

```python
my_age = input("Enter your name")
```

!!! tip Commenting best practices

	https://realpython.com/python-comments-guide/

example:

```python
#Palindrome check
word = 'reviver'
p = bool(word.find(word[::-1]) + 1)
print(p) # True
```

#### List

List can contain any/combination of type

```python
>>> list1 = [1,2,3,4,5]
>>> list2 = ['a', 'b', 'c', 'd', 'e']
>>> list3 = [1, 2, 'a', True]

>>> list3[2] # access element
'a'

>>> ek_string[-1]
'9'
```


**List Slicing**

Same as string

```python
>>> list1[0::2]
[1,3,5]
```

Lists are mutable

`list1 = list2` modifing list1 index values will also modify the values of list2 as it gets assigned by reference.

To avoid this we can use slicing `list1 = list2[:]` slicing creates new object or we can use `list1 = list2.copy()`

**Matrix**

```python
>>> matrix = [
>>> 	[1, 2, 3],
>>> 	[4, 5, 6],
>>> 	[7, 8, 9]
>>> ]
>>>
>>> matrix[1][0]
4
```

```python
# Matrix
matrix = [[1,2,3], [4,5,6], [7,8,9]]
matrix[2][0] # 7 --> Grab first first of the third item in the matrix object

# Looping through a matrix by rows:
mx = [[1,2,3],[4,5,6]]
for row in range(len(mx)):
	for col in range(len(mx[0])):
		print(mx[row][col]) # 1 2 3 4 5 6

# Transform into a list:
[mx[row][col] for row in range(len(mx)) for col in range(len(mx[0]))] # [1,2,3,4,5,6]

# Combine columns with zip and *:
[x for x in zip(*mx)] # [(1, 3), (2, 4)]
```

**List Method**

```python
>>> len(list1)
5

# Add to List
>>> list1.append(100) #changes list inplace
[1, 2, 3, 4, 5, 100]
>>> list1.insert(2, 200) #insert at index
[1, 2, 200, 3, 4, 5, 100]
>>> list1.extend([101, 102])
[1, 2, 200, 3, 4, 5, 100, 101, 102]

# Copy a List
>>> list4 = ['apples', 'pears', 'oranges']
>>> new_list = list4.copy()
>>> new_list2 = list4[:]

# Remove from List
>>> list1.pop() #removes the last element
>>> list1.pop(0) #remove the element at index
>>> list1.remove(4) #removes the first matching element
>>> list1.clear() #removes all the element from list

# Ordering
>>> list1.sort() #sort the list inplace in accending order
>>> list1.sort(reverse=True) #sort the list inplace in accending order
>>> sorted(list1) #sort and retun new list
>>> list1.reverse() #reverse the list
>>> list(reversed([1,2,5,3]))# [3, 5, 2, 1] --> reversed() returns an iterator

>>> list1.index(2) #give the index of the matching element
>>> list2.index('d', 0, 3) # (element, startIndex, endIndex)
>>> 'x' in basket #check if list contain the value
```

```python
# Useful operations
>>> 1 in [1,2,5,3]  # True
>>> min([1,2,3,4,5])# 1
>>> max([1,2,3,4,5])# 5
>>> sum([1,2,3,4,5])# 15

# Get First and Last element of a list
>>> mList = [63, 21, 30, 14, 35, 26, 77, 18, 49, 10]
>>> first, *x, last = mList
>>> print(first) #63
>>> print(last) #10
```

**Common list patterns**

```python
>>> list(range(1, 100)) # will produce list of numbers from 1 to 99
>>> join_by = " "
>>> join_by.join(['Hi', 'my', 'name', 'is', 'Shubham']) 
'Hi my name is Shubham' # join method joins elements of list with join_by
>>> 
```

List unpacking

```python 
a, b, c, *other = [1,2,3,4,5,6,7,8,9]
```

**Advanced Functions**

```python
# Advanced Functions
list_of_chars = list('Helloooo')                                   # ['H', 'e', 'l', 'l', 'o', 'o', 'o', 'o']
sum_of_elements = sum([1,2,3,4,5])                                 # 15
element_sum = [sum(pair) for pair in zip([1,2,3],[4,5,6])]         # [5, 7, 9]
sorted_by_second = sorted(['hi','you','man'], key=lambda el: el[1])# ['man', 'hi', 'you']
sorted_by_key = sorted([
                       {'name': 'Bina', 'age': 30},
                       {'name':'Andy', 'age': 18},
                       {'name': 'Zoey', 'age': 55}],
                       key=lambda el: (el['name']))# [{'name': 'Andy', 'age': 18}, {'name': 'Bina', 'age': 30}, {'name': 'Zoey', 'age': 55}]
```

#### Dictionary

```python
>>> user = {
	'name': 'Shubham',
	'age': 26,
	'is_cool': True,
	'basket': [1,2,3]
}

>>> dict(name='Shubham') # return new directory
```

**Dictionary methods**

```python
>>> user.get('age', 55) # get method retrives value of key, second param(optional) is default value if key not present.
>>> basket in user #return boolean if key present
>>> user.keys() # return list of keys
>>> user.values() #return list of values
>>> user.items() #return tuple with pair of key and value
>>> user.clear()
>>> user.copy()
>>> user.pop('age') #removed perticular field
>>> user.update({'age': 27}) #upsert the key into dict
>>> user['favourite_snack'] = 'Grapes'

#Remove key
>>> del user['name']
>>> user.pop('name', None)

>>> new_dict = dict([['name','Andrei'],['age',32],['magic_power',False]])  # Creates a dict from collection of key-value pairs.
>>> new_dict = dict(zip(['name','age','magic_power'],['Andrei',32, False]))# Creates a dict from two collections.


>>> {**my_dict, **{'cool': True} }                                         # {'name': 'Andrei Neagoie', 'age': 30, 'magic_power': False, 'favourite_snack': 'Grapes', 'cool': True}
>>> new_dict = dict([['name','Andrei'],['age',32],['magic_power',False]])  # Creates a dict from collection of key-value pairs.
>>> new_dict = dict(zip(['name','age','magic_power'],['Andrei',32, False]))# Creates a dict from two collections.
```

**Ordered Dictionary**

```python
from collections import OrderedDict
# Store each person's languages, keeping # track of who responded first. 
programmers = OrderedDict()
programmers['Tim'] = ['python', 'javascript']
programmers['Sarah'] = ['C++']
programmers['Bia'] = ['Ruby', 'Python', 'Go']

for name, langs in programmers.items():
    print(name + '-->')
    for lang in langs:
      print('\t' + lang)
```

#### Tuples

Tuples is immutable and they are faster than list

```python
>>> my_tuple = (1,2,3,4,5)
>>> my_tuple[1] # return 2
>>> 
>>> my_tuple = ('apple','grapes','mango', 'grapes')
>>> apple, grapes, mango, grapes = my_tuple.   # Tuple unpacking
>>> len(my_tuple)                              # 4
>>> my_tuple[2]                                # mango
>>> my_tuple[-1]                               # 'grapes'
```

```python
# Methods
>>> my_tuple.index('grapes') # 1
>>> my_tuple.count('grapes') # 2
```

```python
# Zip
>>> list(zip([1,2,3], [4,5,6])) # [(1, 4), (2, 5), (3, 6)]

# unzip
>>> z = [(1, 2), (3, 4), (5, 6), (7, 8)] # Some output of zip() function
>>> unzip = lambda z: list(zip(*z))
>>> unzip(z)
```

#### Sets

Set's store and return only `unique` element

```python
>>> my_set = {1,2,3,4,5,5}
>>> my_set.add(100) #add value to set
>>> my_set.add(2) # 2 is already present in the set
>>> my_set.copy()
>>> my_set.clear() # {}
>>> my_set.remove(100)      # {1} --> Raises KeyError if element not found
>>> my_set.discard(100)     # {1} --> Doesn't raise an error if element not found
```

```python
>>> my_list = [1,2,3,4,5,5]
>>> set(my_list)
{1, 2, 3, 4, 5
>>> list(my_set)
[1, 2, 3, 4, 5]
>>> 1 in my_set
>>> len(my_set)
```

**Sets methods**

```python
>>> my_set = {1,2,3,4,5}
>>> your_set = {4,5,6,7,8,9,10}
>>> my_set.difference(your_set)
{1, 2, 3}
>>> my_set.discard(5) #inplace
{1, 2, 3, 4}
>>> my_set.difference_update(your_set) #it removes all common values
{1, 2, 3}
>>> my_set.union(your_set) #join sets together 
{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
>>> my_set | your_set #union
>>> my_set.intersection(your_set) #return common value
{4, 5}
>>> my_set & your_set #intersection
>>> my_set.isdisjoint(your_set) #return boolen true if nothing common or false
>>> my_set.issubset(your_set) #return boolean - if my_set present in your_set
>>> my_set.issuperset(your_set) #return boolen - if my_set contains your_set
```

#### Conditional Logic

```python
age = 26

if age > 18 and age <= 50 and not(age == 27):
	print("Your are adult")
elif age > 50:
	print("Buddha ho gaya re tu")
elif not age:
	print("Paida to ho ja")
else:
	print("Baccha he tu")
```

```python
# Ternery Operator
# condition_if_true if condition else condition_if_else

is_friend = True
can_message = "Message Allowed" if is_friend else "Not Allowed to Message"
```

**Logical Operators**
| Operator | Description | Example |
| ---- | ---- | ---- |
| and | Returns True if both statements are true | `x < 5 and  x < 10` |
| or | Returns True if one of the statements is true | `x < 5 or x < 4` |
| not | Reverse the result, returns False if the result is true | `not(x < 5 and x < 10)` |

**Comparison Operators**
| Operator | Name | Example |
| ---- | ---- | ---- |
| == | Equal |x == y | 
| != | Not equal | x != y |
| /> | Greater than | x >  y |
| < | Less than | x < y |
| />= | Greater than or equal to | x >= y |
| <= | Less than or equal to | x <= y |

**is vs `==`**

`is` will return `True` if two variables point to the same object (in memory), `==` if the objects referred to by the variables are equal.

```python
>>> a = [1, 2, 3]
>>> b = a
>>> b is a 
True
>>> b == a
True

# Make a new copy of list `a` via the slice operator, 
# and assign it to variable `b`
>>> b = a[:] 
>>> b is a
False
>>> b == a
True
```


```python
any([False, True, False])# True if at least one item in collection is truthy, False if empty.
all([True,1,3,True])     # True if all items in collection are true
```

#### For Loops

```python
for item in (1,2,3,4,5):
	for x in ['a', 'b', 'c']:
		print(str(item) + x)
```

> list, dictionary, tuple, set, string are iterables

```python
>>> user = {
>>> 	"name": "Shubham",
>>> 	"age": 26,
>>> 	"is_cool": True
>>> }
>>>
>>> for item in user:
>>> 	print(item)
name
age
is_cool

>>> for item in user.items():
>>> 	key, value = item
>>> 	print(key, value)
>>>
>>> for key, value in user.items():
>>> 	print(key, value)
>>> 	
>>> for item in user.keys():
>>> 	print(item)
>>> 	
>>> for item in user.values():
>>> 	print(item)
```

**range**

```python
for number in range(0, 100): # 0 to 99
	print(number)

for _ in range(0, 10, 2): # (start, end, stepover)
	print(_)
```

**Enumerate**

```python
for i, char in enumerate('Helllloooo'): # it gives index and value both
	print(i, char)

for i, number in enumerate(list(range(100))):
	print(i, number)
	if number == 50:
		print(f'index of 50 is: {i}')
```

**Counter**

```python
from collections import Counter
colors = ['red', 'blue', 'yellow', 'blue', 'red', 'blue']
counter = Counter(colors)# Counter({'blue': 3, 'red': 2, 'yellow': 1})
counter.most_common()[0] # ('blue', 3)
```

#### While Loops

```python
i = 0

while i < 50:
	print(i)
	break
else: #else will only run if the loop completes without break statement
	print("done with all the work")
```

```python
my_list = [1,2,3]

for item in my_list:
	print(item)

i = 0
while i < len(my_list):
	print(my_list[i])
	i += 1
```

**break** statement: The **break** statement in Python terminates the current loop and resumes execution at the next statement, just like the traditional break found in C.

```python
while True:
	response = input('Say something')
	if (response == 'bye'):
		break
```

**continue** statement: The **continue** statement in Python returns the control to the beginning of the while loop. The **continue** statement rejects all the remaining statements in the current iteration of the loop and moves the control back to the top of the loop.

```python
for letter in 'Python':     # This skips printing letter 'h'
   if letter == 'h':
      continue
   print('Current Letter :', letter)
```

**pass** statement: The **pass** statement in Python is used when a statement is required syntactically but you do not want any command or code to execute.

The **pass** is also useful in places where your code will eventually go, but has not been written yet (e.g., in stubs for example)

```python
for i in 'Python': # Empty loop
    # No error will be raised
    pass
 
def fun():
    pass
```

**Find Duplicates** [[#^90cfc7]] ^60485b

```python
some_list = ['a', 'b', 'c', 'b', 'd', 'm', 'n', 'n']

duplicates = []
for value in some_list:
	if some_list.count(value) > 1:
		if value not in duplicates:
			duplicates.append(value)

print(duplicates)
```

#### Functions

define functions first and then only call it or else python will give an error

```python
def say_something():
	print("Hello Shubham")

say_something()
```

**parameters vs arguments**

```python
#parameters
def say_hello(name, emoji):
	print(f'Hello {name} {emoji}')

#arguments
say_hello("Shubham", "🤩")

#positional arguments
say_hello("Snehal", "😁")

#keyword arguments
say_hello(emoji='😎', name='Emily')

#default parameters
def say_hello(name='Alex', emoji='👨‍💻'):
	print(f'Hello {name} {emoji}')

say_hello('Shubham') #it will use default parameter for emoji
```

**return**

```python
def sum(num1, num2):
	return num1 + num2

sum(5, sum(2, 8)) # retrun 15

# return another function
def sum(num1, num2):
	def another_func(n1, n2):
		return n1 + n2
	return another_func(num1, num2)
```

**Closures**

```python
def get_multiplier(a):
    def out(b):
        return a * b
    return out

>>> multiply_by_3 = get_multiplier(3)
>>> multiply_by_3(10)
30
```

**Docstrings**

Python documentation strings (or docstrings) provide a convenient way of associating documentation with Python modules, functions, classes, and methods.

It will get associated with `__doc__`
 
```python
def sum(num1, num2):
	'''
	Info: This function return sum of two numbers passed
	'''
	return num1 + num2

print(sum.__doc__)
```

this will open doc in editors on hover also the docstring will print when you pass function in help

```python
>>> help(sum)
Help on function sum in module __main__:

sum(num1, num2)
    Info: This function return sum of two numbers passed
```

**\*args \*\*kwargs**

> Rule: params, \*args, default parameters, \*\*kwargs

```python
>>> def super_func(*args, **kwargs):
>>> 	print(args)
>>> 	print(kwargs)
>>> # arguments should be grouped and subsequent
>>> super_func(1,2,3,4,5, num1=5, num2=10) # kewaord arguments automatically gets assigned to the **kwargs and everything else gets assigned to *args
(1, 2, 3, 4, 5) # args as tuples
{'num1': 5, 'num2': 10} # kwargs as dictionary
>>> head, *body, tail = [1,2,3,4,5]
```

```python
def add(*a):
    return sum(a)

add(1, 2, 3) # 6
```

Example: 

```python
def highest_even(li):
	evens = []
	for item in li:
		if item % 2 == 0:
			evens.append(item)
	return max(evens)

print(highest_even([10,2,3,4,8,11]))
```

**pure function**

A function is called pure function if it always returns the same result for same argument values and it has no side effects like modifying an argument (or global variable) or outputting something.

Rules:
1. it always returns the same result for same argument values 
2. it should not interact outside the functions scope
	-  ex: modifying an argument (or global variable) or outputting something.

```python
def multiply_by_2(li):
	new_list = []
	for item in li:
		new_list.append(item*2)
	return new_list

multiply_by_2()
```

#### Scopes

```python

if True:
	x = 10 # Global scope - X can be accessed outeside of the if condition

def some_func():
	total = 100 # Local scope - total can be accessed only inside this function
```

**scope rule**

#1 - Start with local
#2 - Parent local
#3 - Global
#4 - Built-in python

```python
a = 1 # global scope

def parent():
	a = 10 # local scope - it creates new varibale in local scope
	def confusion():
		return a
	return confusion()

print(parent()) # print 10
print(a) # print 1
```

**global**

```python
total = 0

def count():
	golbal total # if global not written here python will create local var
	total += 1
	return total

count()
```

**nonlocal**

```python
def outer():
	x = 'local'
	def inner(): 
		nonlocal x # use parent variable
		x = 'nonlocal'
		print('inner: ', x)
	inner()
	print('outer: ', x)

outer()
# inner: nonlocal
# outer: nonlocal
```

#### Important built in functions

**map**

with map we write pure functions

`map(action, iterables)`
action: logic to perform on each item of the iterables
iterables: iterable on which you want to perform that action
return map object with type casting we can convert it

```python
my_list = [1,2,3]

def multiply_by_2(item):
	return item * 2 # right only action that you want to perform on each item

list(map(multiply_by_2, my_list)) # map(action, iterables)
# [2,4,6]
```

**filter**

```python
my_list = [1,2,3]

def only_odd(item):
	return item % 2 != 0

list(filter(only_odd, my_list))
# [1,3]
```

**zip**

zip is like zipper we need two plus iterables and we can zip them together, it will zip till the length of the smallest list

```python
my_list = [1,2,3]
your_list = [10,20,30]

list(zip(my_list, your_list))
# [(1, 10), (2, 20), (3, 30)]
```

**reduce**

same as javascript
`reduce(function, itterabale, initial value)`

```python
from functools import reduce

my_list = [1,2,3]

def accumulator(acc, item):
	return acc + item

reduce(accumulator, my_list, 0)
# 6
```

#### Comprehensions

**List comprehensions**

list = \[ variable/expression for_loop condition \]

```python
my_list = [char for char in 'hello']
my_list1 = [char for char in range(0,100)]
my_list2 = [num**2 for num in range(0, 100)]
my_list3 = [num**2 for num in range(0, 100) if num % 2 == 0]
```

**Set comprehensions**

```python
my_set = {char for char in 'hello'}
my_set1 = {char for char in range(0, 100)}
my_set2 = {num**2 for num in range(0, 100)}
my_set3 = {num**2 for num in range(0, 100) if num % 2 == 0]}
```

**Dictionary comprehensions**

```python
simple_dict = {
	'a': 1,
	'b': 2,
}

my_dict = {key:val**2 for key, val in simple_dict.items()}
my_dict = {k:v**2 for k, v in simple_dict.items() if v%2 == 0}
```

**Find Duplicates** [[#^60485b]] ^90cfc7

```python
some_list = ['a', 'b', 'c', 'b', 'd', 'm', 'n', 'n']

duplicates = list(set([x for x in some_list if simple_list.count(x) > 1]))
```

#### Modules

```python
# main.py

import utility

utility.multiply(2,5)
```

```python
# utility.py

def multiply(num1, num2):
	return num1 * num2

def devide(num1, num2):
	return num1 / num2
```

#### Packages

package is a folder containing modules

`folder`
	`__init__.py`  this file is really important for package, it can be empty
	`utility.py`

```python
import folder.utility

folder.utility.something()
```

we can have `package` under `package`

`folder`
	`__init__.py` 
	`utility.py`
	`other_folder`
		`__init__.py` 
		`product.py`

**Different ways of importing**

```python
if __name__ == '__main__': # Runs main() if file wasn't imported.
    main()
```

```python
import folder.other_folder.product

folder.other_folder.product.get_items()
```

```python
from folder.other_folder import product

product.get_items()
```

```python
from folder.other_folder.product import get_items, buy

get_items()
buy('apple')
```

```python
from utility import *
```

```python
import <module_name>
from <module_name> import <function_name>
import <module_name> as m
from <module_name> import <function_name> as m_function
from <module_name> import *
```

#### Generators

**Convenient way to implement the iterator protocol.**

```python
def count(start, step):
    while True:
        yield start
        start += step
```

```python
>>> counter = count(10, 2)
>>> next(counter), next(counter), next(counter)
(10, 12, 14)
```

#### Decorators

A decorator takes a function, adds some functionality and returns it.

```python
@decorator_name
def function_that_gets_passed_to_decorator():
    ...
```

Decorator that prints function's name every time it gets called.

```python
from functools import wraps

def debug(func):
    @wraps(func)
    def out(*args, **kwargs):
        print(func.__name__)
        return func(*args, **kwargs)
    return out

@debug
def add(x, y):
    return x + y
```

- `wraps` is a helper decorator that copies `metadata` of function `add()` to function `out()`.
- Without it `'add.__name__'` would return `'out'`.

#### Class

User defined objects are created using the class keyword

```python
class <name>:
    age = 80 # Class Object Attribute
    def __init__(self, a):
        self.a = a # Object Attribute

    @classmethod
    def get_class_name(cls):
        return cls.__name__
```

**Inheritance**

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age  = age

class Employee(Person):
    def __init__(self, name, age, staff_num):
        super().__init__(name, age)
        self.staff_num = staff_num
```

**Multiple Inheritance**

```python
class A: pass
class B: pass
class C(A, B): pass
```

MRO determines the order in which parent classes are traversed when searching for a method:

```python
>>> C.mro()
[<class 'C'>, <class 'A'>, <class 'B'>, <class 'object'>]
```

#### Exception

```python
try:
  5/0
except ZeroDivisionError:
  print("No division by zero!")
```

```python
while True:
  try:
    x = int(input('Enter your age: '))
  except ValueError:
    print('Oops!  That was no valid number.  Try again...')
  else: # code that depends on the try block running successfully should be placed in the else block.
    print('Carry on!')
    break
```

**Raising Exception**

```python
raise ValueError('some error message')
```

**Finally**

```python
try:
  raise KeyboardInterrupt
except:
  print('oops')
finally:
  print('All done!')
```

#### Command Line Arguments

```python
import sys
script_name = sys.argv[0]
arguments   = sys.argv[1:]
```

#### File

**File IO**

Opens a file and returns a corresponding file object.

```python
<file> = open('<path>', mode='r', encoding=None)
```

**Modes**
'r' - Read (default).
'w' - Write (truncate).
'x' - Write or fail if the file already exists.
'a' - Append.
'w+' - Read and write (truncate).
'r+' - Read and write from the start.
'a+' - Read and write from the end.
't' - Text mode (default).
'b' - Binary mode.

```python
<file>.seek(0)                      # Moves to the start of the file.
<str/bytes> = <file>.readline()     # Returns a line.
<list>      = <file>.readlines()    # Returns a list of lines.
<file>.write(<str/bytes>)           # Writes a string or bytes object.
<file>.writelines(<list>)           # Writes a list of strings or bytes objects.
```

Read Text from File

```python
def read_file(filename):
    with open(filename, encoding='utf-8') as file:
        return file.readlines() # or read()

for line in read_file(filename):
  print(line)
```

Write Text to File

```python
def write_to_file(filename, text):
    with open(filename, 'w', encoding='utf-8') as file:
        file.write(text)
```

Append Text to File

```python
def append_to_file(filename, text):
    with open(filename, 'a', encoding='utf-8') as file:
        file.write(text)
```


#### Useful Libraries

**CSV**

```python
import csv

# Read Rows from CSV File
def read_csv_file(filename):
    with open(filename, encoding='utf-8') as file:
        return csv.reader(file, delimiter=';')

# Write Rows to CSV File
def write_to_csv_file(filename, rows):
    with open(filename, 'w', encoding='utf-8') as file:
        writer = csv.writer(file, delimiter=';')
        writer.writerows(rows)
```

**JSON**

```python
import json
<str>    = json.dumps(<object>, ensure_ascii=True, indent=None)
<object> = json.loads(<str>)

# Read Object from JSON File
def read_json_file(filename):
    with open(filename, encoding='utf-8') as file:
        return json.load(file)

# Write Object to JSON File
def write_to_json_file(filename, an_object):
    with open(filename, 'w', encoding='utf-8') as file:
        json.dump(an_object, file, ensure_ascii=False, indent=2)
```

**Pickle**

```python
import pickle
<bytes>  = pickle.dumps(<object>)
<object> = pickle.loads(<bytes>)

# Read Object from File
def read_pickle_file(filename):
    with open(filename, 'rb') as file:
        return pickle.load(file)

# Write Object to File
def write_to_pickle_file(filename, an_object):
    with open(filename, 'wb') as file:
        pickle.dump(an_object, file)
```

**Profile**

Basic

```python
from time import time
start_time = time()  # Seconds since
...
duration = time() - start_time
```

Math

```python
from math import e, pi
from math import cos, acos, sin, asin, tan, atan, degrees, radians
from math import log, log10, log2
from math import inf, nan, isinf, isnan
```

Statistics

```python
from statistics import mean, median, variance, pvariance, pstdev
```

Random

```python
from random import random, randint, choice, shuffle
random() # random float between 0 and 1
randint(0, 100) # random integer between 0 and 100
random_el = choice([1,2,3,4]) # select a random element from list
shuffle([1,2,3,4]) # shuffles a list
```

**Regex**

```python
import re
<str>   = re.sub(<regex>, new, text, count=0)  # Substitutes all occurrences.
<list>  = re.findall(<regex>, text)            # Returns all occurrences.
<list>  = re.split(<regex>, text, maxsplit=0)  # Use brackets in regex to keep the matches.
<Match> = re.search(<regex>, text)             # Searches for first occurrence of pattern.
<Match> = re.match(<regex>, text)              # Searches only at the beginning of the text.
```

**Date Time**

```python
from datetime import date, time, datetime, timedelta
from dateutil.tz import UTC, tzlocal, gettz
```

```python
<D>  = date(year, month, day)
<T>  = time(hour=0, minute=0, second=0, microsecond=0, tzinfo=None, fold=0)
<DT> = datetime(year, month, day, hour=0, minute=0, second=0, ...)
<TD> = timedelta(days=0, seconds=0, microseconds=0, milliseconds=0,
                 minutes=0, hours=0, weeks=0)
```

```python
<D/DTn>  = D/DT.today()         # Current local date or naive datetime.
<DTn>    = DT.utcnow()          # Naive datetime from current UTC time.
<DTa>    = DT.now(<tz>)         # Aware datetime from current tz time.
```

####
---
[Python Detailed CheetSheet](https://github.com/gto76/python-cheatsheet)
