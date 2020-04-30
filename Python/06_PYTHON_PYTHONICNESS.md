# **PYTHON: PYTHONICNESS**

As learning to understand how the Python can and be use on programming, there is a Python's unique style of programming recommended for Python developer to implement as possible.

## Zen of Python

A set of principle guide when coding Python, provided within Python itself. Accessible via example below.

```python
import this
```

## Python Enhancement Proposals

Eight scripting style guides for Python suggested by experienced Python developers, aka. **PEP8**.
1.	Module should have short, all-lowercase name.
2.	Class name should be in the CapWords style.
3.	Most variables and function names should be lowercase_with_underscores.
4.	Constants (variables that never change value) should be CAPS_WITH_UNDERSCORES.
5.	Names that would clash with Python keywords (such as 'class' or 'if') should have a trailing underscore.
6.	Line shouldn’t be longer than 80 characters.
7.	`from module import *` should be avoided.
8.	There should be only one statement per line.

## Entry Point

While other program language such as C/C++ has a traditional entry point called `main()` which is the function where the program execution starts, Python does not have one.

Instead, Python uses special variable `__name__` which indicates the current Python script being executed. When this script is the main executing file, the `__name__` variable is assigned as `"__main__"` value. 

```python
# ENTRY POINT
if __name__ == "__main__":
    statements
```

Codes and statements indented under this condition will not be executed when it is imported as a module to the other script. Beware, the equivalent `==` operator cannot be replaced to logical `is` operator.