# **PYTHON: FUNCTIONAL PROGRAMMING**

파이썬 : 함수형 프로그래밍

There are three different types of programming method that can be applied to Python language: procedural, functional, and object-oriented.

파이선 언어에 적용할 수 있는 프로그래밍 방법에는 절차적, 함수형, 객체 지향적 세 가지 유형이 있다.

Functional programming is a style of program scripting that is based mostly around usage of the functions. This chapter will be introducing the guide on how to create and use function in Python for functional programming.

함수형 프로그래밍은 프로그램 스크립팅의 한 유형으로, 주로 함수 사용을 중심으로 한다. 이 장에서는 함수형 프로그래밍을 위해 파이썬에서 함수를 만들고 사용하는 방법에 대한 가이드를 소개한다.
## Function

함수

Function is an independent block of code which can process the data and present newly processed data once it’s called, allowing dynamic program scripting. Function can be distinguished from its code format which has parenthesis after its name; `function()`.

함수는 데이터를 처리하고 일단 호출되면 새로 처리된 데이터를 표시할 수 있는 독립적인 코드 블록으로, 유동적 프로그램 스크립팅을 가능하게 한다. 함수는 이름 뒤에 괄호가 있는`function()`이라는 코드형식과 구별할 수 있다.

The programming based around use of custom functions is called *functional programming*.

사용자 지정 함수 사용을 중심으로 한 프로그래밍을 *함수형 프로그래밍*(사용자 정의 함수)라고 한다.

```python
x = [0, 3, 5, 9]
print(len(x))
# Code "print()" function, and "len( )" function that returns the length of list object.

# 코드 "print()"함수, 리스트 객체의 길이를 반환하는 "len( )" 함수.
```

```
4
```

Although function acts quite different from variable, they can be treated just the same. For easier understanding please refer to the example below:

비록 함수는 변수와는 꽤 다르게 작용하지만, 똑같이 취급될 수 있다. 보다 쉽게 이해하려면 아래 예제를 참조하자.

```python
# ORIGINAL FUNCTION
# 원시 함수
function(arg1, arg2)

# ASSIGNING AND EXECUTING FUNCTION VIA VARIABLE
# 함수 변수를 통한 실행과 할당
variable = function
print(variable(arg1, arg2))
```

Not only can it be assigned to variable, but function can also be passed as parameter of the other function. Therefore, you can define a function by using another function that’s been already defined.

변수에 할당할 수 있을 뿐만 아니라, 함수도 다른 함수의 매개변수로 전달할 수 있다. 그러므로 이미 정의된 다른 함수를 사용하여 또 다른 함수를 정의할 수 있다.

### Pure Function

순수 함수 

Function that returns a value that depends only on their arguments without any side effects.

어떤 부작용도 없이 그들의 인자에만 의존해 값을 반환하는 함수.

As for an example, cosine function `cos(x)` that only has single parameter `x` returns the value which depends only on the argument `x`; hence, the the cosine function is a pure function.

예를 들어, 오직 하나의 변수 `x`만 있는 코사인 함수 `cos(x)`는 인자 `x`에만 의존하여 값을 반환하기에 코사인 함수는 순수 함수이다.

```python
# FUNCTION WITH x AND y PARAMETER.
# 매개변수가 x 와 y 로 이루어진 함수. 
def function(x,y):
    variable = 2 * x
    vairable += y
    return variable			# RETURN DEPENDS ONLY ON x AND y PARAMETER.
                            # 매개변수 x 와 y 에 의존해 반환한다.
```

### Higher-Order Function
고차 함수

A function that takes other function(s) as parameters or return the function(s) as a result.

다른 함수를 매개변수로서 사용하거나 결과적으로 함수를 반환하는 함수.

## `def` Keyword

키워드 `def`

The `def` keyword is used to create your own function. When calling your newly created function before defining one, an error occurs as Python executes sequentially, thus is deemed calling non-existing function.

 `def`라는 키워드는 본인만의 함수를 만들기 위해 사용된다. 새로 생성한 함수를 정의하기도 전에 호출을 하게 되면 파이썬이 순차적으로 실행되면서 오류가 
 발생하고 존재하지 않는 함수를 호출하는 것으로 간주된다.

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

함수를 정의할 때는 어떤 매개변수가 없을지언정 괄호`()`가 필요하다.

### `return` Statement
반환문 `return`

The `return` statement is a function-exclusive statement that returns value of certain data that can be directly used from the function. Once a return statement is executed, the function ends immediately despite there are codes still left inside.

반환문(`return`)은 함수에서 직접 사용하는 특정 데이터의 값을 반환하는 함수 전용 문장이다. 일단 반환문(`return`)이 실행되면 코드가 남아 있음에도 불구하고 함수는 즉시 종료된다.

Function does not need to have a `return` statement which will return `None` when passed to variable or be printed on console terminal (for example, by using `print()` function).

함수는 변수에 전달되거나 콘솔 단자에 프린트될 때 반환하는 값이 `None`이면 반환문(`return`)을 사용 할 필요가 없다. 

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

매개변수 & 인자

Following are the difference between parameters and arguments that is referred significantly when discussed on function.

다음은 함수에 대해 논의할때 중요하게 언급되는 매개변수와 인자 사이의 차이이다.

**Parameter**

매개변수

Parameter is a function-internal local variable: because parameters is a function-exclusive local variable, it cannot be called from outside.

매개변수는 함수 내부의 지역변수 : 매개변수는 함수 전용 지역변수이기 때문에 
밖에서 호출 할 수가 없다.

| OPERATOR |    SYNTAX    | DESCRIPTION                                                  |
| :------: | :----------: | ------------------------------------------------------------ |
|   `*`    |   `*args`    | Allows multiple number of arguments.<br />Call by `args`(arguments) without asterisk, and returns tuple of arguments. Must locate after normal parameter. |
|   `**`   |  `**kwargs`  | Allows use of undefined parameter in advance.<br />Call by `kwargs`(keyword arguments) without asterisks, and returns dictionary of arguments’ name and corresponding values. |
|   `=`    | `arg1=value` | Returns default value otherwise inputted to its parameter. Must locate after normal parameter. |

| 연산자 |    구문    | 설명                                                 |
| :------: | :----------: | ------------------------------------------------------------ |
|   `*`    |   `*args`    | 여러개의 인자들을 허락한다.<br />별표 없이 `args`(인자)를 호출하고, 인자들의 튜플을 반환한다. 반드시 일반 매개변수 뒤에 위치해야 한다. |
|   `**`   |  `**kwargs`  | 정의되지 않은 매개변수를 미리 사용하는것을 허락한다.<br />별표없이 `kwargs`(keyword arguments)로 호출하고, 인자 이름과 해당 값의 딕셔너리를 반환한다. |
|   `=`    | `arg1=value` | 매개변수에 입력되지 않은 기본값을 반환한다. 반드시 일반 매개 변수 뒤에 위치해야 한다. |

**Argument**

인자

Argument is a value/object being passed to the function parameter and those passed values and objects will be processed by the function code.

인자는 함수 매개 변수에 전달되는 값/객체이며 전달된 값과 객체는 함수 코드에 의해 처리된다.

Examples below show how function parameter and argument works:

아래 예제에서는 함수 매개 변수와 인자가 작동하는 것을 보여준다:

```python
# PARAMETER *args ALLOWS MORE ARGUMENT TO BE PASSED.
# 매개변수 *args는 인자가 더 전달되는 것을 허용한다.
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
# 매개변수 **kwargs는 정의되지 않은 함수의 매개변수를 허용한다.
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
# 매개변수 arg2의 기본값 초기화
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

익명 함수

Also known as **Lambda function (express)**, is a function without declaration without name (thus, anonymous) and does not store data, returning value only from a single expression. Anonymous function is generally used for a single-use function, or as an argument of higher-order function's parameter.

일명 **람다 표현삭** 이라고도 알려져 있으며, 이름이 없는 선언 없는 함수로, 데이터를 저장하지 않고, 단일 표현식에서만 값을 반환한다. 익명함수는 일반적으로 1회용 함수에 사용되거나 혹은 고차함수의 매개변수 인자로 사용된다.

| SYNTAX                                                       |
| ------------------------------------------------------------ |
| `lambda param0, param1 ∶ expression`                         |
| A main body of anonymous function consisting parameters and its return expression. |

| 구문                                                       |
| ------------------------------------------------------------ |
| `lambda param0, param1 ∶ expression`                         |
| 익명 함수의 주 몸체는 매개변수와 그를 반환하는 표현식의 구성으로 되어 있다. |


Although anonymous function is a function without a name for a single-use, it can be assigned to variables and called when the function is needed. The anonymous function of the named function at *Pure Function* example section is expressed as below:

비록 익명함수가 1회용을 위한 이름이 없는 함수이지만 변수들에게 할당할수 있으며 그 함수가 필요할 때 호출이 가능하다. *순수 함수* 예제 구역에서 지정된 함수의 익명 함수는 다음과 같이 표현된다.

```python
# NAMED FUNCTION
#이름이 있는 함수
def function(x, y):
    return 2 * x + y

# ANONYMOUS FUNCTION
#익명 함수
(lambda x, y: 2 * x + y)(2, 3)

# ANONYMOUS FUNCTION ASSIGNED TO VARIABLE
#변수에 할당된 익명 함수
variable = lambda x, y: 2 * x + y
variable(2,3)
```

```
7
```

## Map Function

맵 함수

Built-in function which takes iterable objects and function with parameters as arguments. Map function returns a list containing return value of the function with iterable objects as arguments.

내장 함수로 반복 객체와 인자를 매개변수로 사용하는 함수이다.  맵함수는 반복 객체를 인자로 사용하여 함수의 반환 값을 포함하는 리스트를 반환한다.

| SYNTAX                                                       |
| ------------------------------------------------------------ |
| `map(function, iter0, iter1, ...)`                           |
| In higher-order `map` function, iterable object `iter0` and `iter1` are passed as argument for `function`. |

| 구문                                                       |
| ------------------------------------------------------------ |
| `map(function, iter0, iter1, ...)`                           |
|고차 `map`함수에서는 반복가능한 객체 `iter0` 및 `iter1`가 `function`의 인자로 전달된다. |

Conversion to an iterable object, such as `list()` function is necessary to avoid error such as "SyntaxError".

"SyntaxError"와 같은 오류를 방지하려면 `list()` 함수와 같은 반복 객체로 전환해야 한다.

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

필터 함수

Built-in function which takes iterable object and Boolean conditioning function (aka. predicate) as arguments and returns iterable object containing only with the data that passed the predicate.

내장 함수로 반복 객체와 부울 조건화 함수(일명 술어)를 인자로 사용하고 술어를 통과한 반복객체만을 반환하는 함수이다. 
 
| SYNTAX                                                       |
| ------------------------------------------------------------ |
| `filter(predicate, iterable)`                                |
| In higher-order `filter` function, iterable object `iterable`are passed as argument for `predicate`. |

| 구문                                                       |
| ------------------------------------------------------------ |
| `filter(predicate, iterable)`                                |
| 고차  `filter` 함수로 반복 객체의 반복만이 술어의 인자로 전달된다. |

Conversion to an iterable object, such as `list()` function is necessary to avoid error such as "SyntaxError".

"SyntaxError"와 같은 오류를 방지하려면 `list()` 함수와 같은 반복 객체로 전환해야 한다.

```python
lst = [1, 2, 3, 4, 5]

var = filter(lambda x: x % 2 is 0, lst)

print( list(var) )
```

```
[2, 4]
```

## Recursive Function

재귀 함수 

Recursive function is a function that calls itself (recursion). Factorial $!$ in mathematic is the best example of recursive function implementation.

재귀 함수란 자기자신의 함수를 호출하는 함수이다. 수학에서의 펙토리얼"!" 이 재귀함수 구현의 가장 좋은 예제이다.

```python
# EXAMPLE: FACTORIAL "!"
# 펙도리얼 '!' 예제
def factorial( x ):
    # BASE CASE: a case when to escape from the recursion.
    # 베이스 케이스 : 재귀로부터 탈출하는 경우
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

재귀는 많은 수의 함수들로 인해 하나가 호출이 되면 간접적으로 발생할수 있는데,그렇게 되면 다시 처음으로 돌아간다.

### Base Case

베이스 케이스

A case of recursion which doesn’t involve referring to itself anymore. It can be deemed as an exit condition. Without a base case, recursion results infinitely and thus crashes due to memory shortage:

더 이상 자신을 나타내는 것을 포함하지 않는 재귀의 경우, 그것이 출구조건으로 여겨질 수 있다. 베이스 케이스 없이, 재귀는 무한히 발생해여 메모리 부족으로 인해 충돌된다. 

```
RuntimeError: maximum recursion depth exceeded
```

## Decorator

데코레이터

A function which modifies original function’s functionality and returns the modified "function" itself (rather than returning value). Hence, assignment to a variable is needed for a function to properly work after processing through the decorator. Its function will then have a same name as the variable.

함수의 기능을 수정하고 그 수정된 함수 자체를 반환하는 함수이다(값을 반환하기 보다는). 따라서, 변수에 대한 할당은 함수가 데코레이터를 통해 처리한 후에 적절히 작동하기 위해 필요하다. 그러면 함수는 변수와 같은 이름을 가지게 될 것이다.

```python
# ORIGINAL FUNCTION
# 원시 함수
def function():
	statements

# CREATING DECORATOR
# 데코레이터 만들기
def decorator(func):
	def modified_function():
        """
        statements including func()
        """
	return modified_function

# DECORATING (MODIFYING) FUNCTION
# 함수 수정하기(데코레이팅)
variable = decorator(function) 
variable()		# WHICH IS ACTUALLY A FUNCTION ASSIGNED TO "variable".
                # '변수'에 실제로 할당된 함수.
# DECORATING (MODIFYING) FUNCTION: MAINTAIN FUNCTION NAME
# 함수 수정하기(데코레이팅) : 함수의 이름 유지하기
function = decorator(function)
function()
```

Decorator above have decorated (modified) `function()` and assigned the decorated function to a variable `variable()` and `function()`, where latter maintains the function name.

위의 데코레이터는 `function()`을 수정하고, 수정된 함수를 변수 `variable()`과 `function()`에 할당하여 나중에 함수명을 유지한다.

When passing function as a parameter of a decorator, no parenthesis are needed like `function()`. This is because former passes function itself and latter passes return value of the function.

데코레이터의 매개변수로써 함수를 전달할 때  `function()`과 같은 괄호는 필요하지 않다. 이는 전의 것이 함수 자체를 전달하고 나중의 것이 함수의 반환값을 전달하기 때문이다. 

### `@` Symbol

`@` 상징

A decorator symbol `@` used for pre-pending the function definition, placed before pre-decorated function.

수정된 함수 앞에 위치하는 함수 정의의 사전 첨부를 위해 사용되는 데코레이터 상징 `@`

| OPERATOR | EXAMPLE      | DESCRIPTION                                               |
| :------: | ------------ | --------------------------------------------------------- |
|   `@`    | `@decorator` | `@decorator` is a replacement of `func = decorator(func)` |

| 연산자 |  예시   | 설명                                              |
| :------: | ------------ | --------------------------------------------------------- |
|   `@`    | `@decorator` | `@decorator` 는 `func = decorator(func)`의 대체이다 |


```python
# CREATING DECORATOR.
# 데코레이터 생성하기
def decorator(func):
    def modified_function():
        """
        statements including func()
        """
    return function_modified

# DECORATING FUNCTION: @ SYMBOL
# 함수 데코레이팅 : 상징 @
@decorator
def function():	# ORIGINAL FUNCTION OF "function()"
                # "function()"의 원시 함수
    statements

# FUNCTION NAME REMAINS THE SAME.
# 함수이름은 같게 유지된다.
function()
```

Additionally, more than one decorator can be applied to a single pre-decorated function.

추가적으로, 하나 이상의 데코레이터를 이미 수정된 하나의 함수에 적용 할 수 있다.

```python
@decorator0
@decorator1
def function():
    statements
```

A decorator located closest to pre-decorated function will be applied firsthand. Thus, the function object `function()` will first be decorated by `@decorator1`  then `@decorator0` sequentially.

이미 수정된 함수에 가깝게 위치한 데코레이터가 직접적으로 적용된다.
따라서 함수 객체`function ()`은 먼저 `@ decorator1`로 수정된 후
`@ decorator0`으로 순차적으로 수정된다.