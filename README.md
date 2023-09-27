- [1](#1)
  - [input()](#input)
  - [type 함수](#type-함수)
    - [cannot convert {type} to {type}](#cannot-convert-type-to-type)
  - [isinstance 함수](#isinstance-함수)
    - [isinstance](#isinstance)
  - [{str} \* {int}](#str--int)
- [2](#2)
  - [List](#list)
    - [Slicing](#slicing)
    - [Append](#append)
    - [Packing \& Unpacking](#packing--unpacking)
  - [Mutable \& Immutable data types](#mutable--immutable-data-types)
    - ['==' and 'is'](#-and-is)
    - [Lists](#lists)
- [3](#3)
  - [string](#string)
    - [f-string](#f-string)
    - [r-string](#r-string)
    - [repr()](#repr)
  - [Static memory allocation](#static-memory-allocation)
  - [range()](#range)
  - [list vs str](#list-vs-str)
  - [enumerate](#enumerate)
  - [iteretor and generator](#iteretor-and-generator)
    - [iter()](#iter)
    - [generator](#generator)
- [4](#4)
  - [Recursive functions](#recursive-functions)
    - [Memoization (top-down approach)](#memoization-top-down-approach)
    - [Tabulation (bottom-up approach)](#tabulation-bottom-up-approach)
  - [Arguments](#arguments)
    - [Keyword arguments](#keyword-arguments)
    - [Default arguments](#default-arguments)
    - [Variable-length arguments (Unpacking)](#variable-length-arguments-unpacking)
    - [Keyword variable-length arguments](#keyword-variable-length-arguments)
    - [\*args + \*\*kwargs](#args--kwargs)
  - [yield](#yield)
  - [Type annotation](#type-annotation)
- [5](#5)
  - [String](#string-1)
    - [String manipulations](#string-manipulations)
    - [File](#file)
    - [Formatting and Literals](#formatting-and-literals)
- [6](#6)
  - [conda](#conda)

---

# 1

## input()

+ takes input as str
```python
n = int(input('type something...'))
```

+ 

## type 함수

```python
print(type(n))
# <class 'str'>
# <class 'float'>
```

### cannot convert {type} to {type}

+ str to float `X`

## isinstance 함수

```python
isinstance(a, int)
# True
# False
```

### isinstance

+ int is bool?

```python
n = 1

isinstance(n, bool)

# False
```

+ bool is int?

```python
n = True

isinstance(n, int)

# True
```

## {str} * {int}

```python
a = '10'
print(a * 3)

# 101010
```

# 2

## List

```python
colors = ["red", "yellow", "green"]

print(colors)
# ['red', 'yellow', 'green']

print(type(colors))
# <class 'list'>

print(type(colors[0]))
# <class 'str'>

print(len(colors))
# 3
```

### Slicing

```python
cities = ["Seoul", "Busan", "Asan", "Cheonan", "Jeju"]

print(cities[::2])
# stride 2

print(cities[0:5:2])
# index 0 to index 4, stride 2
# ['Seoul', 'Asan', 'Jeju']

print(cities[::-1])
# backwards
# ['Jeju', 'Cheonan', 'Asan', 'Busan', 'Seoul']
```

### Append

+ .append() method

```python
colors.append('black')
```

>  + append returns nothing
>
>  ```python
>  a = fruits.append('grape')
>  print(a)
>  # None
>  ```

+ **\+**

```python
colors = colors + ['blue']
```

### Packing & Unpacking

+ better to use unpacking than list indexing

```python
colors = ['red', 'yellow', 'green']

r, g, b = colors
print('Unpacked:', r, g, b)
# red yellow green

print('Unpacked with *:', *colors)
# red yellow green

packed = r, g, b
print(packed)
# ('red', 'yellow', 'green')
print(type(packed))
# <class 'tuple'>
```

+ Unpacking

```python
oldest, second_oldest, *others = car_ages_descending
print(oldest, second_oldest, others)

# 20 19 [15, 9, 8, 7, 6, 4, 1, 0]
```

```python
oldest, *others, youngest = car_ages_descending
print(oldest, youngest, others)

# 20 19 [15, 9, 8, 7, 6, 4, 1, 0]
```

## Mutable & Immutable data types

|Mutable|Immutable|
|---|---|
list, dictionary, set, user-defined classes|int, float, decimal, bool, string, tuple, range

+ single-item data types, such as integers, floats, complex numbers, and Booleans, are always immutable

### '==' and 'is'

```python
list1 = [1, 2, 3]
list2 = list1[0:3]
print(list1 is list2)
print(id(list1), id(list2))

# False
# 140199141214016 140200780884032
```

```python
tuple2 = tuple1[0:3]
print(tuple1 is tuple2)
print(id(tuple1), id(tuple2))

# True
# 140200780916608 140200780916608
```

```python
a = 1
b = 100000

print(a is 1)
print(b is 100000)

# True
# False
```

### Lists

+ List is an object that can change themselves after we instantiate them

```python
list1 = ['hi','bye',52,True,2.3]
print(id(list1), list1)

list1[1]='see u later'
print(id(list1), list1)

# 140200218474240 ['hi', 'bye', 52, True, 2.3]
# 140200218474240 ['hi', 'see u later', 52, True, 2.3]
```

+ Integer cannot change themselves after we initialize them

```python
integer1 = 1000
print(id(integer1), integer1)

integer1 += 1000
print(id(integer1), integer1)

# 140200771415536 1000
# 140200771415984 2000
```

+ That is why we can use method to manipulate list, like append()

```python
list2 = [1, 2, 3]
print(id(list2), list2)

list2.append(4) # Not list2 = list2.append(4)!!
print(id(list2), list2)

# 140200781017216 [1, 2, 3]
# 140200781017216 [1, 2, 3, 4]
```

# 3

## string

### f-string

```python
print(f"{affiliation}에 소속된 {name}님은 {age}세로 판명되어 서비스 이용이 가능합니다."
```

### r-string

+ in json, html etc.

```python
print(f"String is {string}")
print(r"String is {string}")

# String is Hello World
# String is {string}
```

### repr()

```python
print(string)
print(repr(string))

# Hello World
# 'Hello World'
```

+ repr() to int and string

```python
print(f"{repr(int_value)} = {repr(str_value)}")

# 5 = '5'
```

## Static memory allocation

```python
a = 1000
b = 1000
print(a == b)
print(a is b)
print(id(a) == id(b))

c = 1
d = 1
print(c == d)
print(c is d)
print(id(c) == id(d))

# True
# False
# False
# True
# True
# True
```

## range()

```python
for num in range(10, 1, -1):
    print(num)

# backwards

# 10
# 9
# 8
# 7
# 6
# 5
# 4
# 3
# 2
```

+ same as `range(2, 11)[::-1]`:

## list vs str

```python
list_var = ['h', 'e', 'l', 'l', 'o']
str_var = 'hello'

print('h' in list_var)
# True
print('he' in list_var)
# False
print('h' in str_var)
# True
print('he' in str_var)
# True
```

## enumerate

+ lazy generator

```python
for i, flavor in enumerate(flavor_list):
    print(f"{i + 1}: {flavor}")

# 1: vanilla
# 2: chocolate
# 3: pecan
# 4: strawberry
```

```python
for i, flavor in enumerate(flavor_list, 1):
    print(f"{i}: {flavor}")

# 1: vanilla
# 2: chocolate
# 3: pecan
# 4: strawberry
```

## iteretor and generator

### iter()

   list

```python
a = [1, 2, 3, 4]
it_a = iter(a)
print(next(it_a))
print(next(it_a))
print(next(it_a))
print(next(it_a))

# 1
# 2
# 3
# 4
```

+ enumerate()

```python
it_enum = enumerate(flavor_list)
print(next(it_enum))
print(next(it_enum))
print(next(it_enum))
print(next(it_enum))

# (0, 'vanilla')
# (1, 'chocolate')
# (2, 'pecan')
# (3, 'strawberry')
```

### generator

```python
def test_gen():
  yield 1
  yield 2
  yield 3
  
gen = test_gen()
print(next(gen))
print(next(gen))
print(next(gen))

# 1
# 2
# 3
```

# 4

## Recursive functions

### Memoization (top-down approach)

### Tabulation (bottom-up approach)

## Arguments

### Keyword arguments

```python
def print_something(personname, univname):
    print(f"Hello {personname} in {univname}")

print_something("Taewon", "SCH University")
print_something(personname = "yim", univname = "SCH University")
print_something(univname = "SCH University", personname = "yim")
```

### Default arguments

```python
def print_something(personname, univname="SCH University"):
    print(f"Hello {personname} in {univname}")

print_something("yim", "SCH University")
print_something("yim", univname = "Other University")
```

### Variable-length arguments (Unpacking)

+ 가변인자

```python
def summation(a, b, *args):
    # return a + b + sum(args)
    print(a, b, args)

print(summation(1,2))
print(summation(1,2,3,4,5))
```

### Keyword variable-length arguments

+ 매개변수를 딕셔너리로

```python
def kwargs_test(**kwargs):
    print(kwargs['first'], kwargs['second'], kwargs['third'])

kwargs_test(first = 3, second = 4, third = 5)
```

+ 딕셔너리를 전달해도 됨

```python
def print_major_info(**kwargs):
    print(kwargs['Major'])

info = {'Name':'Taewon', 'Affiliation':'SCH University'}
info['Major']='Electrical Engineering'

print_major_info(**info)
```

### *args + **kwargs

```python
def f(*args, **kwargs):
    print(args)
    print(kwargs)
    
f(10, 20, name='yim', age='20', gender='male')
```

## yield

+ iterable

```python
def test_generator():
    yield 1
    yield 2
    yield 3

gen = test_generator()
print(next(gen))
print(next(gen))
print(next(gen))
```

+ 

```python
def weird_calculator(a, b):
    print(f"Addition: {a} + {b}")
    yield a+b
    
    print(f"Subtraction: {a} - {b}")
    yield a-b
    
    print(f"Multiplication: {a} * {b}")
    yield a*b
    
    print(f"Division: {a} / {b}")
    yield a/b
    
a = 10
b = 5
g = weird_calculator(a, b)
print(type(g))

print(next(g))
print(next(g))
print(next(g))
print(next(g))
```

## Type annotation

```python
age: int = 10
```

```python
def greeting(name: str) -> str:
    return 'Hello ' + name

greetings = greeting('yim')
print(greetings)
```

# 5

## String

### String manipulations

+ strip(): get rid of spaces in both sides
+ split(): splits string by spaces
+ split('.'): splits string by '.'
+ list is immutable data type

```python
str_example = " 수익률 (1M/3M/6M/1Y)/ +4.58%/ -4.78%/ -4.66%/ +34.20%  "
print(str_example)
print("============")

print(str_example.strip())
print(str_example.split())
print(str_example.split("/"))

# immutable
stripped_str_example = str_example.strip()
print(stripped_str_example.split("/ "))
```

### File

+ write

```python
filename = 'yesterday.txt'
lyric_file = open(filename, 'wb')
lyric_file.write(lyric)
lyric_file.close()
```

+ readline() and readlines()

```python
f = open('yesterday.txt', 'r')
lyric_with_readline = f.readline()  # one line
lyric_with_readlines = f.readlines()  # all lines, including '\n'
f.close()
```

### Formatting and Literals

+ padding

```python
num_pi = "3.141592"
num_e = "2.718281"

print("PI is %s and Euler's number is %s." % (num_pi, num_e))
print("PI is {} and Euler's number is {}.".format(num_pi, num_e))
print(f"PI is {num_pi} and Euler's number is {num_e}.")

# Padding
print("===Padding===")
print("PI is %10s and Euler's number is %s." % (num_pi, num_e))
print("PI is {:>10} and Euler's number is {}.".format(num_pi, num_e))
print(f"PI is {num_pi:>10} and Euler's number is {num_e}.")
```
+ '' % 3

```python
'I eat %d apples.' % 3
```

+ Numeric literals

```python
# Integer Literals
a = 0b1010 # Binary Literals
b = 100 # Decimal Literal
c = 0o310 # Octal Literal
d = 0x12c # Hexadecimal Literal

# Float Literal
float_1 = 10.5
float_2 = 1.512e2

# Complex Literal
x = 1.1 + 3.14j

print(a, b, c, d)
print(float_1, float_2)
print(x, x.real, x.imag)
```

+ String literals

```python
# String Literals
strings = "This is Python"
char = "C"
multiline_str = """This is a multiline string with more than one line code."""
unicode = u"\u00dcnic\u00f6de"
raw_str = r"raw \n string"

print(strings)
print(char)
print(multiline_str)
print(unicode)
print(raw_str)
```

+ Boolean literals

```python
# Boolean Literals
x = (1 == True)
y = (1 == False)
a = True + 4
b = False + 10

print("x is", x)
print("y is", y)
print("a:", a)
print("b:", b)
```

# 6

## conda

```bash
conda create -n "name" python=3.10
```

```bash
conda activate name
```

```bash
```