# Python

Python is an interpreted, Object oriented, scripting language

SO OBJECT ORIENTED, that everything is an object

Python follows Indentation to separate code blocks instead of flower brackets `{}`

## Additional Language Info

- high-level and general-purpose 
- dynamically typed programming language
- Object oriented
- modular oriented

- By default, python doesn't require any imports to run a python file.

## Create and execute a program

1. Open up a terminal/cmd
2. Create the program: nano/cat > nameProgram.py
3. Write the program and save it
4. run python file
   - `$ python <filename.py>` or `$ python3 <filename.py>`

## Basic Data Types

| Data Type | Description |
| --------- | ----------- |
| int | Integer values [0, 1, -2, 3] |
| float | Floating point values [0.1, 4.532, -5.092] |
| char | Characters [a, b, @, !, `] |
| str | Strings [abc, AbC, A@B, sd!, `asa] |
| bool | Boolean Values [True, False] |
| complex | Complex numbers [2+3j, 4-1j] |

## Keywords

- As of python3.8 there are 35 keywords

| Keyword | Description  | Category |
|---------- | ---------- | --------- | 
| True      | Boolean value for not False or 1 | Value Keyword|
| False     | Boolean Value for not True or 0 | Value Keyword |
| None      | No Value or null | Value keyword |
| and       | returns true if both (oprand) are true (other language && ) | Operator keyword |
| or        | returns true of either operands is true (other language || ) | Operator keyword |
| in        | returns true if word is in iterator | Operator keyword |
| is        | returns true if id of variables are same | Operator keyword |
| not       | returns opposite Boolean value | Operator Keyword |
| if | get into block if expression is true | conditional |
| elif | for more than 1 if checks | conditional |
| else | this block will be executed if condition is false | conditional |
| for | used for looping | iteration |
| while | used for looping | iteration |
| break | get out of loop | iteration | 
| continue | skip for specific condition | iteration |
| def | make user defined function | structure |
| class | make user defined classes | structure |
| lambda | make anonymous function | structure |
| with | execute code within context manager's scope | structure |
| as | alias for something | structure |
| pass | used for making empty structures(declaration) | structure |
| return | get value(s) from function, get out of function | returning keyword |
| yield | yields values instead of returning (are called generators) | returning keyword |
| import | import libraries/modules/packages | import |
| from | import specific function/classes from modules/packages | import |
| try | this block will be tried to get executed | exception handling |
| except | is any exception/error has occured it'll be executed | exception handling |
| finally | It'll be executed no matter exception occurs or not | exception handling | 
| raise | throws any specific error/exception | exception handling |
| assert | throws an AssertionError if condition is false | exception handling |
| async | used to define asynchronous functions/co-routines | asynchronous programming |
| await | used to specify a point when control is taken back | asynchronous programming |
| del | deletes/unsets any user defined data |  variable handling |
| global | used to access variables defined outside of function | variable handling |
| nonlocal | modify variables from different scopes | variable handling |

## Operators

| Operator | Description |
|-|-|
|  ( )	|  grouping parenthesis, function call, tuple declaration |
|  [ ]	|  array indexing, also declaring lists etc.|
|  !	|    relational not, complement, ! yields true or false |
|  ~   | 	bitwise not, ones complement, ~a |
| \-   |	unary minus, - a |
|  \+   | 	unary plus,  + a |
|  \*   |	multiply, a * b |
|  /   	| divide, a / b |
|  %    |	modulo, a % b |
|  \+   | 	add, a + b |
| \-   | 	subtract, a - b |
| <<   | shift left,  left operand is shifted left by right operand bits (multiply by 2) |
| \>>   |	shift right, left operand is shifted right by right operand bits (divide by 2) |
 | <    |	less than, result is true or false,  a %lt; b
| <=   |	less than or equal, result is true or false,  a <= b
| \>    |	greater than, result is true or false,  a > b
| \>=   |	greater than or equal, result is true or false, a >= b
|  ==   |	equal, result is true or false,  a == b
| !=  | 	not equal, result is true or false,  a != b
|  & | bitwise and,  a & b
| ^ | bitwise exclusive or XOR,  a ^ b
| \| | bitwise or,  a | b
|  &&, and | relational and, result is true or false,  a < b && c >= d
| \|\|, or | relational or, result is true or false,  a < b \|\| c >= d |
| =  | store or assignment |
|  += | add and store |
|  -=  | subtract and store |
|  *= | multiply and store |
|  /= | divide and store|
|  %= | modulo and store|
| <<= | shift left and store|
|  \>>= | shift right and store|
|  &= | bitwise and and store|
|  ^= | bitwise exclusive or and store|
|  \|= | bitwise or and store|
|  , | separator as in   ( y=x,z=++x )|

## Conditional branching

```python
    if condition:
        pass
    elif condition2:
        pass
    else:
        pass
```

## Loops

 Python has two primitive loop commands:
1. while loops
2. for loops

### While loop

- With the `while` loop we can execute a set of statements as long as a condition is true.
- Example: Print i as long as i is less than 6
```python
i = 1
while i < 6:
  print(i)
  i += 1
```
- The while loop requires relevant variables to be ready, in this example we need to define an indexing variable, i, which we set to 1.
- With the `break` statement we can stop the loop even if the while condition is true
- With the continue statement we can stop the current iteration, and continue with the next.

- With the else statement we can run a block of code once when the condition no longer is true.

### For loop

- A for loop is used for iterating over a sequence (that is either a list, a tuple, a dictionary, a set, or a string).

- This is less like the for keyword in other programming languages, and works more like an iterator method as found in other object-orientated programming languages.

- With the for loop we can execute a set of statements, once for each item in a list, tuple, set etc.
```python
fruits = ["apple", "banana", "cherry"]
for x in fruits:
  print(x)
```
- The for loop does not require an indexing variable to set beforehand.
- To loop through a set of code a specified number of times, we can use the range() function.
- The range() function returns a sequence of numbers, starting from 0 by default, and increments by 1 (by default), and ends at a specified number.
- The range() function defaults to increment the sequence by 1, however it is possible to specify the increment value by adding a third parameter: range(2, 30, 3).
- The else keyword in a for loop specifies a block of code to be executed when the loop is finished.
A nested loop is a loop inside a loop.

- The "inner loop" will be executed one time for each iteration of the "outer loop":

```python
adj = ["red", "big", "tasty"]
fruits = ["apple", "banana", "cherry"]

for x in adj:
  for y in fruits:
    print(x, y)
```
- for loops cannot be empty, but if you for some reason have a for loop with no content, put in the pass statement to avoid getting an error.

```python
for x in [0, 1, 2]:
  pass
```

## Functions

```python
def function_name():
    return

function_name()
```

- We need not to specify the return type of the function.
- Functions by default return `None` 
- We can return any datatype.
