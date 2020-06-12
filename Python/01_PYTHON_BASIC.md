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

숫자 데이터 유형의 산술 연산은 다음과 같다:

| 이름                           | 연산자 | 설명                                                  |
| ------------------------------ | :------: | ------------------------------------------------------------ |
| 더하기                       |   `+`    | -                                                            |
| 빼기                    |   `-`    |  파이썬은 뺄셈이 없다. 음수 기호는 음수 값을 추가하는 것이 감산 값과 같기 때문에 감산을 대체한다. |
| 곱하기                 |   `*`    | -                                                            |
| 제곱                    |   `**`   | -                                                            |
| 나누기                       |   `/`    |  나누면 값이 암시적으로(또는 자동으로) `float` 형으로 변환된다. |
| 몫 |   `//`   | 나머지 부분 없이 몫만 출력된다.    |
| 나머지                     |   `%`    | 나눗셈의 나머지만 출력된다.                         |

산술 연산을 쉽게 읽을 수 있도록 숫자 사이에 공백을 넣을 수 있다. 이 공백은 숫자 및 연산자 출력에 영향을 주지 않는다.

숫자 자료형에 국한된 내장 함수 및 메서드를 사용하여 추가적인 작업을 수행할 수 있다. 아래 대부분의 작업에는 *list* 라는 이터러블 객체가 필요하며 이 객체는 나중에 소개할 것이다.

| 함수  | 예시             | 설명                                                  |
| --------- | ------------------- | ------------------------------------------------------------ |
| `abs()`   | `abs(-21)`          | 숫자의 절댓값을 구한다.                       |
| `round()` | `round(164.2597,2)` | 기본적으로 한 자릿수로 숫자를 반올림하거나 뒤의 소수 자릿수로 반올림한다. |
| `max()`   | `max([0,1,2,3,4])`  | 가장 큰 숫자를 구한다.                              |
| `sum()`   | `sum([0,1,2,3,4])`  | list에서 숫자를 모두 더한다.                             |

```python
# ROUND() 함수의 예
print(round(164.259763145))
print(round(164.259763145,2))
```

```
164
164.26
```

할당 연산자는 산술과 할당 기호 `=`의 조합으로, 숫자 계산 코드를 보다 간결하게 작성하게 한다.

| 연산자 | 예시  | 동일한 코드                                                |
| :------: | -------- | --------------------------------------------------------- |
|   `=`    | `x = y`  | `x = y`;    `x`에 `y`변수의 값을 할당한다. |
|   `+=`   | `x += y` | `x = x + y`                                               |
|   `-=`   | `x -= y` | `x = x - y`                                               |
|   `*=`   | `x *= y` | `x = x * y`                                               |
|   `/=`   | `x /= y` | `x = x / y`                                               |
|   `%=`   | `x %= y` | `x = x % y`                                               |

파이썬 프로그래밍 언어에는 증분 및 감소가 없다.

### 논리형 데이터 타입

논리형 데이터 타입은 문장이 참인지 거짓인지 논리적 조건화가 필요한 코드에 유용하다.

| 값          | 이름            | 설명                   |
| -------------- | --------------- | ----------------------------- |
| `True` or `1`  | 논리적 참  | 논리가 참일 때 반환.  |
| `False` or `0` | 논리적 거짓 | 논리가 거짓일 때 반환. |

0이 아닌 양수는 `True`에 논리형 값을 나타낼 수 있따. 즉, 논리형 `2` 또는 `3`은 `True`와 같고 거짓(`False`)은 숫자 `0`으로만 표현 된다.

비교 연산자는 둘 이상의 값의 관계를 비교하는데 사용되며, 조건이 참인지 거짓인지 여부에 따라 해당하는 논리형 데이터 타입을 반환한다.

| 연산자 | 표현              |
| -------- | ------------------------ |
| `<`      | 보다 작음              |
| `<=`     | 보다 작거나 같음  |
| `>`      | 보다 큼             |
| `>=`     | 보다 크거나 같음 |
| `==`     | 같음                 |
| `!=`     | 같지 않음             |

한편, 다음과 같이 논리형 데이터 타입을 추가, 증분 및 보완할 수 있다.

| 연산자 | 이름           | 표현                                             |
| :------: | -------------- | ------------------------------------------------------- |
|   `is`   | 등가    | 두 데이터 사이의 논리형 평가기이다. `==`와 동일하다.|
|  `and`   | 곱하기 | 모든 인수가 True이면 True이고 그렇지 않으면 False이다.       |
|   `or`   | 더하기       | 하나 이상의 인수가 True이면 True이고 그렇지 않으면 False이다.    |
|  `not`   | 보충     | True를 False로 변경하거나 False로 변경한다.                    |

### 문자열 데이터 타입

문자열 데이터 유형은 단일 따옴표 `''` 또는 큰따옴표 `""`로 구분할 수 있는 텍스트 기반 데이터이다. 문자열 데이터 유형인 변수 또는 데이터를 일반적으로 *문자열 객체* 라고 한다.

문자열 개체 내부에 따옴표를 배치하면 문자열 데이터가 손상될 수 있지만 따옴표 앞에 `\`를 배치하면 문자열을 유지할 수 있다.

```python
# 입력 문자열의 부적절한 방법과 적절한 방법을 비교.
print('Where's my "Cat in the Hat" book?')
print('Where\'s my "Cat in the Hat" book?')
```

```
Where
Where's my "Cat in the Hat" book?
```

따옴표 세 집합(단일 또는 이중)이 있는 문자열을 만든다. 문서 문자열은 Enter/Return 버튼을 누르는 것만으로도 새 줄을 만들 수 있다. 그렇지 않으면 개발자가 수동으로 `\n` 코드를 삽입해야 한다.

```python
# 여러 줄로 문자열을 인쇄하고 씀
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

Python의 문자열 개체를 숫자 데이터 유형처럼 추가하고 곱할 수 있다:

| 연산자 | 이름           | 표현                                                  |
| :------: | -------------- | ------------------------------------------------------------ |
|   `+`    | 연쇄  | 서로 다른 두 문자열을 하나의 문자열에 병합한다(따옴표 유형은 중요하지 않다). |
|   `*`    | 곱하기 | 문자열을 정수 수로 곱한다(float는 동작하지 않음)). |

```python
print("Pyt" + 'hon')
print(4 * "2")
```

```
Python
2222
```

문자열은 객체(또는 단순히 데이터의 독립적인 개체)이므로 이전 두 데이터 유형에는 적용되지 않은 고유한 작업을 가진다.


| 메서드         | 예                  | 설명                                                  |
| -------------- | ------------------------ | ------------------------------------------------------------ |
| `format()`     | `str.format(data)`       | 문자열 또는 비 문자열 `data` 유형을 `{}` 에서 지정한 위치에 삽입한다. |
| `join()`       | `str.join(str_lst)`      | 문자열 객체 `str`를 중간에 배치하여 문자열 객체 `str_lst` list에 결합한다. |
| `split()`      | `str.split([str1])`      | 메서드에 인수가 없는 경우 공백에 따라 구분하여 문자열 `str`를 목록으로 변환합니다.<br/>*[옵션: `str1`] 인수가 있을 경우 문자열 개체인 `str`은 `str1`을 기준으로 구분된다.]* |
| `replace()`    | `str.replace(str1,str2)` | 문자열 객체인 `str`에서 `str1`을 `str2`로 바꾼다.     |
| `startswith()` | `str.startswith()`       | `str`의 시작에서 동등성을 확인한다.
            |
| `endswith()`   | `str.endswith()`         | `str`의 끝에서 동등성을 확인한다.                  |
| `upper()`      | `str.upper()`            | `str`의 모든 텍스트를 대문자로 변경한다.              |
| `lower()`      | `str.lower()`            | `str`의 모든 텍스트를 소문자로 변경한다.              |


```python
# 문자열 형식: [1] 위치별 및 [2] 이름별 할당.
lst = [str0, int1, int2]
print("{2} {0} {1}".format(lst[0], lst[2], lst[1]))
print("{x} {y} {z}".format(x = lst[0], y = lst[2], z = lst[1]))

# 문자열 연쇄
print(" ! ".join([str0, str1, str2]))
print("str0 ! str1 ! str2".split(" ! "))

# 문자열 확인
print("This is a sentence.".startswith("this"))
print("This is a sentence.".endswith("sentence."))

# 알파벳 대문자/소문자 구분
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
데이터 유형을 다른 데이터 유형으로 변환할 수 있다. 다음은 Python 프로그램을 개발할 때 널리 사용되는 변환이다.

| 함수  | 이름               | 설명                                                  |
| --------- | ------------------ | ------------------------------------------------------------ |
| `int()`   | 정수로 변환 | `float`: 분수는 제거되고 정수만 반환됨<br />`string`: 숫자만 변환할 수 있음. |
| `float()` | 실수로 변환   | `int`: 제한 없음.<br />`string`: 숫자만 변환할 수 있음  |
| `str()`   | 문자로 변환  | `int`: 제한 없음.<br />`float`: 제한 없음.         |

## 탈출 문자

Escape character `\` is used to escape from execution of operation intended for an operator. On introduction on string data type, `\'` is used to prevent string from premature ending.
탈출 문자 `\`는 조작자가 의도한 조작의 실행에서 벗어날 때 사용한다. 문자열 데이터 유형에 대해 소개할 때 문자열의 조기 종료를 방지하기 위해 `\`를 사용하기도 한다.

| 구문 | 설명    |
| ------ | -------------- |
| `\n`   | 새로운 줄       |
| `\t`   | 수평 탭 |
| `\\`   | 백슬래시      |
| `\b`   | 백스페이스      |
| `\'`   | 단일 인용   |
| `\"`   | 복수 인용   |

원치 않는 작업에서 벗어나기 위해 탈출 문자를 사용하면 긴 코드 한 줄을 짧은 연속 다중 라인 코드로 코드화할 수 있다.

## None

An data with no value regardless of data type. Although `None` can be used as `False` in Boolean logic conditioning, `None` and `False` is completely different even in Boolean concept.
데이터 유형에 관계없이 값이 없는 데이터다. 논리 조건화에서는 `None`을 `False`으로 사용할 수 있지만 논리 개념에서도 `None`와 `False`은 완전히 다르다.


```python
# 조건부 확인: 부울에서 None을 False로 간주할 수 있을까?
if not(None and True):
    print(None)
```

```
None                    # 이는 None을 False로 사용할 수 없음을 증명한다.Boolean.
```