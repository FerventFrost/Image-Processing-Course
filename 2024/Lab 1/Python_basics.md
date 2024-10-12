# Python
Python is a dynamic type language that depend on interperter to provide types for it. Python like any other moderen language has datatypes, variables, conditions, loops, functions, and classes (Although this isn't the most important feature in it). Before get started with python please open README.md.

# Get Started
This lab will go through Datatypes, Variables, Conditions, Loops, and Functions in addition we will introduce some numpy basics.

## Datatypes
Python has 10 basic datatypes in total which are (int, float, string, boolean, list, set, tuple, dictionary, none, and objects).

### int
Let's start with the most beloved datatype int. Int stores integer numbers (whole number) and can be initialized by declear and assign number to a variable. for example:
`x = 5` or by `x = int()` first one interperter takes responsiblity for datatype and it come with some preformance draw backs. The other one developer is the one whom responsible for deciding the variable datatype.
<br/>
Int is value type and immutable which means:
- Value type means: any passing of a value between one variable to another will copy the value not the address. 
example:

```python
x = 5
y = x 
x = 7
print(y)
> 5
```
- Immutable means: any change of the variable will occupy new memory space and remove the previous one.
example:
```python
x = 5
print(id(x))
> 140736470995944
x = 7
print(id(x)) 
> 140736470995944
```
address of x changed as you see

### Float
Float stores real numbers and can be initialized by declear and assign number to a variable. for example:
`x = 5.3` or by `x = float()` 

<br>
Float is value type and immutable which means:

- Value type example:

```python
x = 5.0
y = x 
x = 7.0
print(y)
> 5.0
```
- Immutable example:

```python
x = 5.0
print(id(x))
> 2382438668464
x = 7.0
print(id(x))
> 2382438677104
```
address of x changed as you see

### Boolean
Boolean store 2 values which are (True and False). it can be initialized by declear and assign number to a variable. for example:
`x = True` or by `x = bool()` 

<br>
Boolean is a value type and immutable

- Value type example:
```python
x = True
y = x
x = False
print(y)
> True
```

- Immutable example:
```python
x = True
print(id(x))
> 140723449494376
y = x
print(id(y))
> 140723449494376
x = False
print(id(x))
> 140723449494408
```

### String
String is a data type that holds words. it can be initialized by declear and assign number to a variable. for example:
`x = "Hello"` or by `x = str()` 

<br>
String is reference type and immutable. but because of the immutable behaviour of Strings, each update to the variable it locate a new address.

### List
List is a data structure that holds a collection of any data type and can hold multiple datatype like int and string. it can be initialized by declear and assign number to it. for eacmple:
`x = [1,"hello"]` or by `x = list()`

<br>
List is a refernece and mutable type. that means that the type of data that is pass between 2 variable is the address not a copy. to fix this .copy() must be attached to the passed variable. 

- refernece example:
```python 
x = [1,2,3,4,5]
y = x 
x[0] = 100
print(y)
> [100, 2, 3, 4, 5]
```

- Mutable example:
```python
x = [1,2,3,4,5]
print(id(x))
> 1647832812928
y = x
print(id(y))
> 1647832812928
```

### Set
Set is a data structre that hold collection of unique data. it can be initalized by the by the clearing would assign variables declaring or assign values to it. Example:
`x = {1,2,3}` or by `x = set()`

<br>
Set is a refernece and mutable type.

### Tuple
Tuple is a data structure that hold data in a pair manner. it can be initalized by the by the clearing would assign variables declaring or assign values to it. Example:
`x = (1,2,3)` or by `x = tuple()`

<br>
Tuple is a reference and immutable type.

### Dictionaries
Dictionaries is a data structure that holds data in a key value manner. it can be initalized by the by the clearing would assign variables declaring or assign values to it. Example:
`x = {'a' : 1}` or by `x = dict()`

<br>
Dictionary is a reference and mutable type.

### None and objects
Lastly is None and objects. None is a value type that indicates nothing. object is a reference type that indicates an object. Example:
`x = None` and `x = object()`

## Condition
Conditions is a branches that is activated based on a condition. if the condition is true the branch is activated, else the is ignored.

### If
if condition branch is activated if the condition is true. example:
```python
if True:
  print("Hello world 1")
> Hello world 1

if False:
  print("Hello world 2")
> 
```

### else
else branch is activated if the `if` statement is false.

```python
if False:
  print("Hello world 1")
else:
  print("Hello world 2")
> Hello world 2
```
### else if
else if branch is activated if the `if` statment is false and else if condition is true.

```python
if False:
  print("Hello world 1")
elif True:
  print("Hello world 2")
> Hello world 2
```

### Ternary condition
condition is a one liner with if and else.

```python
message = "x is greater than 5 " if False else " x is not greater than 5"
print(message)
> x is not greater than 5
```

## Loops
loops is a block of statement that runs multiple time for of the user input number. example:

```python
for i in range(5):
  print(i, end="-")
> 0-1-2-3-4
```

## Functions
functions is a block of code that can be called at any time and anywhere. example:

```python 
def greet():
    print("Hello, world!")

greet()
> Hello, world!
```

## Numpy basics
To use numpy install numpy first then import it. `import numpy`

### Create numpy array
You can create numpy array from an existing list.
```python
import numpy
numpy.array([1,2,3,4,5])
```

You can also create an empty array.
```python
import numpy
# for 1-d
numpy.zeros(3)
> [0. 0. 0.]

# for 2-d
numpy.zeros((2,2))
> [[0. 0.]
   [0. 0.]]
```

Random array
```python 
import numpy

numpy.random.rand(2,2)
> [[0.2584 0.88934]
   [0.221455 0.111]]

numpy.random.randint(0,256,(2,2))
> [[152 111]
   [72 90]]
```

### numpy array dtype
you can specify data type using `dype` parameter.

```python
import numpy

numpy.array([1,22,3,5], dtype=numpy.float32)
> [1. 22. 3. 5.]
```

### Access elements in numpy array
you can access elements like accessing element in a list. access 1-d array.

```python
import numpy

arr = numpy.array([1,22,3,5])
# access element
arr[0]
> 1

# access sub-array
arr[1:3]
> [22 3]
```

access 2-d array
```python
import numpy

arr = numpy.array([[3,4,5],
                  [6,7,8],
                  [9,10,11]])

# access element
arr[1,2]
> 8

# access sub-array
arr[1, 0:2]
> [6 7]

# access 2 rows
arr[0:2]
> [3 4 5]
  [6 7 8]

# access 1 column
arr[1, :]
> [4 7 10]
```

### Arithmetic Operations
Any operation applied on a numpy array is applied on the whole array. example:

```python
import numpy
newArr = numpy.array([1,2,3,4])
newArr = newArr + 20
print(newArr)
> [21 22 23 24]

newArr = numpy.array([1,2,3,4])
newArr = newArr * 20
print(newArr)
> [20 40 60 80]
```

### Logic Operations
you can apply logical operation in numpy array in the same manner as arithmetic operations. example:
```python
import numpy
newArr = numpy.array([1,5,10,20])
newArr = newArr > 5
print(newArr)
> [False False True True]
```