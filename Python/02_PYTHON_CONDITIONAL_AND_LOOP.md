# **파이썬: 조건문과 반복문**

조건문 및 반복문은 일반적으로 사용되며 프로그래밍에 필수적인 코드 중 하나이다. 이 챕터에서는 파이썬 프로그래밍의 조건문과 반복문을 소개하려 한다.

## 들여쓰기
들여쓰기는 코드 블록을 구분(제한 또는 경계를 표시)하는데 사용한다. 간단히 말해, 코드 블록이 어디에 속하는지 구별하는데 사용한다. 들여쓰기는 코드 뒤 콜론 `:` 뒤에 삽입된다.

들여쓰기의 위치에 따라 코드가 완전히 변경될 수 있으므로 주의해야 한다.

```python
# 두번째 print에 들여쓰기가  된 경우
if 1 < 0:
    print("Condition is False.") 
    print("End of IF statement.")
print("The End.") 

# 두번째 print에 들여쓰기가 되지 않은 경우
if 1 < 0:
    print("Condition is False.") 
print("End of IF statement.")
print("The End.") 
```

```
The End.

End of IF statement.
The End.
```

## `if` 문

조건부 `if` 문은 조건이 참일 경우 코드를 실행한다. 조건이 `True`일 때 문장이 수행되지만 그렇지 않으면 무시된다.

```python
if 조건:
    문장
```

### `else` 문

조건부 `else`문은 반드시 `if`문 뒤에 있어야 하므로 단독으로 사용할 수 없다. 문장에는 조건이 `False`라고 평가할 때 호출되는 코드가 포함되어 있다. `else`문은 `if`문과 같이 들여쓰기 되어있지 않다.

```python
if 조건:
    문장
else:
    문장
```
`if`문과 `else`문은 다음과 같은 연속적인 조건에서도 가능하다.

```python
if 조건1: 
    문장
else:
    if 조건2:
        문장
    else:
        문장
```

### `elif` 문

조건부 `elif`문은 `if`와 `else`문의 조합으로 첫 번째 조건이 거짓일 경우, 첫 번째 조건과 다른 조건을 평가할 수 있는 두 번째(혹은 그 이상) 기회를 제공한다.

```python
if 조건1: 
    문장
elif 조건:
    문장
else:
    문장
```

이것은 다른 두 가지 조건부 집합의 조합인 반면에, `elif`는 하나의 조건부 집합을 보장한다는 점에서 `else`-`if` 조건부 문장과는 연결되지 않는다.

### Ternary 연산자

조건문은 아래와 같이 3차 연산자를 사용하여 간단히 표현할 수 있다.

```python
var = True_return if condition else False_return
```

*ternary*는 세 가지 인수를 사용하는 문장을 나타낸다. 3차 연산자는 가독성을 감소시키므로 과용해서는 안되지만 변수 할당에는 유용하다.

## `while` 반복문

`while` 반복문은 조건이 유지되는 한 내부(일명 반복) 문장을 반복적으로 실행한다. 조건이 `False`임을 판단하면 반복이 종료된다.

```python
while 조건:
    문장
```
`else`문은 `while`문 뒤에 따라올 수 있으며, 반복 문장이 성공적으로 반복(조건 평균으로)되었을 때 실행된다.

```python
# 끝난 루프: 반복 완료
while index < 10:
    index += 1
    if index == 100:
        break
    else:
        print("First...successful!")

# 끝난 루프: break문으로 강제 처리됨
while index < 10:
    index += 1
    if index == 5:
        break
    else:
        print("Second...successful!")
```

```
First...successful!
```

### `break` 문

`break`문은 반복이 완료되기 전에 루프를 조기 종료하는데 사용할 수 있다. 루프 내부에서 마주친 경우에는 즉시 루프에서 탈출하지만 외부 루프에서는 탈출하지 않는다.

```python 
while single_loop_condition:
    statement1
    statement2
    break
    statements3
```

```
statement1
statement2
```

### `continue` 문

`continue`문은 아래 문장의 나머지 부분을 루프에서 건너뛰고 다시 조건화 부분으로 돌아가게 한다. 이것은 `break`문 처럼 루프를 탈출하는 것이 아니라 루프 반복을 유지한다.

```python 
while i < 5:
    statement1
    statement2
    continue
    statement3
```

```
statement1
statement2
statement1
statement2
statement1
statement2
...
```

## `for` 반복문

`for` 반복문은 유효한 범위에 있는 한 내부(일명 반복) 문장을 반복적으로 실행한다. 범위의 모든 값이 반복되면 루프가 종료된다.

```python
for index in iterable:
    statements
```

여기서 지역 변수 `index`는 `iterable`에서 값을 얻고, 내부의 모든 값을 실행할때까지 하나씩 문장을 실행한다. 루프에서 사용되는 `iterable`은 다음과 같다.

1. range 객체: 순서대로 번호 패턴을 포함한다(*파이썬: 반복가능한 객체 § Range* 참고).
2. list 객체: 데이터 유형 및 패턴에 관계없이 데이터 목록을 포함합니다(*파이썬: 반복가능한 객체 § List* 참고).
3. string 객체: 문자열을 구성하는 문자를 반환한다.

```python
for var in range(3):
    print("Hello World" , var)
```

```
Hello World 0
Hello World 1
Hello World 2
```

`while` 반복문과 마찬가지로 `break`와 `continue`를 같은 반복문인 `for` 루프에서도 사용할 수 있다.

`else` 문장은 `for` 루프 문 다음에 나타날 수 있다. 루프 문장은 루프 문장이 성공적으로 반복을 마쳤을 때(범위가 부족하여) 실행된다.

```python
# 끝난 루프: 반복 완료
for index in range(10):
    if index == 100:
        break
    else:
        print("First...successful!")

# 끝난 루프: break문으로 강제 처리됨
while index in range(10):
    if index == 5:
        break
    else:
        print("Second...successful!")
```

```
First...successful!
```

## 예외

예외는 오류 전용 조건문이다. 이 문장은 잘못된 코딩이나 입력으로 인해 실행 불가능한지 여부를 확인하고 프로그램을 즉시 중지한다. 스크립트 오류를 처리하는 데 사용할 수 있는 몇 가지 문이 있다.

### `try`/`except` 문

`try`/`except` 문은 예외를 처리하고 예외 발생에 해당하는 특정 문을 호출하는 데 사용된다. 다음 쌍과 함께 사용할 수 있는 추가 문장이 있다.

| 용어      | 설명                                                  |
| --------- | ------------------------------------------------------------ |
| `try`     | 예외가 있는지 확인되어야 할 코드이다.                 |
| `except`  | 특정한 예외가 발생했을 때 실행할 코드이다.         |
| `else`    | [선택사항: 오류(예외)없이 코드가 통과되었을 때 실행할 코드이다.] |
| `finally` | [선택사항: 어떤 예외가 발생했든, 오류가 없더라도 실행된 코드이다.] |

```python
try:
    statements
except exception_type1:
    statements
except exception_type2:
    statements
except:			# 전조건 예외처리는 마지막에 위치
    statements
finally:
    statements
```

`try`/`except`문이 실행된 후에도 프로그램은 멈추지 않고 계속된다.

### `raise` 문

`raise`문은 수동으로 의도적으로 예외를 처리하는데 사용된다. 이 명령문은 오류가 발생하면 실행도 즉시 중지하므로 더 이상 실행되지 않는다.

```python
# 명시적인 raise 예외: 위의 'except' 코드 안에서도 단독으로 사용할 수 있음
raise

# 명시적으로 발생된 예외에 대한 자세한 설명을 제공한다.
raise exception_description
```

### `assert` 문

`assert`문은 표현식의 타당성(일명 주장)을 확인한다. 테스트된 표현식이 문제 없이 유효하면 assertion에서 `True`를 반환한다. 예외가 발생하면 assertion은 `False`를 반환한다.

```python
print(0)
assert TRUE_expression
print(1)
assert FALSE_expression,"exception_type"
print(2)
```

```
0
1
AssertionError: exception_type
```

## `pass` 문

`pass`문은 실행될 때 아무 작업도 수행되지 않는 null 작업이다. 코드가 아직 작성되지 않은 곳에 코드를 삽입하면 유용합니다.