## Code Quality Tools in Python

---
 title: Python Code Quality Tools 
 tags: [python, code-quality]
 style: fill
 color: light
 comments: true
 categories: computer-science
 excerpt: An introduction to some code quality tools in python like linters, formatters & style guides
---

## What is code quality?
Before we talk about code quality tools, let's see what code quality is. We can agree that code is of high quality if

### It does what it is supposed to do
If the code written is not doing what is supposed to do, then it doesn't meet the very basic requirements, and we can
say that the code quality is low.

### It does not contain defects or problems
Let's say that your code does what it is supposed to do, but struggles to perform well on edge cases. Let's take an
example of a mobile app that you start using for communicating with friends and family. You can send & receive messages easily from your friends through this app. One fine day, you want to share a photo with a group and your app
crashes. Certainly, there is some issue with the code that has not been tested properly. 


### It is easy to read, maintain, and extend
Robert C. Martin in his book [Clean Code](https://www.oreilly.com/library/view/clean-code-a/9780136083238/) says:

>Indeed, the ratio of time spent reading versus writing is well over 10 to 1. We are constantly reading old code as
part of the effort to write new code. Because this ratio is so high, we want the reading of the code to be easy, 
even if it makes the writing harder.

Therefore, code readability is a very important factor in code quality. A code which is readable makes it easier to maintain and extend.


## Style guide: following the conventions

> Great codebases look like they were written by an individual, 
when they were worked on by a team.

Consistent code is easier to read & therefore maintain by a team. 
**A style guide serves the purpose of defining a consistent way to write your code.** 
The style guide contains conventions to be followed for writing a code. 
[PEP8](https://pep8.org/) is the official style guide for Python that is recommended to use for writing any python code.
Let's consider a small example. In the python code below, the operators tend to get scattered across different columns 
on the screen, and each operator is moved away from its operand and onto the previous line. 
Here, the eye has to do extra work to tell which items are added and which are subtracted:

**Not Recommended:**
```python
## No: operators sit far away from their operands
income = (gross_wages +
          taxable_interest +
          (dividends - qualified_dividends) -
          ira_deduction -
          student_loan_interest)
```




To solve this readability problem, mathematicians and their publishers follow the opposite convention which is more 
readable

**Recommended:**
```python
## Yes: easy to match operators with operands
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```

Another official recommendation from Python is [PEP-257](https://www.python.org/dev/peps/pep-0257/) Docstring Conventions.
A docstring is a string literal that occurs as the first statement in a module, function, class, or method definition.

```python
def complex(real=0.0, imag=0.0):
    """Form a complex number.

    Keyword arguments:
    real -- the real part (default 0.0)
    imag -- the imaginary part (default 0.0)
    """
    if imag == 0.0 and real == 0.0:
        return complex_zero
    ...
```
There are tools capable of generating documentation directly from the code if the docstrings are consistent in the code.

Some organisations like Google have their own [style guides](https://google.github.io/styleguide/). 
Checkout google's [python style guide](https://google.github.io/styleguide/pyguide.html).  




## How to measure code quality?
There are different ways to measure code quality in general. This article talks about some basic tools
provided in Python to measure the code quality:
- Linters
- Formatters

## Linters
Linters analyze code to detect various categories of issues:

1. Logical Issue
  - Code errors
  - Code with potentially unintended results
  - Dangerous code patterns
  
2. Stylistic Issue
  - Code not conforming to defined conventions/style guide

### Popular python linters

1. [Pylint](https://www.pylint.org/): Features like checking **coding standards**, **error detection**, **refactoring help** and more.
2. [pycodestyle](https://github.com/PyCQA/pycodestyle): for checking some of the style conventions in PEP8
3. [Flake8](https://pypi.org/project/flake8/): a combination of following linters: [PyFlakes](https://github.com/PyCQA/pyflakes), 
[pycodestyle](https://github.com/PyCQA/pycodestyle), [Ned Batchelder’s McCabe script](https://github.com/PyCQA/mccabe)
4. [Pylama](https://github.com/klen/pylama): composed of the following linters and other tools for analyzing code: 
- [pycodestyle](https://github.com/PyCQA/pycodestyle)
- [pydocstyle](https://github.com/PyCQA/pydocstyle)
- [PyFlakes](https://github.com/PyCQA/pyflakes) 
- [Mccabe](https://github.com/PyCQA/mccabe) 
- [Pylint](https://www.pylint.org/) 
- [Radon](https://radon.readthedocs.io/en/latest/)
- [gjslint](https://atom.io/packages/linter-gjslint)

Every linter has its advantages and disadvantages and should be picked up based on the project you are working on.
If a linter doesn't give out any warning for any lint, that doesn't mean that code is always correct, a linter is just a 
static tool for code analysis. It cannot check if the job that is supposed to be done is done or not.



## Formatters
Formatters automatically format your code based on a style guide. Some popular python formatters are:

### Black
as per the black's documentation, [Black](https://github.com/psf/black) is "The uncompromising Python code formatter". 
It is my personal favourite because it has minimal configuration and is fast enough. Black is used by some very popular open-source projects, such as pytest, tox, Pyramid, Django Channels, Poetry, and so on. Example usage:

`unique.py`

```python
def is_unique(
               s
               ):
    s = list(s
                )
    s.sort()
 
 
    for i in range(len(s) - 1):
        if s[i] == s[i + 1]:
            return 0
    else:
        return 1
 
 
if __name__ == "__main__":
    print(
          is_unique(input())
         )
```

`$ black unique.py` produces the following
```python
def is_unique(s):
    s = list(s)
    s.sort()
 
    for i in range(len(s) - 1):
        if s[i] == s[i + 1]:
            return 0
    else:
        return 1
 
 
if __name__ == "__main__":
    print(is_unique(input()))
```

### YAPF
[YAPF](https://github.com/google/yapf) (Yet Another Python Formatter) is Google's official python formatter which
follows google's [style guide](https://google.github.io/styleguide/pyguide.html). The documentation is easy to
understand the installation and configuration for this formatter.

### autopep8
[autopep8](https://pypi.org/project/autopep8/) is an unofficial, yet popular, tool that automatically formates 
Python code to conform to PEP 8. It uses pycodestyle, Python’s official PEP-8 violation checker tool, to determine what parts of the code need to be formatted.


### isort
[isort](https://github.com/PyCQA/isort) is a Python utility/library to sort imports alphabetically, and 
automatically separated into sections and by type.

Before isort:

```python
from my_lib import Object

import os

from my_lib import Object3

from my_lib import Object2

import sys

from third_party import lib15, lib1, lib2, lib3, lib4, lib5, lib6, lib7, lib8, lib9, lib10, lib11, lib12, lib13, lib14

import sys

from __future__ import absolute_import

from third_party import lib3

print("Hey")
print("yo")
```

After isort:

```python
from __future__ import absolute_import

import os
import sys

from third_party import (lib1, lib2, lib3, lib4, lib5, lib6, lib7, lib8,
                         lib9, lib10, lib11, lib12, lib13, lib14, lib15)

from my_lib import Object, Object2, Object3

print("Hey")
print("yo")
```




## Where to use the code quality tools?
You can use these code quality tools:
- In your IDE/editor, when you are writing your code
- on committing the code
- merging the code or while running the tests


### IDE/editor

Most modern IDEs and editors have inbuilt support for linters. Some editors like [VS Code](https://code.visualstudio.com/docs/python/linting) have great support for linters. You can also run a specific formatter on running the auto-format command in VS Code. Check more about it
[here](https://code.visualstudio.com/docs/python/editing#_formatting).

For IDE like Pycharm, there are plugins available for running lints and formatters. For example, check out the [pylint plugin](https://plugins.jetbrains.com/plugin/11084-pylint) and 
[black formatter plugin](https://plugins.jetbrains.com/plugin/10563-black-pycharm)

### On Committing the code: Hooks
Like many other Version Control Systems, Git has a way to fire off custom scripts when certain important actions occur through [git-hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks). You can use these scripts to run the 
lints and formatters to block any new code that doesn’t meet quality standards or to automatically format the commit.
A useful [pre-commit](https://pre-commit.co m/) (written in python) is a multi-language package manager for 
pre-commit hooks. You specify a list of hooks you want and pre-commit manages the installation and execution of any hook written in any language before every commit


### When running tests: Continuous Integration
You can also place linters & formatters directly into whatever system you may use for continuous integration. 
The linters can be set up to fail the build if the code doesn’t meet quality standards. A CI(continuous integration)  is a practice of automating the integration of code changes from multiple contributors into a single software project. This means that as soon as a developer merge their code in the main branch, the CI 
pipeline(for eg: git workflow) can perform some automatic operations like formatting before the code is deployed.



## Conclusion
A code is of high quality if it does what it is supposed to do, it **does not contain defects** or problems and
it is easy to **read, maintain, and extend**. Style guides like A style guide like [PEP8](https://pep8.org/) and google's [style guide](https://google.github.io/styleguide/) help serve the purpose of defining a consistent way to write your code. The different tools for measuring and improving the code quality are linters & formatters.

Linters analyze code to detect various categories of issues like logistical issue and stylistic issues. Some  
popular linters are [Pylint](https://www.pylint.org/), [pycodestyle](https://github.com/PyCQA/pycodestyle), 
[Flake8](https://pypi.org/project/flake8/) and [Pylama](https://github.com/klen/pylama). 

Formatters automatically format your code based on a style guide. Some popular formatters are 
[Black](https://github.com/psf/black), [YAPF](https://github.com/google/yapf), 
[autopep8](https://pypi.org/project/autopep8/) and [isort](https://github.com/PyCQA/isort). 

Finally, You can use these code quality tools using:
- IDE/editors - when you are writing your code
- pre-commit hooks - on committing the code using 
- continuous integration - while running the tests
