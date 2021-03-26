## Abstract Base Class in Python

## What is an abstract base class?
In simple words, an abstract base class provides a blueprint for other classes. Abstract base classes doesn't contain the implementation. Instead, they provide an interface and make sure that the derived classes are properly implemented.

## Why do we need abstract base classes?
Imagine that you are creating a game in which you have different animals. For defining animals you can have an abstract class called as `Animal`. A Dog/Cat/Duck are all the classes that are derived from the base class `Animal`. 

### Animal Base Class
```
class Animal:
    def get_age():
        ## return age of the animal
    
    def is_dead():
        ## return the colour of the animal
```

- Every animal will have both of these methods. So, we want every animal to implement these methods whenever we are inheriting an animal class from the `Animal` class. We cannot have an animal which doesn't supports any of these methods. [Rule 1]
- Whenever we see an animal, we call it a dog/cat/duck/tiger.. These are all kinds of **animals**. That is, you never look at something purple and furry and say "that is an animal and there is no more specific way of defining it". The point is, that you can never see an animal walking around that isn't more specifically something else (duck, pig, etc.) [Rule 2]


## Rules
By using these 2 rules we can make our code more maintainable and programmer-friendly
#### Rule 1
> Subclasses inherited from a specific base class must implement all the methods and properties defined in the abstract base class.

#### Rule 2
> Abstract base classes cannot be instantiated. They are inherited by the other subclasses.


## Implementation in Python
Let's try to implement these animal classes in Python with the rules we talked about.

```
class Animal:
    def get_age(self):
        # return the animal's age
        raise NotImplementedError()

    def is_dead(self):
        # check if animal is dead or alive
        raise NotImplementedError()


class Dog(Animal):
    def bark(self):
        print("whoof whoof!!")

    def get_age(self):
        print("5 years")

```
In the above program we are creating a `Dog` class that is inheriting all the methods from the `Animal` class. Let's see if the rule 1 is followed. 
> Rule 1: Subclasses inherited from a specific base class must implement all the methods and properties defined in the abstract base class.

Let's create an object of the `Dog` class

```
bulldog = Dog()

bulldog.get_age() # 5 years

bulldog.is_dead() # NotImplementedError
 
```
The subclass `Dog` does not implements the `is_dead` method of the `Animal` base class and when we try to call this method from the bulldog object we get an error. So this works as expected. But we are able to run the program successfully if we don't call this method without even a warning for breaking this rule. Ideally, all the methods of the base class should be implemented by the subclass.

**Clearly the above program does not follow Rule 1.**

>Rule 2: Abstract base classes cannot be instantiated. They are inherited by the other subclasses.
Let's check if Rule 2 is followed. Let's try to instantiate the base class.

```
animal = Animal()
animal.get_age() # NotImplementedError
```
We get the error if we try to call base class' method. But, we are able to instantiate the base class. 
**So, the above program doesn't follow Rule 2**

## `abc` module to the rescue

With Python's `abc` module, we can do better and make sure that both the rules are followed.
Let's update the above program

```
from abc import ABC, abstractmethod


class Animal(ABC):
    @abstractmethod
    def get_age(self):
        pass

    @abstractmethod
    def is_dead(self):
        pass


class Dog(Animal):
    def bark(self):
        print("whoof whoof!!")

    def get_age(self):
        print("5 years")


    # we forgot to declare "is_dead" again

```
In the above program we have imported the helper class `ABC` from the module `abc` through which we have implemented the base class. Also, we have used the decorator `@abstractmethod` for all the methods in our base class.

Let's try to instantiate our subclass: `Dog`
```
bulldog = Dog()
```


```
TypeError: Can't instantiate abstract class Dog with abstract methods is_dead
```
This time we get a `TypeError` specifying that the abstract method is not implemented.

** This follows the Rule 1 successfully. **

Let's try to instantiate our base class: `Animal`

```
animal = Animal()
```

```
TypeError: Can't instantiate abstract class Animal with abstract methods get_age, is_dead
```
This time we get a `TypeError` specifying that the abstract class cannot be instantiated.

** This follows the Rule 2 successfully. ** 

## Conclusion
Using ABCs in your code will make your class hierarchies more robust and more readily maintainable. Some of the key takeaways in this article are:

- Abstract e Classes(ABCs) ensure that derived classes implement the particular methods from the base class at instantiation time.
- Using ABCs can help in writing a bug free class hierarchies which are easy to read and maintain.