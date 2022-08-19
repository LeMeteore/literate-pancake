---
title: |
  "Python Type Hinting."
date: May, 2022
lang: en-EN
urlcolor: blue
geometry: "left=2.5cm,right=2.5cm,top=3cm,bottom=3cm"
documentclass: article
fontfamily: Alegreya
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhf{}
    \rhead{Dakar Institute of Technology}
    \lhead{Patrick Nsukami}
    \rfoot{Page \thepage}
    \hypersetup{pdftex,
            pdfauthor={Lucis ASSOGBA},{Viwossin Dégboé}
            pdftitle={Python Type Hinting},
            pdfsubject={Python Type Hinting},
            pdfkeywords={Python, Programming, Type Hinting},
            pdfproducer={Emacs, Pandoc, Latex, Markdown},
            pdfcreator={Emacs, Pandoc, Latex, Markdown}}
    
---
INTRODUCTION

Python is a programming language that has been popular for some time now. Its excellent design makes it well-suited for data analysis and machine learning, and it also supports many other applications.
Python's syntax is intuitive and easy to read, which makes it pleasant to work with.

The simplicity of Python can, paradoxically, become a problem. Applications are more quickly produced but they can also contain more bugs. One of the criticisms often levied against Python is its dynamic typing. In fact, the type of variables is assigned at declaration time and it can be changed during the interpretation of code.

Python 3.5 introduced the "type hinting" (PEP484: Type Hints). In this article, we'll explain how type hinting works in Python, what strategies you can adopt to use it in your codebase and how to verify types while your program is running.


How to type in python?

The Typage is done through annotations. They allow you to associate a given type (List, bool, etc) 
Python has a set of primitive types that are the most commonly used and reoccurring. These include bool, int, str, and float. They can be used to type arguments as well as return values from functions. In the example 1 below, the circle_surface function takes in a radius argument and calculates the surface of that circle. The argument is of type float (indicated after : following the name of the argument) and the response is also of type float (the return type is indicated after ->).

It is also possible to create composite data types such as lists of integers (integer) or in this example2 lists of floating-point numbers (floats).




# Foo:

foo bar baz

```python
# Exemple 1
def circle_surface(radius: float) -> float:
    return 3.141516 * math.sqrt(radius) 

# Exemple 2
from typing import List

Vector = List[float]

def scale(scalar: float, vector: Vector) -> Vector:
    return [scalar * num for num in vector]

def bar(x):
    print(x)

def foo():
    return 42
```
