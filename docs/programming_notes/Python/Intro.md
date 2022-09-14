---
sidebar_position: 1
---
# Intro

Python is an interpreted and high level language. It supports duct typing in variables, which means you don't need to define the type of variable before using them. This is different from some compiled languages such as C, C++, C# etc. 

You can execute python in a REPL fashion, either by starting the interpreter `python` or using some other tool such as `ipython` or `jupyter`. You can just enter the python code in their cells, and it will execute it instantly and show you the output (if the output is not saved in a variable).

## Variables & Data Types

Integers and floating point numbers can be defined as is:

```python
a = 13
b = 1.2
```

Strings can be declared in a number of ways

```python
'Saurav'

"Saurav"

'''Hello
World!
'''

"""Hello,
World"""
```

The only difference is with `'''` and `"""` you can have multiple lines of strings.

Boolean values can either be true and false.

```python
a = True
b = False
```

You can get the type of variable by using `type()`.

```python
> type('Saurav')
'str'
```

List are a collection of variables that begin and end with `[` and `]`. Lists in python can have different data types. 

```python
l = [ 1, 2, 'abc', 'def', True ]
l.append(False)
l[1] = 24
```

Python uses zero index to access the value of a list. E.g. `l[0]`. You can add values using `append()` and you can change the value of a particular index.

Dictionaries are created using `{` and `}` and contain the key value pairs. 

```python
{
	"name": "Saurav Modak",
	"age": 31
}
```

You can access the data of dictionary using the keys, e.g. `obj["name"]`. 

Dictionaries and JSON are quite similar, but they have some subtle differences (like the keys need to be string and in double quotes).

The last native data type we need to know is a tuple. Tuple is an immutable list of data, with properties similar to lists, except the values cannot be changed. 

## Some Essential Python Functions

`help()`: This is used for getting the documentation of a function or a class. 

`range(start, end, step)`: Gets a sequence of numbers from `start` (inclusive) to `end` (exclusive) with `steps`. You can use this range in for loops. 

## Loops In  Python

The simplest loop in python is a for loop which we can use using range. Since python is an indented language, indentation is important and determines the scope of the variables and statement in loops. 

```python
for i in range(10):
    print('i: ' + str(i))
    for j in range(i):
        print('j: ' + str(j))
```

`range()` returns an iterable, which we use to run the for loop. They are like lists, but we can use them in loops like above. 