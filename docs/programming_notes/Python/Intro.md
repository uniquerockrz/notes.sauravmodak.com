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

You can get the type of variable by using `type()`.

```python
> type('Saurav')
'str'
```

