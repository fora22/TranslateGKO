# **PYTHON: BASIC**

Python is a high-level programming language with applications in numerous areas, including web programming, scientific computing, and artificial intelligence. The language is executed sequentially line-after-line and doesn't need semicolon `;` to end the line of statement.

This chapter describes on basic concepts and coding syntax used in Python.

# **파이썬(Python): 기초**
파이썬은 웹 프로그래밍, 컴퓨터 과학, 인공지능을 포함한 수많은 영역에서 응용 가능한 고급 프로그래밍 언어이다. 파이썬은 줄-다음-줄로 순차적으로 실행되며 줄의 끝에 세미콜론(';')이 필요하지 않다.

이 챕터에서는 파이썬에서 사용되는 코딩 구문과 기초적인 개념에 대해 설명하려 한다.



##  Interpreter

Programming language such as C/C++ uses compiler that translates a source code (written in English) to a computer language (such as binary language) computer can understand for execution. However, interpreter allows computer to execute the program directly from a source code without translation.

Python is interpreter-driven high-level language: this allows scripting the code much easier than compiler, but its execution time can be slower in comparison.

## 인터프리터
C/C++과 같은 프로그래밍 언어는 소스 코드(영어로 쓰여진)를 컴퓨터가 이해하고 실행할 수 있는 컴퓨터 언어(이진언어와 같이)로 번역하는데 컴파일러를 사용한다. 그러나, 인터프리터는 컴퓨터가 번역 없이 소스코드에서 직접 프로그램을 실행할 수 있도록 한다.
<!-- 여기 문장이 조금 이상한듯
인터프리터도 번역을 하지 않나?-->

파이썬은 인터프리터로 동작하는 고수준 언어: 코드를 작성할 때 컴파일러보다 쉽지만, 실행 시간에 있어서 비교했을 때 느리다.

### CPython

Originally, Python interpreter was developed using C programming language. This implementation is called CPython and is the most widely used implementation of all. Other implementations are Jython (Java-implementation), IronPython (.NET-implementation), PyPy (Python-implementation), and more.

While Python is introduced as an interpreter language, it actually is both interpreter and compiler: CPython first processes Python code into intermediate bytecode which is than executed by CPython interpreter. Because of this, Python execution takes longer time on first run from compilation.

### CPython (C-파이썬)

원래, 파이썬 인터프리터는 C 언어를 사용하여 개발되었다. 이렇게 구현된 것을 'CPython'이라 불리며 가장 널리 사용된다. 다른 언어로 구현된 것은 Jython(Java로 구현된 인터프리터), IronPython(.NET로 구현된 인터프리터), PyPy(Python로 구현된 인터프리터) 등 이 있다.

파이썬은 인터프티 언어로 소개되지만, 실제로 인터프리터와 컴파일러 둘 다 해당된다: CPython은 먼저 파이썬 코드를 CPython 인터프리터에 의해 실행되기 전에 중간 바이트 코드로 처리한다. 이 때문에 파이썬의 실행은 첫 컴파일로부터 더 오랜 시간이 걸린다.

## Comment

There are two different comments in Python: line comment and block comment.

* **Line comment**
  : a comment worth a single line of code, and is declared by `#` (octothorpe).
* **Block comment** (aka. **docstrings**)
  : a comment with multiple lines of code by using three pairs of double quote `""" """` or single quote `''' '''`. Docstrings can even be used to write multiple lines of sentence and view it on runtime.

```python
"""
BLOCK COMMENT:
multiple line of comment can be placed here and can even be viewed on runtime.
"""
# LINE COMMENT: for a single line of code.
```
## 주석


파이썬에는 다른 두 가지 주석이 있다 : 줄 주석과 블록 주석

* **줄 주석** : 코드 한 줄짜리 주석, `#`(octothorpe, 샵, 해시태그 등)에 의해 선언된다.
* **블록 주석**(별명. docstrings) : 작은 따옴표 3개 `''' '''`나 큰 따옴표 3개 `""" """`를 사용해서 여러 줄 주석을 할 수 있다. Docstrings는 또한 여러 줄의 문장을 쓰는데 사용될 수 있고, 실행할 때 볼 수 있다.

```Python
"""
블록 주석:
여기에 여러 줄 주석을 달 수 있고, 실행 시 볼 수 있다.
"""
# 줄 주석: 한줄 짜리 주석이다.
```

## Input & Output

Python has a single input and output function for a terminal text-based:

| INPUT/OUTPUT | SYNTAX            | DESCRIPTION                                                  |
| ------------ | ----------------- | ------------------------------------------------------------ |
| `input()`    | `input("Write:")` | Text data inside a function `input()` is shown on a terminal when input is needed, and always return input data as text. |
| `print()`    | `print("Read:",variable)` | Print data types (e.g. text, number) on a console, where `variable` is a text data for concatenation. |

```python
variable = input("Write: ")
print("Read:", variable)
# EQUIVALENT: print("Read:", input("Write: "))
```

```
Write: Hello World!
Read: Hello World!
```

To print mixture of more than a single data type in a single `print()` function, there are two possible methods with slightly different results.

1. Using a comma `,` can list the data in sequence but always places blank space on each comma.

   ```python
   A = 10.0
   B = "Python3"
   
   # MIXTURE OF STRING AND INT IS LISTED USING COMMA ",".
   print("A is", A , ", \nand B is", B, ".")
   ```

   ```
   A is 10.0 ,
   and B is Python3 .
   ```

2. Concatenation of string using `+` and does not create blank space between. However, data type that is not a string needs to be converted to string to use a concatenation.

   ```python
   A = 10.0
   B = "Python3"
   
   # MIXTURE OF STRING AND INT IS CONCATENATED USING "+" AFTER STRING CONVERSION.
   print("A is", str(A) + ", \nand B is", B + ".")
   ```

   ```
   A is 10.0,
   and B is Python3.
   ```

## 입력 & 출력

파이썬은 터미날 텍스트 기반으로 된 단일 입력, 출력 함수를 가지고 있다.

| 입력/출력 | 구문            | 설명                                                  |
| ------------ | ----------------- | ------------------------------------------------------------ |
| `input()`    | `input("쓰기:")` | 입력이 필요할 때 텍스트 데이터를 `input()`함수에 넣으면 터미널에 표시되며, 항상 입력한 데이터는 텍스트의 형태로 반환된다. |
| `print()`    | `print("읽기:",변수)` | 콘솔에서 데이터 타입(예 : 텍스트, 번호)을 출력한다. 여기서 `변수`는 연결을 위한 텍스트 데이터이다. |

```python
variable = input("쓰기: ")
print("읽기:", variable)
# 동일한 기능: print("읽기:", input("쓰기: "))
```

```
쓰기: Hello World!
읽기: Hello World!
```
단일 `print()` 함수를 사용하여 혼합된 단일 데이터 유형을 출력하려 하면, 약간의 다른 결과가 나오지만 두 가지의 방법이 있다.

1. 쉼표(`'`)를 사용하여 연속적으로 데이터를 나열할 수 있다. 하지만 항상 쉼표에는 공백이 놓여지게 된다.
    ```python
    A = 10.0
    B = "Python3"
    
    # 문자열과 정수의 혼합된 데이터를 쉼표("'")를 사용해 나열했다.
    print("A is", A , ", \nand B is", B, ".")
    ```

    ```
    A is 10.0 ,
    and B is Python3 .
    ```


2. 문자열의 연결에서 `+`를 사용하면 사이에 공백이 생기지 않는다. 하지만, 문자열이 아닌 데이터 형식은 연결을 사용하려면 문자열로 변환해야 한다.

   ```python
   A = 10.0
   B = "Python3"
   
   # 문자열 변환 후, 문자열과 정수의 혼합된 데이터를 쉼표("'")를 사용해 나열했다.
   print("A is", str(A) + ", \nand B is", B + ".")
   ```

   ```
   A is 10.0,
   and B is Python3.
   ```

## Variable

Variable is a container for the data which can be assigned using assignment operator `=`. There are three different common stages in variable: declaration, definition, and initialization.

* **Declaration**
  : declaration is declaring existence of the construct of such as variables, functions, objects, and more. While declaration also includes specifying which data type the construct is in other languages, this is exception to Python since constructs in this language do not need to be declared with data type.

* **Definition**
  : definition refers to block of codes on values and performance the construct has and is capable of.

  ```python
  # DEFINITION (+DECLARATION) OF VARIABLE
  variable = 1
  
  # DEFINITION (+DECLARATION) OF FUNCTION
  def function():
    statements
      return 0
  ```
  
* **Initialization**
  : initialization is assigning the initial value to the construct, simply the *first* definition. The first definition is generally done on the same time when declaring the construct. Hence, initialization is commonly thought by people as *declaration + definition*, but is not always true.

Programmer should observe the rules on naming variable in Python:

* Only letters, numbers, and underscores are allowed.

* Name cannot start with numbers.

* Spaces are not allowed.

Variables are not data-type fixed, allowing programmer to change the value whatever and whenever they want even from a single variable.

### Local & Global Variable

**Local variable** is a variable declared inside a code block, such as function or class. Data stored in local variable is removed when exiting the code block, thus cannot be used outside. Local variable is allowed to have same variable name declared outside (technically, is borrowing the name as a different identity).

**Global variable** is a variable declared on a global scope of the script which is outside a code block. It is possible to use the global variable inside a code block using `global` keyword. However, global variable should be avoided if possible to prevent unexpected result and error caused by conflicting variables.

### Constant Variable

Constant variable is a special type of variable that cannot be changed after its initialization. Unfortunately, Python does not have a constant variable since Python does not have a concept of *declaration*. While C-based language do have this feature, Python developer should just be careful not to mess up the what-is-used-as-constant variable.

Common method used in Python to indicate the constant variable is declaring the variable UPPERCASE.

### `del` Keyword

A keyword used to delete variable. Deleted variable can be reassigned later.

```python
# DECLARATION OF THE VARIABLE "x"
x = "Python"
print(x)

# DELETION OF THE VARIABLE "x"
del x
print(x)
```

```
Python
NameError: name 'x' is not defined
```

## Data Type

Data type a variable can store in Python can be categorized into three different type: numeric, string, and Boolean data type. Depending on the data type, Python can perform type-specific features that process the data, called *operation*. Those that can operates data are (1) operator, (2) function, and (3) method.

Although a function and a method will be introduced in later chapter, knowing the key difference between these three will prevent getting confused on understanding concepts of programming language overall.

* **Operator**
  : a constructs which can manipulate the value of operands, such as an arithmetic sign. It does not need argument to operates but by placing before, after, or between the operands.
* **Function**
  : a reusable piece of code which is called by name to operates. Function can be distinguished from an operator by parenthesis `()` at suffix of the function's name; `function()`.
* **Method**
  : an object-exclusive function. Method also has parenthesis `()` at suffix of its name but is always bounded to an object; `object.method()`.

### Numeric Data Type

Numeric data type is widely used in Python for scientific purpose such as plotting, processing, and on the field of modeling neural network in artificial intelligence. Following are the list of numeric data types:

| KEYWORD   | DATA TYPE             | DESCRIPTION                                                  |
| --------- | --------------------- | ------------------------------------------------------------ |
| `int`     | Integer               | 32-bits precision integer number.<br />Size: unlimited (max. 400 bytes) |
| `float`   | Floating point number | Real number with decimal points.<br />Size: unlimited (max. 400 bytes) |
| `complex` | Complex number        | Contains floating real and imaginary number.<br />Size: unlimited (max. 400 bytes) |

The byte size of numeric data type is greater than any other languages. This is just a maximum byte size numeric data type can have and it can be much smaller depending on the what the number is. This flexibility of the byte size makes Python doesn't require data type declaration.

Data type `float` is one of the commonly used numeric data type as it’s the smallest data type that can express the fraction besides `complex`. The `float` data type has following properties:

* Extra zeros (beside right behind the decimal point) at end of the number are ignored.
* Calculation returns `float` data type automatically when…
  * Arithmetic operation involving even one single `float`.
  * Division of `int`.

```python
print(9.8765000)
print(4 ** 2.0)
print(4 + 1.0)
```

```
9.8765
16.0
5.0
```

Arithmetic operation of a numeric data type is as follows:

| NAME                           | OPERATOR | DESCRIPTION                                                  |
| ------------------------------ | :------: | ------------------------------------------------------------ |
| Addition                       |   `+`    | -                                                            |
| Subtraction                    |   `-`    | Python doesn’t have a subtraction. Instead, negative sign substitutes subtraction, as adding negative value is equal to subtracting. |
| Multiplication                 |   `*`    | -                                                            |
| Exponential                    |   `**`   | -                                                            |
| Division                       |   `/`    | When divided, the value automatically changes to data type of `float`, a data type of number with decimal point. |
| Quotient (aka. floor division) |   `//`   | When divided, gives an output a quotient of division only, without a remainder. |
| Remainder                      |   `%`    | When divided, gives an output a remainder of the division.   |

For easier readability of the arithmetic operation, you can place blank spaces between number and operator as it does not affect anything on its output.

Additional operations using with built-in functions and methods exclusive to numeric data type. Most of the operation below requires an iteratable object called *list* which will be introduced later.

| FUNCTION  | EXAMPLE             | DESCRIPTION                                                  |
| --------- | ------------------- | ------------------------------------------------------------ |
| `max()`   | `max([0,1,2,3,4])`  | Find the maximum number inside.                              |
| `min()`   | `min([0,1,2,3,4])`  | Find the minimum number inside.                              |
| `abs()`   | `abs(-21)`          | Find out absolute value of the number.                       |
| `round()` | `round(164.2597,2)` | Rounds up the number to one’s digit on default, or to a fraction digit behind. |
| `sum()`   | `sum([0,1,2,3,4])`  | Sum all the numbers in the list.                             |

```python
# EXAMPLE OF ROUND() FUNCTION
print(round(164.259763145))
print(round(164.259763145,2))
```

```
164
164.26
```

Assignment operator is a combination of an arithmetic and an assignment sign `=`, making numerical calculation code to be written more concisely.

| OPERATOR | EXAMPLE  | EQUIVALENT                                                   |
| :------: | -------- | ------------------------------------------------------------ |
|   `=`    | `x = y`  | `x = y`; assign the value of variable `y` to the variable `x`. |
|   `+=`   | `x += y` | `x = x + y`                                                  |
|   `-=`   | `x -= y` | `x = x - y`                                                  |
|   `*=`   | `x *= y` | `x = x * y`                                                  |
|   `/=`   | `x /= y` | `x = x / y`                                                  |
|   `%=`   | `x %= y` | `x = x % y`                                                  |

Increment and decrement does not exist in Python programming language.

### Boolean Data Type

Boolean data type is useful for a code that requires logical conditioning whether it is true or false:

| VALUE          | NAME            | DESCRIPTION                   |
| -------------- | --------------- | ----------------------------- |
| `True` or `1`  | Logically true  | Returned when logic is true.  |
| `False` or `0` | Logically false | Returned when logic is false. |

Any non-zero positive number can represents Boolean value of `True`. In other word, Boolean value of `2` or `3` are also equivalent to `True` while `False` is only represented by the number `0`.

Comparison operation is used to compare relation of two or more values, returning corresponding Boolean data type depending on whether the condition is held true or false. 

| OPERATOR | DESCRIPTION              |
| -------- | ------------------------ |
| `<`      | Lesser than              |
| `<=`     | Lesser than or equal to  |
| `>`      | Greater than             |
| `>=`     | Greater than or equal to |
| `==`     | Equal to                 |
| `!=`     | Not equal to             |

Meanwhile, the Boolean data type can be added, multiplied, and complemented as follows:

| OPERATOR | NAME           | DESCRIPTION                                             |
| :------: | -------------- | ------------------------------------------------------- |
|   `is`   | Equivalence    | Boolean evaluator between two data: equivalent to `==`. |
|  `and`   | Multiplication | True when all the arguments are True, else False.       |
|   `or`   | Addition       | True when at least one argument is True, else False.    |
|  `not`   | Complement     | Change True to False and vice versa.                    |

### String Data Type

String data type is a text-based data which can be distinguished with other data type by a pair of single quotation mark `''` or double quotation mark `""`. Variable or data that is a string data type is commonly called *string object*.

Although placing the quotation mark inside a string object can cause broken string data, placing a backslash `\` before the quotation mark can escape from premature end of string.

```python
# COMPARISON BETWEEN IMPROPER AND PROPER WAY OF TYPING STRINGS.
print('Where's my "Cat in the Hat" book?')
print('Where\'s my "Cat in the Hat" book?')
```

```
Where
Where's my "Cat in the Hat" book?
```

Create a string with three sets of quotes (either single or double) becomes docstring; docstring can create a newlines just by pressing Enter/Return button. Otherwise, developer need to insert `\n` code manually.

```python
# PRINTING AND WRITING STRING IN MULTIPLE LINES.
print("Thank you!\nYou're welcome.")
print("""Thank you!
You're welcome.""")
```

```
Thank you!
You're welcome.
Thank you!
You're welcome.
```

String objects in Python can be added and multiplied like a number data type:

| OPERATOR | NAME           | DESCRIPTION                                                  |
| :------: | -------------- | ------------------------------------------------------------ |
|   `+`    | Concatenation  | Merge two different strings to one (type of quote doesn’t matter). |
|   `*`    | Multiplication | Multiply the string by the number of integer (float does not work). |

```python
print("Pyt" + 'hon')
print(4 * "2")
```

```
Python
2222
```

String is an object (or simply, an independent individual of data), thus string has its own unique operations that has not been introduced in previous two data types:


| METHOD         | EXAMPLE                  | DESCRIPTION                                                  |
| -------------- | ------------------------ | ------------------------------------------------------------ |
| `format()`     | `str.format(data)`       | Inserts string or non-string `data` type to a designated space via location or name designated by `{}`. |
| `join()`       | `str.join(str_lst)`      | Joins a list of string objects `str_lst` by placing string object `str` in-between. |
| `split()`      | `str.split([str1])`      | Convert a string `str` to a list by separating based on blank spaces if there's no argument in method.<br /><br />[OPTIONAL: In case there’s an argument `str1`, the string object `str` is separated based on `str1`.] |
| `replace()`    | `str.replace(str1,str2)` | Replace `str1` to `str2` within the string object `str`.     |
| `startswith()` | `str.startswith()`       | Check the start of the `str` for equivalence.                |
| `endswith()`   | `str.endswith()`         | Check the end of the `str` for equivalence.                  |
| `upper()`      | `str.upper()`            | Change every text in `str` to uppercase letter.              |
| `lower()`      | `str.lower()`            | Change every text in `str` to lowercase letter.              |


```python
# STRING FORMAT: [1] BY-LOCATION & [2] BY-NAME ASSIGNMENT
lst = [str0, int1, int2]
print("{2} {0} {1}".format(lst[0], lst[2], lst[1]))
print("{x} {y} {z}".format(x = lst[0], y = lst[2], z = lst[1]))

# STRING CONCATENATION
print(" ! ".join([str0, str1, str2]))
print("str0 ! str1 ! str2".split(" ! "))

# CHECK-UP FOR THE STRING
print("This is a sentence.".startswith("this"))
print("This is a sentence.".endswith("sentence."))

# ALPHABET UPPER/LOWERCASE
print("This is a SENTENCE.".upper())
print("This is a SENTENCE.".lower())
```

```
int1 str0 int2
str0 int2 int1

str0 ! str1 ! str2
[str0, str1, str2]

False       # False as the first letter "t" is not capitalized.
True        # True as it also includes a period at the end.

THIS IS A SENTENCE.
this is a sentence.
```
### Type Conversion

It is possible to convert one's data type to another different data type. The following three are the conversion widely used when developing Python program:

| FUNCTION  | NAME               | DESCRIPTION                                                  |
| --------- | ------------------ | ------------------------------------------------------------ |
| `int()`   | Convert to integer | `float`: Fraction is eliminated, returning integer only.<br />`string`: Only numerical characters are convertible. |
| `float()` | Convert to float   | `int`: No restriction.<br />`string`: Only numerical characters are convertible. |
| `str()`   | Convert to string  | `int`: No restriction.<br />`float`: No restriction.         |

## Escape Character

Escape character `\` is used to escape from execution of operation intended for an operator. On introduction on string data type, `\'` is used to prevent string from premature ending.

| SYNTAX | DESCRIPTION    |
| ------ | -------------- |
| `\n`   | New line       |
| `\t`   | Horizontal tab |
| `\\`   | Backslash      |
| `\b`   | Backspace      |
| `\'`   | Single quote   |
| `\"`   | Double quote   |

Not just to escape from unwanted operation, escape character is also used to code a single long command into short consecutive multi-line commands.

## None

An data with no value regardless of data type. Although `None` can be used as `False` in Boolean logic conditioning, `None` and `False` is completely different even in Boolean concept.

```python
# CONDITIONAL CHECK: is None can be deemed as False in Boolean?
if not(None and True):
	print(None)
```

```
None                    # This proves that None can be used as False in Boolean.
```
