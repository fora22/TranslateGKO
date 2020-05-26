# **PYTHON: BASIC**

Python is a high-level programming language with applications in numerous areas, including web programming, scientific computing, and artificial intelligence. The language is executed sequentially line-after-line and doesn't need semicolon `;` to end the line of statement.

This chapter describes on basic concepts and coding syntax used in Python.

##  Interpreter

Programming language such as C/C++ uses compiler that translates a source code (written in English) to a computer language (such as binary code) computer can understand and execute. However, interpreter allows computer to execute the program directly from a source code without translation.

Python is interpreter-driven high-level language: this allows scripting the code much easier than compiler, but its execution time can be slower in comparison.

### CPython

Originally, Python interpreter was developed using C programming language. This implementation is called CPython and is the most widely used implementation of all. Other notable implementations are Jython (Java-implementation), IronPython (.NET-implementation), and PyPy (Python-implementation).

While Python is introduced as an interpreter language, it actually uses both interpreter and compiler: CPython first processes Python code into intermediate bytecode which is than executed by CPython interpreter. Because of this, Python execution takes longer time on first run from compilation.

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

## Variable

Variable is a container for a data which can be assigned using assignment operator `=`. There are three different common stages in variable: declaration, definition, and initialization.

* **Declaration**
  : declaration is declaring existence of the construct of such as variables, functions, objects, and more. While declaration also includes specifying which data type the construct is in other languages, this is exception to Python since constructs in this language do not need to be declared with data type.

* **Definition**
  : definition refers to block of codes on values and performance the construct has and is capable of. In case of variable which can acquire new data, the term *assignment* is more likely to use.

  ```python
  # DEFINITION (+ DECLARATION) OF VARIABLE
  variable = 1
  
  # DEFINITION (+ DECLARATION) OF FUNCTION
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

Variable is not data-type fixed, allowing developers to change the value whatever and whenever using a single variable.

### Local & Global Variable

**Local variable** is a variable declared inside a code block, such as function or class. Data stored in local variable is destroyed when exiting the code block, thus cannot be used outside. This allows variable with the same name to be declared outside the code block.

**Global variable** is a variable declared outside of any code block on the script. Accessing the global variable in a code block is done using `global` keyword. However, global variable should be avoided if possible to prevent unexpected result and error caused by conflicting variables.

### Constant Variable

Constant variable is a special type of variable that cannot be changed after its initialization. Unfortunately, Python does not have a constant variable since it does not have a concept of *declaration*. While C-based language do have this feature, Python developer should just be careful not to mess up the what-is-used-as-constant variable.

Common method used in Python to indicate the constant variable is declaring the variable UPPERCASE.

### `del` Keyword

The `del` keyword is used to delete variable. Deleted variable can be reassigned later.

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
  : a constructs which can manipulate the value of operands, such as arithmetic operators. It operates simply by placing before, after, or between the operands.
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
| Subtraction                    |   `-`    | Python doesn’t have a subtraction. Negative sign substitutes subtraction, as adding negative value is equal to subtracting value. |
| Multiplication                 |   `*`    | -                                                            |
| Exponential                    |   `**`   | -                                                            |
| Division                       |   `/`    | When divided, the value implicitly (or automatically) converts to `float`. |
| Quotient (aka. floor division) |   `//`   | Outputs a quotient of division only, without a remainder.    |
| Remainder                      |   `%`    | Outputs a remainder of the division.                         |

For easier readability of the arithmetic operation, you can place blank spaces between number and operator as it does not affect on its output.

Additional operations are available using built-in functions and methods exclusive to numeric data type. Most of the operation below requires an iterable object called *list* which will be introduced later.

| FUNCTION  | EXAMPLE             | DESCRIPTION                                                  |
| --------- | ------------------- | ------------------------------------------------------------ |
| `abs()`   | `abs(-21)`          | Find out absolute value of the number.                       |
| `round()` | `round(164.2597,2)` | Rounds up the number to one’s digit on default, or to a fraction digit behind. |
| `max()`   | `max([0,1,2,3,4])`  | Find the maximum number inside.                              |
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

Assignment operator is a combination of an arithmetic and an assignment symbol `=`, making numerical calculation code to be written more concisely.

| OPERATOR | EXAMPLE  | EQUIVALENT                                                |
| :------: | -------- | --------------------------------------------------------- |
|   `=`    | `x = y`  | `x = y`; assigns a value of variable `y` to variable `x`. |
|   `+=`   | `x += y` | `x = x + y`                                               |
|   `-=`   | `x -= y` | `x = x - y`                                               |
|   `*=`   | `x *= y` | `x = x * y`                                               |
|   `/=`   | `x /= y` | `x = x / y`                                               |
|   `%=`   | `x %= y` | `x = x % y`                                               |

Increment and decrement does not exist in Python programming language.


# **파이썬(Python): 기초**
파이썬은 웹 프로그래밍, 컴퓨터 과학, 인공지능을 포함한 수많은 영역에서 응용 가능한 고급 프로그래밍 언어이다. 파이썬은 위에서부터 아래로 순차적으로 실행되며 코드 문(文) 끝에는 세미콜론(';')이 필요하지 않다.

본 챕터에서는 파이썬에서 사용되는 코딩 구문과 기초적인 개념에 대해 설명한다.

## 인터프리터
C/C++와 같은 프로그래밍 언어는 (영어로 쓰여진) 소스 코드를 컴퓨터가 이해하고 실행할 수 있는 (이진코드와 같은) 컴퓨터 언어로 번역하는데 컴파일러가 사용된다. 그러나 인터프리터는 컴퓨터 언어로의 번역 없이 소스코드에서 직접 프로그램을 실행한다.
<!-- 여기 문장이 조금 이상한듯 인터프리터도 번역을 하지 않나?-->

파이썬은 인터프리터로 동작하는 고급 언어이다. 비록 코드 작성은 컴파일러보다 쉽지만, 프로그램 실행 시간은 비교적 느리다.

### CPython
본래 파이썬 인터프리터는 C 언어를 기반하여 개발되었다. C 기반의 인터프리터를 'CPython'이라 부르며 가장 널리 사용된다. 다른 언어로 구현된 것으로 Jython(Java로 구현된 인터프리터), IronPython(.NET로 구현된 인터프리터), 그리고 PyPy(Python로 구현된 인터프리터) 등이 있다.

파이썬은 인터프리터 언어로 소개되었으나, 실제로는 인터프리터와 컴파일러 둘 다 사용한다. CPython은 우선 파이썬 코드를 바이트코드로 컴파일한 다음 CPython 인터프리터에 의해 실행된다. 이 때문에 파이썬의 첫 실행은 컴파일 작업으로 인해 시간이 더 걸린다.

## 주석
파이썬에는 한줄 주석과 블록 주석이 존재한다: 

* **한줄 주석** : 코드 한 줄을 차지하는 주석이며, `#`(해시 기호)로 표시된다.
* **블록 주석**(일명 독스트링) : 코드 여러 줄을 차지하는 주석이며, 세 쌍의 작은 따옴표 `''' '''` 혹은 큰 따옴표 `""" """`로 표시된다. 독스크링(docstrings)은 또한 여러 줄의 문장을 쓰는데 사용되기도 하며, 프로그램 실행 도중에도 볼 수 있다.

```Python
"""
블록 주석:
여기에 여러 줄 주석을 달 수 있고, 실행 시 볼 수 있다.
"""
# 줄 주석: 한줄 짜리 주석이다.
```

## 입력 & 출력
파이썬은 터미널의 텍스트 기반 입력 및 출력 함수를 가진다.

| 입력/출력 | 구문            | 설명                                                  |
| ------------ | ----------------- | ------------------------------------------------------------ |
| `input()`    | `input("쓰기:")` | 입력이 요구될 시 `input()` 함수 내에 있는 문자형 데이터가 터미널에 표시되며, 입력된 데이터는 항상 문자형으로 반환된다. |
| `print()`    | `print("읽기:",variable)` | 콘솔창에 자료형(예 : 문자, 숫자)을 출력한다. 여기서 `variable`은 연결을 위한 문자형 데이터이다. |

```python
variable = input("쓰기: ")
print("읽기:", variable)
# 동일한 기능: print("읽기:", input("쓰기: "))
```

```
쓰기: Hello World!
읽기: Hello World!
```
하나의 `print()` 함수에서 두 가지 이상의 자료형을 한 번에 출력하는 데 두 가지의 방법이 존재하며, 이들의 출력 방식은 약간 다르다.

1. 쉼표(`,`)를 사용하여 연속적으로 데이터를 나열할 수 있다. 하지만 항상 쉼표에는 공백이 놓여지게 된다.
    ```python
    A = 10.0
    B = "파이썬3"
    
    # 문자열과 정수의 혼합된 데이터를 쉼표(",")를 사용해 나열한다.
    print("A는", A , ", \n그리고 B는", B, "이다.")
    ```

    ```
    A는 10.0 ,
    그리고 B는 파이썬3 이다.
    ```


2. 문자열의 연결에서 `+`를 사용하면 사이에 공백이 생기지 않는다. 하지만, 문자열이 아닌 데이터 형식은 연결을 사용하려면 문자열로 변환해야 한다.

   ```python
   A = 10.0
   B = "파이썬3"
   
   # 문자열 변환 후, 문자열과 정수의 혼합된 데이터를 쉼표("'")를 사용해 나열했다.
   print("A는", str(A) + ", \n그리고 B 는", B + "이다.")
   ```

   ```
   A는 10.0,
   그리고 B는 파이썬3이다.
   ```

## 변수
변수는 할당 연산자('=')를 사용하여 데이터를 할당할 수 있는 저장공간이다. 변수에는 선언, 정의, 초기화 등 세 가지 공통 단계가 있다.


* **선언**
  : 선언은 변수, 함수, 객체 등의 존재를 선언하는 것이다. 다른 언어에서 선언은 어떠한 데이터 타입인지도 포함하지만, 파이썬에서는 예외적으로 데이터 타입으로 선언할 필요가 없다.

* **정의**
  : 정의는 코드 블록을 통해 구조물이 가지고 있고 할 수 있는 가치와 성능을 의미한다.


  ```python
  # 변수의 정의(+선언)
  variable = 1
  
  # 함수의 정의(+선언)
  def function():
    statements
    return 0
  ```
* **초기화**
  : 초기화는 초기 값을 구조에 할당하는 것이다. 단순하게 *first* 정의. 첫 번째 정의는 일반적으로 구주 선언과 동시에 이루어진다. 따라서, 초기화는 사람들의 생각에 의해 일반적으로 *선언 + 정의*라고 생각되지만, 항상 사실인 것은 아니다.


프로그래머는 파이썬에서 변수 이름 짓는 규칙을 준수해야 한다.

* 오직 글자, 숫자, 밑줄만 허용된다.

* 첫 글자가 숫자로 시작할 수 없다.

* 공백은 허용되지 않는다.

변수는 데이터 타입이 고정되어 있지 않아, 프로그래머가 원하는 모든 값으로, 원하는 시간에 단일 변수의 값을 변경할 수 있다.


### 지역 & 전역 변수

**지역 변수** 는 함수나 클래스로 된 코드 블록 내부에서 선언된 변수이다. 지역 변수에 저장된 데이터는 코드 블록을 종료할 때 제거되므로 외부에서 사용할 수 없다. 지역 변수는 외부에서 선언된 변수의 이름을 가질 수 있다.(기술적으로 다른 정체성으로 이름을 쓴다.)

**전역 변수**는 코드 블록 외부에 있는 스크립트의 글로벌 범위에 선언된 변수이다. `global` 키워드를 이용해 코드 블록 내부의 글로벌 변수를 활용할 수 있다. 단, 글로벌 변수는 가능하면 피해야 변수 충돌로 인한 예상치 못한 결과와 오류를 방지할 수 있다.

### 상수 변수

상수 변수는 초기화 후 변경할 수 없는 특별한 유형의 변수이다. 불행히도, 파이썬은 *선언*의 개념이 없기 때문에 상수 변수가 없다. C 기반 언어는 이러한 기능을 가지고 있지만, 파이썬 개발자는 단지 사용 가능한 그대로의 변수를 망치지 않도록 주의해야 한다.

파이썬에서 상수 변수를 나타내기 위해 사용되는 일반적인 방법은 변수 UPERCASE를 선언하는 것이다.


### `del` 키워드

이 키워드는 변수를 삭제 할 때 사용한다.
삭제된 변수는 나중에 다시 할당할 수 있다.

```python
# "x" 변수의 정의
x = "Python"
print(x)

# "x" 변수의 삭제
del x
print(x)
```

```
Python
NameError: name 'x' is not defined
```

## 데이터 타입

변수가 파이썬에 저장할 수 있는 데이터 타입은 숫자, 문자열, 불 데이터 타입 등 세가지 유형으로 분류할 수 있다. 데이터 유형에 따라 파이썬은 *operation*이라 하는 데이터 처리 타입별 기능을 수행할 수 있따. 데이터를 조작할 수 있는 것은 (1) 연산자, (2) 함수, (3) 메서드 등이다.

비록 함수와 메서드는 후반부에 소개될 것이지만, 이 세가지 사이의 주요 차이점을 아는 것은 프로그래밍 언어의 개념을 전반적으로 이해하는 데 있어서 혼동을 예방할 것이다.


  
* **연산자**
  : 산술 부호와 같이 피연산자의 값을 조작할 수 있는 것. 작동에 대한 논쟁이 필요 없고 피연산자의 앞, 뒤 또는 사이에 배치한다.

* **함수**
  : 동작하는 이름으로 불리는 재사용 가능한 코드 조각. 함수는 함수 이름의 접미사에서 괄호 `()`로 연산자와 구별할 수 있다. `function()`

* **메서드**
  : 객체 변환 함수. 메서드 또한 이름 접미사에 괄호 `()`가 있지만 항상 객체에 묶여 있다. `object.method()` 
  
### 숫자 데이터 타입

숫자 데이터 타입은 그래프, 연산처리, 인공지능의 뉴럴 네트워크 모델링 등 과학적인 목적으로 파있너에서 널리 사용되고 있다. 다음은 숫자 데이터 타입 목록이다:

| 키워드   | 데이터 타입             | 설명                                                  |
| --------- | --------------------- | ------------------------------------------------------------ |
| `int`     | 정수               | 32 비트 정밀 정수이다.<br /> 크기 : 제한 없음(최대. 400bytes) |
| `float`   | 부동 소수점 수 | 소수점을 포함한 실수.<br />크기: 제한 없음 (최대. 400bytes) |
| `complex` | 복소수        | 부동 소수점 수와 허수를 포함한 수.<br />제한 없음 (최대. 400bytes) |

숫자 데이터 타입의 바이트 크기는 다른 언어에서 보다 크다. 이것은 숫자 데이터 타입이 가질 수 있는 최대 바이트 크기일 뿐이고 숫자가 얼마인지에 따라 훨씬 더 작을 수 있다. 이러한 바이트 크기의 유연성은 파이썬에 데이터 타입 선언이 필요하지 않게 만든다.

`float` 데이터 타입은 `complex` 외에 분수를 표한할 수 있는 가장 작은 데이터 타입이기 때문에 일반적으로 사용되는 숫자 데이터 타입 중 하나이다. `float` 데이터 타입에는 다음과 같은 특징이 있다.


* 숫자 끝에 있는 추가 0(십진점 바로 뒤에 있음)은 무시된다.
* 다음과 같은 경우 `float` 데이터 타입으로 계산결과를 자동으로 반환한다.
  * `float`를 하나라도 포함하는 연산
  * `int`의 나눗셈 연산.

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
| Subtraction                    |   `-`    | Python doesn’t have a subtraction. Negative sign substitutes subtraction, as adding negative value is equal to subtracting value. |
| Multiplication                 |   `*`    | -                                                            |
| Exponential                    |   `**`   | -                                                            |
| Division                       |   `/`    | When divided, the value implicitly (or automatically) converts to `float`. |
| Quotient (aka. floor division) |   `//`   | Outputs a quotient of division only, without a remainder.    |
| Remainder                      |   `%`    | Outputs a remainder of the division.                         |

For easier readability of the arithmetic operation, you can place blank spaces between number and operator as it does not affect on its output.

Additional operations are available using built-in functions and methods exclusive to numeric data type. Most of the operation below requires an iterable object called *list* which will be introduced later.

| FUNCTION  | EXAMPLE             | DESCRIPTION                                                  |
| --------- | ------------------- | ------------------------------------------------------------ |
| `abs()`   | `abs(-21)`          | Find out absolute value of the number.                       |
| `round()` | `round(164.2597,2)` | Rounds up the number to one’s digit on default, or to a fraction digit behind. |
| `max()`   | `max([0,1,2,3,4])`  | Find the maximum number inside.                              |
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

Assignment operator is a combination of an arithmetic and an assignment symbol `=`, making numerical calculation code to be written more concisely.

| OPERATOR | EXAMPLE  | EQUIVALENT                                                |
| :------: | -------- | --------------------------------------------------------- |
|   `=`    | `x = y`  | `x = y`; assigns a value of variable `y` to variable `x`. |
|   `+=`   | `x += y` | `x = x + y`                                               |
|   `-=`   | `x -= y` | `x = x - y`                                               |
|   `*=`   | `x *= y` | `x = x * y`                                               |
|   `/=`   | `x /= y` | `x = x / y`                                               |
|   `%=`   | `x %= y` | `x = x % y`                                               |

Increment and decrement does not exist in Python programming language.

### Boolean Data Type

Boolean data type is useful for a code that requires logical conditioning whether the statement is true or false:

| VALUE          | NAME            | DESCRIPTION                   |
| -------------- | --------------- | ----------------------------- |
| `True` or `1`  | Logically true  | Returned when logic is true.  |
| `False` or `0` | Logically false | Returned when logic is false. |

Any non-zero positive number can represents Boolean value of `True`. In other word, Boolean value of `2` or `3` are also equivalent to `True` while `False` is only represented by the number `0`.

Comparison operator is used to compare relation of two or more values, returning corresponding Boolean data type depending on whether the condition is held true or false. 

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

String data type is a text-based data which can be distinguished by a pair of single quotation mark `''` or double quotation mark `""`. Variable or data that is a string data type is commonly called *string object*.

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
| `split()`      | `str.split([str1])`      | Convert a string `str` to a list by separating based on blank spaces if there's no argument in method.<br /><br />*[OPTIONAL: In case there’s an argument `str1`, the string object `str` is separated based on `str1`.]* |
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

It is possible to convert a data type to another different data type. The following three are the conversion widely used when developing Python program:

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

Not just to escape from unwanted operation, escape character is also used to code a single long line of code into short consecutive multi-line code.

## None

An data with no value regardless of data type. Although `None` can be used as `False` in Boolean logic conditioning, `None` and `False` is completely different even in Boolean concept.

```python
# CONDITIONAL CHECK: can None be deemed as False in Boolean?
if not(None and True):
    print(None)
```

```
None                    # This proves that None can be used as False in Boolean.
```