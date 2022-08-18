---
title: |
  "Introduction Python Type Hinting."
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
            pdftitle={Introduction Python Type Hinting},
            pdfsubject={Introduction Python Type Hinting},
            pdfkeywords={Python, Programming, Type Hinting},
            pdfproducer={Emacs, Pandoc, Latex, Markdown},
            pdfcreator={Emacs, Pandoc, Latex, Markdown}}
    
---
INTRODUCTION

Python is a programming language that has been popular for some time now. Its excellent design makes it well-suited for data analysis and machine learning, and it also supports many other applications.
Python's syntax is intuitive and easy to read, which makes it pleasant to work with.

The simplicity of Python can, paradoxically, become a problem. Applications are more quickly produced but they can also contain more bugs. One of the criticisms often levied against Python is its dynamic typing. In fact, the type of variables is assigned at declaration time and it can be changed during the interpretation of code.

Python 3.5 introduced the "type hinting" (PEP484: Type Hints). In this article, we'll explain how type hinting works in Python, what strategies you can adopt to use it in your codebase and how to verify types while your program is running.
# Foo:

foo bar baz

```python
# module foo.py

a = 42

def bar(x):
    print(x)

def foo():
    return 42
```
