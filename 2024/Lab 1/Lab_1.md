# Week 1 Lab
## Overview
This week's lab session will cover a review of Python fundamentals and a basic introduction to the NumPy library.

## Prerequisites
before we dive into code, make sure you install the following tools:
- Python
- Vscode, Pycharm, Jupyter notebook (or any text editor or ide you prefer, i will use vscode with jupyter notebook extension)

## Libraries
- Numpy
- OpenCV
you can install these 2 libraries by opening your terminal and write `pip install numpy` and `pip install opencv-python` to install respectively.

## Python basics
- Data types
- Value type variables and refernce type variables.
- Condition and ternary condition
- While loop and for loop
- Functions

## Problems
- FuzzBuzz
- Prefix Sum

## Numpy basics
- Create numpy array
  - array of number 
  - array of zeros
  - array of random
- Convert list into array
- Numpy array datatypes
- Access numpy array
- Arithmetic operation
- Logical operation

## Virtual Environment
To ensure a clean and organized development environment, it's essential to create a virtual environment for each project. This isolated space keeps your project's dependencies separate from other projects and the system-wide Python installation, preventing conflicts and version issues. once you created virtual environment,You can directly install the libraries your project needs one by one using `pip install <library_name>` within the activated environment. Alternatively, if your project has a requirements.txt file, you can install all listed libraries at once by running `pip install -r requirements.txt` within the activated environment.
<br/>

> **Note:**
> Next instruction for windows only, it may differ on other OS.

<br/>

## Create virtual environment:
- open you terminal
- python `-m venv name_of_project`
- if you use cmd run the following
  - `name_of_project/Scripts/activate.bat`
  - or
  - `name_of_project/Scripts/activate`
- if you use bash run the following
  - `source name_of_project/Scripts/activate`

> **Note:**
> venv is working from python version 3.3 or above
> you should see the name of the project appear above folder address in your terminal.

## Create requirements.txt
After installing libraries it's good practice to make and update a requirements file to make the installation process easier. 
### To creat `requirements.txt`
- open your terminal
- write `pip freeze > requirements.txt`
requirements should appear with all your libraries and modules. 
### To install libraries from requirements file
- open your terminal
- write `pip install -r requirements.txt`


## Definations
Some defination before we get start:
  - **Value type** means the data that is stored in the variable is copied, not it's address.
    - For example: 
      ```python
      x = 10
      y = x
      y = 20
      print(f"X: {x}, Y: {y}")
      # Output X: 10, Y: 20
      ```  
      Here value of `x` which is `10` is copied, then we change the value of `y` which won't effect value of `x`.
      > **Note:**
      > type of x is int which is value type
  - **Referrence type** means the address of the data that is stored in the variable is copied.
    - For example:
      ```python
      List_1 = [1,2,3]
      List_2 = List_1
      List_2.append(5)
      print(f"List 1: {List_1}, List 2: {List_2}")
      # Output List 1: [1,2,3,5], List 2: [1,2,3,5]
      ```
      Here `List_1` copied it's address not the value, this means when you change the structure of `List_2` will also change structure of `List_1`.
      > **Note:**
      > type of `List_1` is list which is refernce type
  - **Immutable** means once the object it created (program allocate memory to store data), its content (data) can't be changed. but if content changed or modified new memory address is allocated and the object will be assigend to it.
    - For example:
      ```python
      x = 1
      print(f"x is {x} and x address : {id(x)}") 
      y = x 
      print(f"y is {y} and y address : {id(y)}") 
      x = 2
      print(f"x is {x} and x address : {id(x)}") 
      print(f"y is {y} and y address : {id(y)}") 
      """
      Output:
      x is 1 and x address : 140723451024168
      y is 1 and y address : 140723451024168
      x is 2 and x address : 140723451024200
      y is 1 and y address : 140723451024168
      """
      ```
      Here `x` address is change once we modify the content with any operation (add, sub, or even assign variable to new value).
      > **Note:**
      > int is immutable
  - **Mutable** is the exact opposite of **Immutable**, changing or modifing content of the variable is allowed and address of the variable doesn't change.
    - For example:
      ```python
      x = [1,2,3,4,5]
      print(f"x is {x} and x address : {id(x)}") 
      y = x 
      print(f"y is {y} and y address : {id(y)}") 
      x[0] = 100
      print(f"x is {x} and x address : {id(x)}") 
      print(f"y is {y} and y address : {id(y)}") 
      """
      OutPut:
      x is [1, 2, 3, 4, 5] and x address : 1647832812928
      y is [1, 2, 3, 4, 5] and y address : 1647832812928
      x is [100, 2, 3, 4, 5] and x address : 1647832812928
      y is [100, 2, 3, 4, 5] and y address : 1647832812928
      ```
      Even after modifing content of `x`, `x`'s address doesn't.
      > **Note:**
      > List is mutable

----

## Python Basics

### Variables
Variables is a user defined name that stores data in memory. This data can range from 
### Int
Int is a value type and an immutable datatype. It's used to store numbers of size 32-bit.
#### How to store int in a variable