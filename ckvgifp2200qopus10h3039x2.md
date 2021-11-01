## #1 Python Anti-Pattern: Mutable Default Arguments

## Introduction
If you are not sure what a mutable default argument is, please read the full article as it can save you hours of 
debugging.


## Code Example With A Mutable Default Argument
Consider the following code example below. 

```python
def add_fruit(fruit, box=[]):
    box.append(fruit)
    return box

```

Let's understand step by step what is happening:

- We are creating a function to add fruits(str) in a box(list)
- There is a `add_fruit` function which is responsible for adding the `fruit`
- This function takes 2 arguments: `fruit` and `box`
- **Attention!** : The second argument here is a mutable default argument.

## So, what is mutable default argument?

An argument in a function with default value as mutable. 

In short, Python has both mutable and immutable types. The difference being: 
- mutables can be modified
- immutables can't be modified.

For eg: Tuple is an immutable type. If we define a tuple like this:

```python
weekends = ('saturday', 'sunday',)

weekends[0] = 'Monday' # TypeError: 'tuple' object does not support item assignment
```
An immutable type can never be modified.


## What You Might Expect
let's modify our code and create a couple of boxes, i.e. red box and yellow box

```python
def add_fruit(fruit, box=[]):
    box.append(fruit)
    return box

red_box = add_fruit("apple")
print(f"red box: {red_box}")

yellow_box = add_fruit("mango")
print(f"yellow box: {yellow_box}")
```

### Expected Output

```
red box: ["apple"]

yellow box: ["mango"]
```

### Actually Output
Actually, you get the following output:

```
red box: ["apple"]

yellow box: ["apple", "mango"]
```

Wait? What? We never added apple in the yellow box. 

## What Exactly Happened

A new list is created once when the function is defined, and the same list is used in each successive call. 

> Python’s default arguments are evaluated once when the function is defined. This means that if you use a mutable default argument and mutate it, you will and have mutated that object for all future calls to the function as well.

We will get the same result for other mutable types also(For eg: dict).

## What Should Be Done
If your function needs to have a default argument for a mutable type, then default it with None and also add a check for same.
Let's modify our `add_fruit` function:

```python
def add_fruit(fruit, box=None):
    if box is None:
        box = []
        
    box.append(fruit)
    return box

red_box = add_fruit("apple")
print(f"red box: {red_box}")

yellow_box = add_fruit("mango")
print(f"yellow box: {yellow_box}")
```

This extra check can saves hours of debugging!

## Conclusion
It's always a best practice to not use mutable default arguments. Instead, try adding an extra comparison check with 
None to handle default arguments which are mutable.