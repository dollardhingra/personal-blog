## Python Code Best Practices

## Introduction
This article is a collection of best practices for more idiomatic python code especially if you are new to python. 

## Contribute
Feel free to [contribute](https://github.com/dollardhingra/dollardhingra.github.io/edit/master/_posts/2021-12-05-python-code-best-practices.md) to this list, and I will thank you by including a link to your profile with the snippet!

## 1. Catching Exceptions
This is a sure-shot way to get your code into trouble

```python
# very bad practice
try:
    do_something()
except:
    pass

# A slightly better way(included logging), but still a bad practice:
try:
    do_something()
except Exception:
    logging.exception() # although, logging is a good practice

# When we don't use `Exception` we will also be catching events like system exit. 
# So, using Exception means that we are only catching Exceptions.

# A better way:
try:
    do_something()
except ValueError:
    logging.exception()
    # some code to handle your exception gracefully if required

```
Here we have used a specific type of Exception i.e. `ValueError`. 


## 2. Name Casing

```python

# using camelCase is not a convention in python
def isEmpty(sampleArr):
    ...
    
# instead use snake_case in python
def is_empty(sample_arr):
    ...
```

In python, `snake_case` is preferred for variables, functions and method names. However, for classes, `PascalCase` is used.

## 3. Chained comparison operators
There are multiple ways of comparing in Python:

```python
# Don't do this:
if 0 < x and x < 10:
    print('x is greater than 0 but less than 10')

    
# Instead, do this:
if 0 < x < 10:
    print('x is greater than 0 but less than 10')
```

## 4. Mutable default arguments

```python

# wrong way!
# a sure shot way to get some unintended bugs in your code
def add_fruit(fruit, box=[]):
    box.append(fruit)
    return box


# correct way!
# recommended way for handling mutable default arguments:
def add_fruit(fruit, box=None):
    if box is None:
        box = []
        
    box.append(fruit)
    return box
```
Read more about mutable default arguments [here](https://dollardhingra.hashnode.dev/python-mutable-default-arguments)



## 5. String Formatting

```python

# Avoid using it
# %-formatting
name = "James Bond"
profession = "Secret Agent"
print("Hello, %s. You are a %s." % (name, profession))

# slightly better
# str.format()
print("Hello, {}. You are a {}.".format(name, profession))

# Short, crisp and faster!
# f-strings
print(f"Hello, {name}. You are a {profession}.")
```

The f in f-strings may as well stand for "fast." f-strings are faster than both %-formatting and str.format(). [(Source)](https://www.python.org/dev/peps/pep-0498/#abstract)


## 6. Top-level script environment
Executes only if it is run as a script and not as a module

```python
# Filename: run.py

if __name__ == '__main__':
    print('Hello from script!')
```

```
$ python run.py
$ Hello from script!
```

`Hello from script!` will **not** be printed if the module is imported into any other module.


## 7. Conditional expressions

```python
if x < 10:
    return 1
else:
    return 2
```

Can be reduced to this one:
```python
return 1 if x < 10 else 2
```


## 8. Iterating over an iterator
You don’t necessarily need to iterate over the indices of the elements in an iterator if you don’t need them. You can iterate directly over the elements.
This makes your code more pythonic.

```python
list_of_fruits = ["apple", "pear", "orange"]

# bad practice
for i in range(len(list_of_fruits)):
    fruit = list_of_fruits[i]
    process_fruit(fruit)
      
# good practice
for fruit in list_of_fruits:
    process_fruit(fruit)
```

## 9. Indexing/Counting during iteration

```python
# Don't do this:
index = 0
for value in collection:
    print(index, value)
    index += 1


# Nor this:
for index in range(len(collection)):
    value = collection[index]
    print(index, value)

# Definitely don't do this:
index = 0
while index < len(collection):
    value = collection[index]
    print(index, value)
    index += 1

# Instead, use `enumerate()`
for index, value in enumerate(collection):
    print(index, value)
```

## 10. Using context managers
Python provides context managers that manage the overhead of initializing and clearing up the resources and let
you focus on the implementation. For example in the case of reading a file, you don't need to be concerned 
to close the file manually.


```python
d = {"foo": 1}

# bad practice 
f = open("./data.csv", "wb")
f.write("some data")

v = d["bar"] # KeyError
# f.close() never executes which leads to memory issues

f.close()

# good practice
with open("./data.csv", "wb") as f:
    f.write("some data")
    v = d["bar"]
# python still executes f.close() even if the KeyError exception occurs
```

## 11. Using set for searching instead of a list

```python
s = set(['s', 'p', 'a', 'm'])
l = ['s', 'p', 'a', 'm']

# ok for small no. of elements
def lookup_list(l):
return 's' in l # O(n)


# better for large no. of elements
def lookup_set(s):
return 's' in s # O(1)
```
Sets are implemented using hash in python, which makes searching of element faster(O(1)) as compared to searching in a 
list(O(n)). 


## 12. using * while importing a module
Imports should always be specific. Importing * from a module is a very bad practice that pollutes the namespace.
```python
# bad practice 
from math import *
x = ceil(x)

# good practice 
from math import ceil   
x = ceil(x) # we know where ceil comes from
```

## 13. using items() for iterating a dictionary

```python

d = {
     "name": "Aarya", 
     "age": 13
 }

# Dont do this
for key in d:
    print(f"{key} = {d[key]}")

# Instead do this
for key,val in d.items():
    print(f"{key} = {val}")
```

## Sources
- [RealPython f-strings](https://realpython.com/python-f-strings/)
- [RealPython the most diabolic anti pattern](https://realpython.com/the-most-diabolical-python-antipattern/)
- [Python Idiom Patterns](https://arielortiz.info/s201911/pycon2019/docs/design_patterns.html)
- [18 Common Python Anti-Patterns I Wish I Had Known Before](https://towardsdatascience.com/18-common-python-anti-patterns-i-wish-i-had-known-before-44d983805f0f)