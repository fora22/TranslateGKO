# **PYTHON: FUNCTIONAL PROGRAMMING**

There are three different types of programming method that can be applied to Python language: procedural, functional, and object-oriented.

Functional programming is a style of program scripting that is based mostly around usage of the functions. This chapter will be introducing the guide on how to create and use function in Python for functional programming.

## Function

Function is an independent block of code which can process the data and present newly processed data once it’s called, allowing dynamic program scripting. Function can be distinguished from its code format which has parenthesis after its name; `function()`.

The programming based around use of custom functions is called *functional programming*.

```python
x = [0, 3, 5, 9]
print(len(x))
# Code "print()" function, and "len( )" function that returns the length of list object.
```

```
4
```

Although function acts quite different from variable, they can be treated just the same. For easier understanding please refer to the example below:

```python
# ORIGINAL FUNCTION
function(arg1, arg2)

# ASSIGNING AND EXECUTING FUNCTION VIA VARIABLE
variable = function
print(variable(arg1, arg2))
```

Not only can it be assigned to variable, but function can also be passed as parameter of the other function. Therefore, you can define a function by using another function that’s been already defined.

### Pure Function

Function that returns a value that depends only on their arguments without any side effects.

As for an example, cosine function `cos(x)` that only has single parameter `x` returns the value which depends only on the argument `x`; hence, the the cosine function is a pure function.

```python
# FUNCTION WITH x AND y PARAMETER.
def function(x,y):
    variable = 2 * x
    vairable += y
    return variable			# RETURN DEPENDS ONLY ON x AND y PARAMETER.
```

### Higher-Order Function

A function that takes other function(s) as parameters or return the function(s) as a result.

## `def` Keyword

The `def` keyword is used to create your own function. When calling your newly created function before defining one, an error occurs as Python executes sequentially, thus is deemed calling non-existing function.

```python
def function(arg1, ar2):
    print(arg1 * arg2)
    return arg2

function("Hello",3)
print(function("World",2))
```

```
HelloHelloHello
WorldWorld
2
```

Parentheses `()` is necessary when defining a function even the function does not have any parameter.

### `return` Statement

The `return` statement is a function-exclusive statement that returns value of certain data that can be directly used from the function. Once a return statement is executed, the function ends immediately despite there are codes still left inside.

Function does not need to have a `return` statement which will return `None` when passed to variable or be printed on console terminal (for example, by using `print()` function).

```python
def function_name():
    print("Hello!")
    
print(function_name())
```

```
Hello!
None
```


### Parameter & Argument

Following are the difference between parameters and arguments that is referred significantly when discussed on function.

**Parameter**
Parameter is a function-internal local variable: because parameters is a function-exclusive local variable, it cannot be called from outside.

| OPERATOR |    SYNTAX    | DESCRIPTION                                                  |
| :------: | :----------: | ------------------------------------------------------------ |
|   `*`    |   `*args`    | Allows multiple number of arguments.<br />Call by `args`(arguments) without asterisk, and returns tuple of arguments. Must locate after normal parameter. |
|   `**`   |  `**kwargs`  | Allows use of undefined parameter in advance.<br />Call by `kwargs`(keyword arguments) without asterisks, and returns dictionary of arguments’ name and corresponding values. |
|   `=`    | `arg1=value` | Returns default value otherwise inputted to its parameter. Must locate after normal parameter. |

**Argument**
Argument is a value/object being passed to the function parameter and those passed values and objects will be processed by the function code.

Examples below show how function parameter and argument works:

```python
# PARAMETER *args ALLOWS MORE ARGUMENT TO BE PASSED.
def function(arg1, *args):
    print(arg1)
    print(args)
    print(args[0])
    
function(1, 2, 3, 4)
```

```
1
(2, 3, 4)
2
```

----

```python
# PARAMETER **kwargs ACCEPTS FUNCTION-UNDEFINED PARAMETER.
def function(arg1, **kwargs):
    print(kwargs)
    
function(1, key0 = value0, key1 = value1)
```

```
{key_0∶value_0, key_1∶value_1}
```

----

```python
# DEFAULT-INITIALIZED PARAMETER arg2
def function(arg1, arg2="string"):
    print(arg_2)
    
function(1)
function(2, "needle")
```

```
string
needle
```

## Anonymous Function

Also known as **Lambda function (express)**, is a function without declaration without name (thus, anonymous) and does not store data, returning value only from a single expression. Anonymous function is generally used for a single-use function, or as an argument of higher-order function's parameter.

| SYNTAX                                                       |
| ------------------------------------------------------------ |
| `lambda param0, param1 ∶ expression`                         |
| A main body of anonymous function consisting parameters and its return expression. |

Although anonymous function is a function without a name for a single-use, it can be assigned to variables and called when the function is needed. The anonymous function of the named function at *Pure Function* example section is expressed as below:

```python
# NAMED FUNCTION
def function(x, y):
    return 2 * x + y

# ANONYMOUS FUNCTION
(lambda x, y: 2 * x + y)(2, 3)

# ANONYMOUS FUNCTION ASSIGNED TO VARIABLE
variable = lambda x, y: 2 * x + y
variable(2,3)
```

```
7
```

## Map Function

Built-in function which takes iterable objects and function with parameters as arguments. Map function returns a list containing return value of the function with iterable objects as arguments.

| SYNTAX                                                       |
| ------------------------------------------------------------ |
| `map(function, iter0, iter1, ...)`                           |
| In higher-order `map` function, iterable object `iter0` and `iter1` are passed as argument for `function`. |

Conversion to an iterable object, such as `list()` function is necessary to avoid error such as "SyntaxError".

```python 
lst0 = [1, 2, 3, 4, 5]
lst1 = [0, 9, 8, 7, 6, 5]

var0 = map(lambda x, y: x ** 2 + y, lst0, lst1)
var1 = map(lambda y, x: x ** 2 + y, lst1, lst0)

print( list(var0) )
print( list(var1) )
```

```
[1, 13, 17, 23, 31]
[1, 83, 67, 53, 41]
```

## Filter Function

Built-in function which takes iterable object and Boolean conditioning function (aka. predicate) as arguments and returns iterable object containing only with the data that passed the predicate.

| SYNTAX                                                       |
| ------------------------------------------------------------ |
| `filter(predicate, iterable)`                                |
| In higher-order `filter` function, iterable object `iterable`are passed as argument for `predicate`. |

Conversion to an iterable object, such as `list()` function is necessary to avoid error such as "SyntaxError".

```python
lst = [1, 2, 3, 4, 5]

var = filter(lambda x: x % 2 is 0, lst)

print( list(var) )
```

```
[2, 4]
```

## Recursive Function

Recursive function is a function that calls itself (recursion). Factorial $!$ in mathematic is the best example of recursive function implementation.

```python
# EXAMPLE: FACTORIAL "!"
def factorial( x ):
    # BASE CASE: a case when to escape from the recursion.
    if x == 1: 
        return 1
    else:
        return x * factorial(x-1)

print( factorial(5) )
```

```
120
```

Recursion can occur indirectly by multiple number of functions calling one to another, then back to the beginning.

### Base Case

A case of recursion which doesn’t involve referring to itself anymore. It can be deemed as an exit condition. Without a base case, recursion results infinitely and thus crashes due to memory shortage:

```
RuntimeError: maximum recursion depth exceeded
```

## Decorator

A function which modifies original function’s functionality and returns the modified "function" itself (rather than returning value). Hence, assignment to a variable is needed for a function to properly work after processing through the decorator. Its function will then have a same name as the variable.

```python
# ORIGINAL FUNCTION
def function():
	statements

# CREATING DECORATOR
def decorator(func):
	def modified_function():
        """
        statements including func()
        """
	return modified_function

# DECORATING (MODIFYING) FUNCTION
variable = decorator(function) 
variable()		# WHICH IS ACTUALLY A FUNCTION ASSIGNED TO "variable".

# DECORATING (MODIFYING) FUNCTION: MAINTAIN FUNCTION NAME
function = decorator(function)
function()
```

Decorator above have decorated (modified) `function()` and assigned the decorated function to a variable `variable()` and `function()`, where latter maintains the function name.

When passing function as a parameter of a decorator, no parenthesis are needed like `function()`. This is because former passes function itself and latter passes return value of the function.

### `@` Symbol

A decorator symbol `@` used for pre-pending the function definition, placed before pre-decorated function.

| OPERATOR | EXAMPLE      | DESCRIPTION                                               |
| :------: | ------------ | --------------------------------------------------------- |
|   `@`    | `@decorator` | `@decorator` is a replacement of `func = decorator(func)` |

```python
# CREATING DECORATOR.
def decorator(func):
    def modified_function():
        """
        statements including func()
        """
    return function_modified

# DECORATING FUNCTION: @ SYMBOL
@decorator
def function():	# ORIGINAL FUNCTION OF "function()"
    statements

# FUNCTION NAME REMAINS THE SAME.
function()
```

Additionally, more than one decorator can be applied to a single pre-decorated function.

```python
@decorator0
@decorator1
def function():
    statements
```

A decorator located closest to pre-decorated function will be applied firsthand. Thus, the function object `function()` will first be decorated by `@decorator1`  then `@decorator0` sequentially.