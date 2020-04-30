# **PYTHON: PACKAGE**

Python has variety of packages that can be easily downloaded and used on-demand. This chapter describes what the package is and how to implement it to the script.

## Modules

A Python module is simply a Python source code file with `.py` extension. Developer may developed their own code containing class or function, and calling those codes from distribute Python file can be done using `import` keyword.

```python
import module
module.function()
```

Above approach still requires name of the module to be mentioned every time when using its function. To ignore referring to the module while still using module's function, use the `from` keyword beforehand.

```python
from module import function1, function2
from module import function as name
```

However, because module is not referred to use the function, there is potential conflict caused by function naming. Unless the function is named with guaranteed uniqueness, it is safe to use the previous approach to import modules.

## Package

Package is a directory of folder that holds a collection of Python modules or sub-packages. Every package folder must have a special Python file called `__init__.py` which can be blank or contains directory path of current package to prevent directories error caused by a common name.

```python
import package.module
from package.module import function
```

## Python Package Index

Python Package Index (aka. PyPI) is an external module storage website (*https://pypi.python.org/pypi*). To download and install the modules and packages, a software called pip is necessary.

### PIP

The pip software is a package management system required to install and manage the Python package. Nowadays, pip comes installed by default with modern distribution of Python. User can install pip separately online. Installation and management of packages are done using Command Prompt.

| NAME         | DESCRIPTION               | COMMAND                 |
| ------------ | ------------------------- | ----------------------- |
| Installation | Install the package       | `pip install package`   |
| Remove       | Uninstall the package     | `pip uninstall package` |
| List         | Show the list of packages | `pip list`              |

When using Python on Windows, it is recommended to use `python -m pip` instead of `pip` alone. 

```
python -m pip
```

In case `python` command does not work but opens Microsoft Store, type `py` instead.

The command means accessing the pip under the python interpreter specified as `python` in environment variable. This allows package management by each interpreter more controllable, even when using virtual environment. When there is another version of Python installed, say 32 bits of Python 3.5

```
py -3.5-32 -m pip
```