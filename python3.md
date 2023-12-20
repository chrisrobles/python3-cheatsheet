# Python 3

<mark>EVERYTHING IS OBJECTS</mark>

## Resources

### [Style Guide](https://pep8.org/)

### Online IDE

- [line by line execution](http://pythontutor.com/visualize.html#mode=edit)
- [online ide](https://www.online-python.com)

## Starting Point for Script

```python
def main():  # defined starting point, allows to import and run program in another script
    print("hello world")
# ...
# only runs if program ran independently
if __name__ == '__main__': 
    main()
```

## Comments

```python
# comment
"""
multi
line
comment
"""
```

## Print

```python
# Spaces
print('Hello, World!')
print('Hello,', 'World!')
print('Hello', end=', '); print('World!')  # end parameter default = '\n' (new line)

# Line breaks
print('Hello,')
print('World!')

print('Hello,') ; print('World!')

# Multiline strings
print('''
Hello,
World!
''')

# Variables
world = "World"
print(f'Hello, {world.title()}!')
print('Hello, {}!'.format(world))
print('Hello, {person}!'.format(person=world))
print("Hello, ", world, "!")

# Raw string
print(r'Hello \t World \n !')  # Hello \t World \n !
```

### Printing to Debug

Use logpoints instead

Prints to the console and doesnt stop program

## Variables

### None / Null

spam
spam == None #True

### Bool

False = 
- False
- 0
- None
- empty (container)
- ""

### Swap

a,b = b,a

### Get Address

id(a)

### Iterable / sequence

string, list, tuple, ...

### Unused Variables

```python
_ = 5
first, _, last = ["first", "get rid of", "last"]  # will get rid of "get rid of"
```

### Global Variable

define a global variable in local scope with global keyword

```python
def spam():
    global eggs
    eggs = 'spam'
eggs = 'global'
spam()
print(eggs) #prints spam
```

## Arithmetic Operators

```python
** #Exponent
% #Modulus
// #Floor division
/
*
-
+
```

## Logical Operators

```python
and
or
not
is not None
```

### Ternary Operator:

`[result_on_true] if [expression] else [result_on_false]`

## Conditions

- -1 is not a false statement

### if statement

```python
if condition :
    code
elif condition :
    code
else :
    code
```

### if expression | ternary operator:

`[on_true] if [expression] else [on_false]`

### switch statement 

- [(!!!Python 3.10 or higher !!!)](https://docs.python.org/3.10/whatsnew/3.10.html#pep-634-structural-pattern-matching)
    
```python
match subject:
    case <pattern_1>:
        <action_1>:
    case <pattern_2>:
        <action_2>:
    case <pattern_3>:
        <action_3>:
    case _:
        <action_default>
```

## Special Operators

### is

is two variables the same object in memory
- if comparing two lists, then compares by reference

```python
a = 1
b = 1
a is b # False
b = a
a is b # True
```

### in

```python
myList = [1,2,3]

# Iterable (check value is in iterable)
if 3 in myList: # True

#List (iterate and get value from list)
for x in myList: 
  print(x) # 1 2 3
```
- can check for a list inside a list

### yield

yield will return only when `__next__()` called on object

```python
for iterator in iterable[1:]:
    yield joiner
    yield from iterable
```

### * operator

depends what it is put on

#### variable assignment, argument

unpacking operator

- assigns a value from an iterable to a sequence of variables
  - if returning 1 value, just returns a value
  - else returning > 1 value, returns a list of values

```python
# unpack list
arr = [1,2,3]
print(*arr) #Output: 1 2 3 INSTEAD OF [1, 2, 3]
## same as ' '.join(map(str, arr))

# unpack iterable into multiple variables
first, *middle, last = [1, 2, 3, 5, 7] # first = 1, middle = [2,3,5] last = 7

# unpack iterable into single variable
*string, = 'PythonIsTheBest' #['P', 'y', 't', 'h', 'o', 'n', 'I', 's', 'T', 'h', 'e', 'B', 'e', 's', 't']
```

#### parameter

packing operator

- pack several values in a single tuple

```python
myFunc(1, "a")

def myFunc(*allParams):
  print(allParams) # (1,'a')
```

### ** unpacking operator for dictionaries

can use inside callables and other dictionaries

`merged_dict = {**food, **colors}`



## Loops

- break = break Loop
- continue = jump back to start of loop
- pass = does nothing just keeps going forward like normal

### while

```python
while condition :
  code
```

### do while

```python
while True:
  print(i)
  i = i + 1
  if i > 3:
    break
```

### for statement | for loop

```python
#for
for i in range(5): # 0->4 (5 not included)
  print('Jimmy Five Times ' + str(i))

#foreach
for n in numbers:
  print(n)
```

#### Range function

`range(start num, up to num, increment by num)`

```python
range(5) #0,1,2,3,4
range(12,16) #12,13,14,15
range(0,10,2) #0,2,4,8
```

### List Comprehension | Single Line List Loop Through

When you only need to do one piece of logic in a loop

```python
numbers = [1,2,3,4,5]
squared = [x**2 for x in numbers]
print(squared)  # [2, 4, 9, 16, 25]
```

### Generators | Waits to be asked loop

sum(x**2 for x in range(5))

Like list comprehension but instead of looping through all at once 

it waits to be ask to do the *next* iteration

- Generates the next value on the fly rather than storing it all in memory
- Has a yield instead of return
- An instance of the generator can only be used once
    ```python
    myGenerator = createMyGenerator()  # myGenerator can only be used once
    """ """
    for v in createMyGenerator()  
    # createMyGenerator() creates a generator only for the scope of this for loop
    # can call the function again somewhere else
    ```
- Considered iterator (handles creating `__iter()__`)
```python
def createGenerator():
    myList = range(3)
    print("second")  # second
    for i in myList:
        yield i*i  # returns a generator
        print("test")  # prints after each print(i)
myGenerator = createGenerator()
for i in myGenerator:
    print(i)  # first
```

#### yield

returns a generator

yield makes it a function a generator

- When function is called no code is ran (prev, curr = 0,1 not ran when function called)
- waits for __next__ to be called on the generator object to start executing code
  - stops executing after yield ran
  - Order of execution:
        ```python
        #same as the class above
        def fib():
            prev, curr = 0,1
            while True:
                yield curr
                prev,curr = curr, prev + curr
        f = fib()
        list(islice(f, 0, 10)) #islice is an efficient split
        ```
      - f is idle, islice() is idle,
          list() will consume all of its arguments by
          calling next() on the islice() instance which will
          call next() on the f instance
      - yield curr produces value in curr and go idle again
      - islice will produce it because not past 10th value
      - list can add curr's value of 1
      - next iteration will pick up after yield until yield encountered again
      - repeats until list() asks islice() for the 11th value
      - islice() will raise a "StopIteration" exception
      - generator (f) will be garbage collected

```python
numbers = [1,2,3,4,5,6]
lazy_squares = (x * x for x in numbers)  
lazy_squares #<generator object <genexpr> at 0x10d1f5510>
next(lazy_squares) #1
list(lazy_squares) #[4,9,16,25,36]
return ", ".join(  #NO FUCKING CLUE WHAT THIS IS LOL
        f"{param}: {value}" #generator expression
        for param, value in attributes.items()
    )
```
### Generator Expression | Single Line Iterator Creation

Like list comprehension but `( )` instead of `[ ]`

Generator expressions are often used with functions like sum, max, and min
`sum(x**2 for x in range(5))`

```python
g = (x**2 for x in range(3))`

# Iterate
next(g)  # 0
for (v in g):
    print(v)  # 2, 4
next(g)  # StopIteration Error
```
- Hard example
    ```python
    numbers = [1,2,3,4,5,6]
    lazy_squares = (x * x for x in numbers)  
    lazy_squares #<generator object <genexpr> at 0x10d1f5510>
    next(lazy_squares) #1
    list(lazy_squares) #[4,9,16,25,36]
    return ", ".join(  #NO FUCKING CLUE WHAT THIS IS LOL
            f"{param}: {value}" #generator expression
            for param, value in attributes.items()
        )
    ```
- can never get the 1 again! Only can be used/iterated once
- Why use?:
  - Less memory, CPU, & lines of code
- When to use?:
  - Useful when you have a huge set of values you only need to read once
    ```python
    #Instead of this
    def something():
        result = []
        for ... in ...:
            result.append(x)
        return result
    #Do this
    def iter_something():
        for ... in ...:
            yield x
    something = list(iter_something()) #Only if you need a list structure
    ```
- print contents:
    `print(*(f"{s}" for s in ["bar", "test"]))`
  - * = unpacking operator (iterates(i.e. call __next__()) over iterable and assigns each value to a different variable)
    - "itertools" library assists a lot


## Strings

### Info

```python
# Length
len(myStr)

# substring [from start index:up to index]
"string"[0:2]  # st

# isX
isalpha() # if only letters and is not blank
isalnum() # if only letters and numbers and is not blank
isdecimal() # if only numbers and is not blank
isspace() # if only spaces, tabs, and new lines and is not blank
istitle() # if only words that begin with an uppercase letter followed by only lowercase

# startswith/endswith
'Hello world'.startswith('Hello') #returns true
```

### Manipulation

```python
# Concat
'Alice' + 'Bob'

# Multiply
'Alice' * 5

# type cast
myInt = int(myStr)
str(myInt)  # used for end user / goal to be readable
repr(myInt)  # used for debugging / goal to be unambiguous / will be wrapped in ' '
float(myStr)

# case manipulation
myStr.lower().upper() # lower case returns string object that upper() turns upper case
myStr.title() # title case

myStr.isupper() # has no lowercase and at least one upper
myStr.islower() # has no uppercase and at least one lower

# string to list of WORDS
## default separator = by space
"Hello, World".split()  # ["Hello," , "World"] 
"Hello, World".split(", ")  #["Hello" , "World"]

# string to list of CHARS
list('Hello') # ['H','e','l','l','o']

# escape characters:
\'
\"
\\

# insert tab 
\t = tab

# insert newline
\n = newline

# removing whitespace:
myStr.strip() #return a new string without any whitesapce characters at the beginning or end
myStr.lstrip()
myStr.rstrip()

# move text right, left, or center | justify
txt = "hello"
x = txt.rjust(20)
print(x,"world")
```


## Built-In Containers

- empty containers == false

### Indexes/Slices

Indexes enumerate the elements
Slices enumerate the spaces between the elements
```python
Index from rear:    -6  -5  -4  -3  -2  -1      a=[0,1,2,3,4,5]    a[1:]==[1,2,3,4,5]
Index from front:    0   1   2   3   4   5      len(a)==6          a[:5]==[0,1,2,3,4]
                   +---+---+---+---+---+---+    a[0]==0            a[:-2]==[0,1,2,3]
                   | a | b | c | d | e | f |    a[5]==5            a[1:2]==[1]
                   +---+---+---+---+---+---+    a[-1]==5           a[1:-1]==[1,2,3,4]
Slice from front:  :   1   2   3   4   5   :    a[-2]==4
Slice from rear:   :  -5  -4  -3  -2  -1   :
                                                b=a[:]
                                                b==[0,1,2,3,4,5] (shallow copy of a)
                                                b = []
        
                                                b = b.extend(a)
# slice [n:m] 
## [from start index:up to index
example[1:3] #[3.1415, True] SLICE

## SLICE TO END
example[1:] #[3.1415, True, None, 'last']

## SLICE FROM BEGINNING
example[:2] #[['hello', 'world'], 3.1415]

## SLICE to 1 before end
example[1:-1] #[3.1415, True, None]
```


### Lists / arrays

- Passes by reference when copied and when used as an argument
- Size is dynamic
- Creating for:
  - Stack or Queue? Use deque

```python
example = [['hello', 'world'], 3.1415, True, None, 'last']
```

#### Index

```python
example[0] #['hello', 'world']
example[-1] #'last'

"""
  n  [ 0, 1, 2, 3,   -1 ]
      |  |  |  |   |    |
  m   0  1  2  3 4/-1  5
"""

# slice [n:m] 
## [from start index:up to index
example[1:3] #[3.1415, True] SLICE

## SLICE TO END
example[1:] #[3.1415, True, None, 'last']

## SLICE FROM BEGINNING
example[:2] #[['hello', 'world'], 3.1415]

## SLICE to 1 before end
example[1:-1] #[3.1415, True, None]
```

#### Find

- Find Index:
  `example.index('last') # returns 4`

- Find Number of Occurrences:
`example.count('abc')  # of times 'abc' occurs in list`

#### In/Not In

```python
'chris' in ['hello', 'world'] #false
'chris' not in ['hello', 'world'] #true

# with error throwing
assert 'chris' in ['hello','world'] #assertion error thrown
assert 'chris' not in ['hello','world'] #nothing returned
```

#### Print List

```python
print(*arr) # ['hello', 'world'] 3.1415 True None last
# same as print(' '.join(map(str, arr)))
print(arr) # [['hello', 'world'], 3.1415, True, None, 'last']
```

#### Length

`len(examples) #5`

#### Concat | Append

```python
list3 = list1 + list2
list1 += list2
list1.append('at the end')
## if a list is passed it will add the list into a single index (creating a 2D list)

# concat per element (separated)
list1.extend(list2)
list1.extend('chris') [...,'c','h','r','i','s']
## adds each element individually
## goes into lists to add each element
```

#### Insert

`list1.insert(-1, 'before last')` 
- O(n) operation INEFFICIENT

#### Replace

all values in slice range replaced

list1[1:1] = ['hello', 'world']
list1[1:2] = ['Hello,', 'World']

#### Delete | Pop

```python
# delete, no return
del example[0]  # can also delete variables

# delete, return value deleted
example.pop()  # last item (top of stack)
example.pop(0)  # first item
```

#### Remove by value

`example.remove('hello')`
- throws ValueError if value not found

#### Multiple Assignment

```python
cat = ['fat', 'orange']
size, color = cat
# SAME AS size = cat[0]; color = cat[1]
# size = cat[0]
# color = cat[1]
```

#### Sort

`spam.sort() #cant use on lists with different types inside`

- Alphabetical:
  `spam.sort(key=str.lower) #uppercase and lowercase separate in ascii`
- Reverse / DESC:
  `spam.sort(reverse=True)`

#### Copy

##### Copy by Value

- shallow: 1D list
- deep: 2D list
- !if the list has a list inside use deepcopy
- python 3: foo = bar.copy()

```python
import copy
spam = [...]
cheese = copy.copy(spam)
cheese = copy.deepcopy(spam)
#OR FASTEST SHALLOW (w/o DEEP)
cheese = spam[:]
#OR FASTEST w/ DEEP
cheese = []
cheese.extend(spam)
# will not keep structure of embedded lists
```

##### Copy by Reference:

`a = b`

#### List to String

`', '.join(myCat) #string of list vals joined by ,`
or
`string = *myCat`

#### String to List

```python
# by word
text.split()

# by line
text.split('\n') #list of entries divided at every \n
```

#### List Comprehension

List Expression

```python
newlist = [x**2 for x in fruits if "a" in x]
# [ (expression_on_item) for (item) in (iterable) if (condition)]

# shorthand for
for x in fruits:
  if "a" in x:
    newlist.append(x**2)
```

- Map / apply function to each element in list:
    map(func, list) 
    - returns map object with results
    - turn into list: list(map(...))

- Filter / test function to each element in list:
    filter(func, list)
    - returns filter object with elements that returned true from applying func to
    - turn into list: list(filter(...))

- Reduce / combine function to each pair of elements in list and return one value:
    from functools import reduce
    reduce(func, list)
    multiply=reduce(lambda a,b:a*b,seq)

### Tuples / const arrays

immutable lists (no add or remove)

`eggs = ('hello', 42, 0.5)`

- more memory efficient than lists
- slight higher time efficiency than lists
- Convert:
    tuple(['cat', 'dog', 45])
    list(('cat', 'dog', 5))
    tuple('hello') #('h','e','l','l','o')
- max()
  - requires all values to be same data type
  - if int, max int
  - if string, string at max index
- min()

### Sets / hash table

Random order, no duplicates list

`thisSet = {"apple", "banana", "cherry"}`

- immutable, can add and remove only
  - `.add()`
  - `.remove()`
- only primitive data types and sets can be added

- define empty set
  - `x = set()`
- check if in set
  - `inSet = True if x in mySet else False`
- append to *current* set
  - `set1.update(set2)`
- union into *new* set
  - `set3 = set1.union(set2)`

### Dictionaries / associative arrays

- no duplicate keys
  - duplicate keys will update the value
- order doesnt matter for determining equality
- Python 3.7 > dicts are ordered
- Python 3.6 < unordered

```python
myCat = {'size': 'fat', 'color': 'gray', 'disposition': 'loud'}
print(myCat['size']) # 'fat'
```

- `.keys()` #tuple of k returned
- `.values()` #tuple of v returned
- `.items()` #tuple of k & v returned

- Foreach loop
    ```python
    for k, v in spam.items():
        print('Key: ' + k + ' Value: ' + str(v))
    ```
- In ?
    'color' in myCat.keys() #True
    'gray' in myCat.values() #True
- Key In ? w/ no return
    assert 1 in {1: 'foo'} #returns nothing
    assert 'foo' in {1: 'foo'} #assertion error thrown
- Get value
    myCat.get('name', 'cat doesn't have a name')
    1st param: key to get value from
    2nd param: (optional) value to return if key isnt found
- Setdefault / check if key exists and set value if not
    myCat.setdefault('name', 'sam')
    Checks if `name` key exists and if not create it and set it to `sam`
    Returns the key's value
- Pretty Printing 
  - Prints the contents of a dictionary better
    ```python
    import pprint
    pprint.pprint(myCat) #prints
    pprint.pformat(myCat) #returns a string
    ```
- Dict comprehension | Single Line Loop
  - *Dict expression*
  - `{x: x for x in numbers}`
- Zip | Create Dict from 2 Lists
    ```python
    name = [...]
    address = [...]
    mapped = dict(zip(name, address))
    #{"name": "address", "name":...}
    ```
- Combine dictionaries
  - new key-value pairs will be added
  - overlapping keys will be updated
  - `dict1.update(dict2)`

### Collections

like the built in containers but w/ added stuff
    
- namedtuple()
  - factory function for creating tuple subclasses with named fields
    
- deque
  - list-like container with fast appends and pops on either end
    
- ChainMap
  - dict-like class for creating a single view of multiple mappings
    
- Counter
  - dict subclass for counting hashable objects
    
- OrderedDict (not needed in Python 3.7)
  - dict subclass that remembers the order entries were added
    
- defaultdict
  - dict subclass that calls a factory function to supply missing values

- UserDict
  - wrapper around dictionary objects for easier dict subclassing
    
- UserList
  - wrapper around list objects for easier list subclassing
    
- UserString
  - wrapper around string objects for easier string subclassing

## Functions

```python
def hello():
    print('Hello')

hello()
```
- Typing
  - void 
    - functions return None (null)
  - no method overloading in python
    - (same method name with different types)
  - type enforcement 
    - Python 3.5 >
      - `def multiply(a: int, b: int) -> int:`
    - Python 3.5 <
      - checked with runtime function type()
- *FUNCTIONS ARE OBJECTS*
  - functions can be stored in variables
    - allows to pass to other functions
    ```python
    def my_func():
        print("hey")
    sayHey = my_func  # no `()` means func wont execute, but store in var
    sayHey()
    ```
- Function **nesting** is possible (function defined inside of function)
  - inner function cant be called from outside of outer function
  - inner function can be returned
- Custom Function **Documentation**
    ```python
    def my_func(my_args):
        '''These are the docs'''
        pass # do nothing
    print(my_func.__doc__)  # Output: These are the docs
    ```

### Lambdas / inline functions

```python
add = lambda a,b: a+b
print(add(4,5)) #Output: 9
```

- anonymous function / function w/o name
- infinite parameters
- one expression
- auto returns function object (can store in variable)


### Decorators

<https://stackoverflow.com/questions/5929107/decorators-with-parameters>
<https://www.google.com/search?client=firefox-b-1-d&q=decorator+with+arguments>
<https://www.geeksforgeeks.org/decorators-with-parameters-in-python/>
<https://www.youtube.com/watch?v=MjHpMCIvwsY>
  
- Allow you to change the behavior of a function 
  - without modifying the function
  - run the same code on multiple functions
    - add logging
    - test performance
    - perform caching
    - verify permissions
- How?: its a func that takes a func as a param and calls it in a nested function with code before and after the call potentially
    ```python
    def my_decorator_func(func):
        def wrapper_func(*args, **kwargs):
            # Do something before the function.
            func()
            # Do something after the function.
        return wrapper_func

    @my_decorator_func
    def execute_inside_wrapper():
        pass
    ```
- Example
    ```python
    @mydeco
    def add(a,b):
        return a+b
    
    add(2,2)
    # actually calling mydeco(add)
    ```
- Arguments get passed to the wrapper function inside the `@mydeco` function



## Arguments

### Positional Arguments

*Order matters* when passed positionally

```python
def quadratic(a, b, c):
    x1 = -b / (2*a)
    x2 = sqrt(b**2 - 4*a*c) / (2*a)
    return (x1 + x2), (x1 - x2)

quadratic(31, 93, 62)  # passed POSITIONALLY
```

- Only allow positional args (no keyword args)
    `f(x,y, /)`
  - python 3.8 >
  - left side of `/` can only be defined by positional args
- Unpack list to pass multiple positional args at once
    ```python
    def product(n1, n2):
        #...

    product(*numbers)
    # same as product(numbers[0], numbers[1])
    ```

### Keyword Arguments

Specify parameter name when passing

- *Order doesnt matter* when passed by name / keyword

- Unpack dict to pass multiple keyword args at once
    ```python
    items = {'name': "Trey", 'website': "http://treyhunner.com", 'color': "purple"}
    format_attributes(**items)
    ```
- Required keyword arguments:
  - Capture all positional arguments so the rest of the arguments have to be keywords
    ```python 
    def join(*iterables, joiner): 
        #...
    join(5,2,3)  # error because joiner not passed
    join(5,2,3, joiner=",")

    # iterables catches all positional args 
    # so "joiner" must be defined as keyword arg due to no default value
    ```
- Only allow keyword args (no positional args)
    `def person(*, name, dateOfBirth):`
  - `*` as a parameter
  - right side of * can only be defined by keyword args
- Use both keywords and positional args
    `def foo(a, b, /, *, c, d=5):`
    `foo(1,2,c=3) OR foo(1,2,c=3,d=4)`
  - left side of `/` = forced positional args
  - right side of `*` = forced keyword args
- inspect
  - `get_signature` to see how functions labels args

## Parameters

### Optional Parameters | Default parameters

Optional parameters to pass to the function call

`def print(*strings, sep=' '):  # sep is optional`

### *args | Pack all Positional Arguments into One Parameter

```python
# all positional keywords stored in numbers as tuple
def product(*numbers, initial=1):
    total = initial
    for n in numbers:
        total *= n
    return total
```

### **kwargs | Pack all Undefined Keyword Arguments into One Parameter
     
```python
def sum(*numbers, **options):
```

## Classes

```python
class fib:
    myVar = "test"  # property / class variable
    def __init__(self):  # constructor
        self.prev = 0  # instance variable
        self.curr = 1
    def __del__(self):  # destructors (called when del myObj)
        pass
    def __iter__(self):  # makes it an iterable
        return self
    def __next__(self):  # makes it usable iterator
        value = self.curr
        self.curr += self.prev
        self.prev = value
        return value
f = fib()
list(islice(f,0,10)) #[1, 1, 2, 3, 5, 8, 13, 21, 34, 55]
```

### Method Types

#### Instance Method

Gets & Sets instance variables / object state

Belongs to the instance

- i.e. member function
- `self` required as first param of every instance method
  - (instance of class) passed automatically as first argument

#### Class Method

Get & Set class state

Belongs to the class

#### Static Method

Belongs to the class but doesnt alter the state of the class

### Access Modifiers

- Public
  - automatic
- Private
  - `__` prefix on member name
- Protected
  - `_` prefix on function name
  - like private, but can be accessed by children

### Function Modifiers

- `@classmethod` decorator
  - implicitly receives the class as an argument
  - When to use?
    - Factory methods (similar to constructor) that will return class objects
- `@staticmethod` decorator
  - Does not implicitly receive the class as an argument
  - Can not access or modify the class state
  - When to use?:
    - Utility Functions
    - Makes sense for the function to be in the class

### Inheritance

```python
class Teacher(Person):  # Teacher extends Person
  def __init__(self, name, age, subject):
    self.subject = subject
    Person.__init__(self,name, age)  # calls the parent constructor to set properties
```

## Objects

- Test if callable:
  - `callable(object)`
  - True if object has `__call__()` method
  - Classes are callable by default

## Iteration

```python
for x in myList:
    # ...
```

### Iterable vs Iterator

- Iterable = overall ds can iterated with `__iter__()` / has iterator 
- Iterator = object that produces the next value when you call its `__next()__` method

### Iterable

`myList` is the iterable, an object that has the iterator protocol `__iter__()`

- `__iter__()` returns an iterator
  - an object with `__next()__`
  - could just return self if self has `__next__()`
- ex. string, list, tuple, set, range(), file
- values stored in memory

### Iterator

Any object that has a `__next__()` method

1. Gets an iterator of `myList`
   1. Call `iter(myList)`
   2. Returns object with a `__next__()` method
2. Use the iterator to loop over items
   1. Keep calling `__next__()`
   2. which returns result into `x`
      - if a `StopIteration` is raised from within `__next__()`, it means there are no more values in the iterator and the loop is exited

### Iterable Functions

- Map | apply function to each element in list
  - `map(func, list)`
  - returns map object with results
  - convert to list `list(map(...))`
- Filter | applies function to each element of list that meets condition
  - `filter(func, list)`
  - returns filter object with elements that returned true
  - convert to list `list(filter(...))`
- Reduce | apply function to each pair of elements in list and return one value
    ```python
    from functools import reduce
    reduce(func, list)
    multiply=reduce(lambda a,b:a*b,seq)
    ```
- Zip | take 0 or more iterables and make an iterator of ith tuples
  - `zip(*iterables)`
  - and stops at the length of the shortest iterable
  - ex) iterable1[0] AND iterable2[0] stored in the 0th tuple
- All True?
  - `all(iterable)`
- Any True?
  - `any(iterable)`
  - Often used with generators on lists
    - `any(letter == 't' for letter in 'monty')  # True`
- Reverse Iterator
  - `reversed(seq)`
  - Prereqs
    - seq has a __reversed__()
    - OR
    - *Sequence Protocol* supported
  - __len__()
  - __getitem__()
  - w/ int args starting at 0
    - returns a reverse iterator

## Error Handling

```python
try:
    # Throw Exceptions
    if False:
        raise Exception("It's false")
    else if False && False:
        raise ValueError("Not proper value")
    # Catch Exceptions
    print(42/0)
    print("This will never print")
except ZeroDivisionError:  # catch
    print('cant divide by 0')
except:  # default
    print('Some error happened')
finally:  # always executes
    print('Always prints')

# ...

assert podBayDoorStatus == 'closed', 'The pod bay doors need to be closed.'
# AssertionError: The pod bay doors need to be closed.
```

- traceback errors 
  - `import traceback`

## Input

`myInput = input("Message to user: ")`

- Dynamic Input
    ```python
    catNames = []
    while True:
        name = input()
        catNames = catNames + [name]
        if name == "exit":
            break
    ```

## Context Managers

ensures that resources are returned after usage

### Using `With`

```python
with open("test.txt") as line:
    data = line.read()
# returns resources after with statement exits
```

### Creating from Scratch

- `__enter__()`
  - returns the resource that needs to be managed
- `__exit__()`
  - no return, performs cleanup

```python
class ContextManager():
    def __init__(self):
        print('init method called')
        
    def __enter__(self):
        print('enter method called')
        return self
    
    def __exit__(self, exc_type, exc_value, exc_traceback):
        print('exit method called')

with ContextManager() as manager:
    print('with statement block')
print("Last thing to be printed")
```

## Files

`import os`

### Handling files proper

```python
with open("test.txt") as line:
    data = line.read()
# OR
class FileManager():
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None
        
    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file
    
    def __exit__(self, exc_type, exc_value, exc_traceback):
        self.file.close()
        
with FileManager('test.txt', 'w') as f: # loading a fil
    f.write('Test')

print(f.closed)
```

- Open/read/write/close file:
    ```python
    # Open
    myFile = open(path, mode = r)
    myContents = myFile.read()
    readlines() # list of string values from file
    myFile.close()

    # Write
    open(path, w) # overrides original file contents
    # creates a new file if it doesnt exist
    write('test') 

    # Close
    myFile.close()

    # Append
    open(path, a) # append to the end of the file
    ```
- copy,move,rename,delete:
    `import shutil`
- safe delete:
    `import send2trash`
- Join file path
    `os.path.join('usr', 'bin', 'spam')`
- File size:
    `os.path.getsize(path)`
- Directory
  - Get current working directory
    `os.getcwd()`
  - Change current working directory
    `os.chdir`
  - Get files in dir:
      `os.listdir(path)`
  - Check if it exists:
      `os.path.exists(path)`
  - Check file exists:
      `os.path.isfile(path)`
  - Check dir exists:
    `os.path.isdir(path)`

## Standard Library | stl

[Standard Library](https://docs.python.org/3/library/)

- Modules written in C to give access to the system Python doesnt have
  - standardized solutions to common problems in programming
  - enhance portability by abstracting away platform-specifics into platform-neutral APIS

### Command Line arguments

```python
import sys
sys.argv[1]
```

### Random

```python
import random, sys, os, math
random.randint(1,10)
# OR
from random import * #from random import everything
randint(1,10) #didnt need to specify random. because of from
sys.exit()

# GET HELP
help(randint)
```

## 3rd Party Libraries

- Install
  - Windows:
    1. In the python directory, under scripts folder
    2. ./pip.exe install pyperclip
    - OR
    1. `python -m pip install pyperclip # may require elevation`
  - macOS:
    - `python3 -m pip install pyperclip`
  - linux:
    - `apt-get install python3-tk`
    - `python3 -m pip install pyperclip`

### Copy & Paste

```python
import pyperclip
pyperclip.copy('test')
pyperclip.paste()
```

### Save variables to hard drive

```python
import shelve
myFile = shelve.open('mydata')
cats = ['sophie', 'pooka', 'Simon']
myFile['cats'] = cats
myFile.close()
```

### matplotlib

`import matplotlib.pyplot as plt`

- wont show on wsl

### numpy

`import numpy as np`

### logging logs


### Asyncio | Concurrent Execution | Asynchronous I/O

[Distribute tasks via queues](https://docs.python.org/3/library/asyncio.html)

`import asyncio`
    
### Multiprocessing
    
[Process-based Parallelism](https://docs.python.org/3/library/multiprocessing.html)
    
`import multiprocessing`
    
- Spawns processes by 
  1. side-stepping the Global Interpreter Lock
     - *Global Interpreter Lock* assures CPython only has one thread execute Python bytecode
  2. using subprocesses instead of threads
        
- When to use:
  - for CPU heavy processes that dont benefit from threading
  - Programs that need more CPU

- How to:
  - create a process
    - `from multiprocessing import Process`
  - offer a convenient means of parallelizing the execution of a function across multiple input values
    - `from multiprocessing import Pool`
  - Threading
    - a thread is an execution context (all the info needed to execute / resume executing a stream of instructions)
    - two things appearing to be happening at once
      - but threads dont run at the same time
      - even if they are on different processors
    - When to use?:
      - Tasks that spend much of their time waiting for external events
      - NOT for CPU-bound problem
        - NOT for processes that require heavy CPU computation and spend little time waiting for external events might not run faster at all.
      - Want tasks to run simultaneously and not have to wait on each other i.e. CONCURRENCY
      - takes far less time to create & terminate a thread than to create a new processes
      - can share common data, they do not need to use inter-process communication
      - slower than context switching
    - Example:
        A web browser will need multiple threads
        1) Display the page
        2) Download files
        ...
        If you only had one thread, the web page could not display while the download is happening 
    - multiprocessing vs threading
      - A program running is called a process
      - A program can have multiple processes
      - A process can have multiple threads
    - Process vs Thread:
      - A process has data
      - A thread has a stack, registers, and the program counter
    - Subprocess
      - run & control other programs

## Security Considerations

[More info](https://docs.python.org/3/library/security_warnings.html)

- base64, cgi, hashlib, http.server, logging, multiprocessing, pickle
  random, shelve, ssl, subprocess, tempfile, xml, zipfile

## Virtual Environment
    
- Windows:
  1) `py -3 -m venv .venv`
  2) `.venv\scripts\activate`
  3) if "Activate.ps1...", change PowerShell execution policy to allow scripts to run
      1) Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
- macOS/Linux:
  1) `python3 -m venv .venv`
  2) `source .venv/bin/activate`
- VSCode
  - Prompted when a new virtual environment created:
    - "Set as default for your workspace folder?"
    - If yes, Environment automatically activated when you open a new terminal
  - **Set environment as python interpreter**

### Commands

- deactivate
    `$ deactivate`
