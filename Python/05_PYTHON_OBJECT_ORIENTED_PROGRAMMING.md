# **파이썬: 객체지향 프로그래밍**

이전 챕터에서는 절차적 및 함수형 프로그래밍을 소개하고 설명하였다. 세 번째 프로그래밍 방법인 객체지향 프로그래밍(object-oriennted programming, 일명 OOP)은 함수 대신 클래스와 객체 사용을 기반으로 한다.


## 객체

이전 챕터에서는 변수 (데이터를 저장할 수있는)와 기능 (데이터를 처리 할 수있는)을 소개했다. 일명 개체, 인스턴스는 이러한 변수와 기능을 하나의 정체로 캡슐화하는 데이터 블록이다.

사용자 정의 객체의 사용에 기반한 프로그래밍을 *객체지향 프로그래밍*이라고 한다.

```python
x = [0, 3, 5, 9]
print(x.index(5))
# 인덱스 메소드를 사용하여 값 5에 대한 인덱스를 반환한다 
```

```
2
```

## 캡슐화

캡슐화는 객체의 핵심개념인데..

1. 변수와 함수를 하나의 객체로 결합한다
2. 외부 코드에서 우연적 수정을 방지하기 위해 이러한 변수 및 함수에 대한 직접 접근을 제한한다


### 속성과 메서드

객체에 캡슐화 된 변수와 함수는 다르게 호출된다:

* **속성** 은 객체 종속 변수이며 `object.attribute`형식으로 접근한다.
* **메서드** 은 객체 종속 함수이며 `object.method()`형식으로 접근한다.

## 클래스

클래스는 객체 (일명 인스턴스)를 만드는 데 사용되므로 객체의 청사진으로 간주 될 수 있다. 클래스는 키워드`class`를 사용하여 만들어지며 내부는 객체의 속성과 메소드가되는 변수와 함수를 정의한다.

```python
# 클래스 생성하기
class CLASS∶
    # 인스턴스 초기화(= 생성자)
    def __init__(self, arg1, arg2):
        # 속성(변수와 비슷함)
        self.attr1 = arg1
        self.attr2 = arg2
        
	# 메서드(함수와 비슷함)
    def method(self, arg3):
        self.attr3 = arg3
        return self.attr1 + self.attr2 - self.attr3

# 객체화
instance = CLASS(value1, value2)	# 클래스로부터 객체 생성

# 그러므로...
print(instance.attr3)
print(instance.method(value3))
```

```
value3
value1 + value2 - value3
```

### `self` 변수

`self` 변수는 인스턴스 자체를 나타내는 일반적인 이름이다. 변수 또는 함수에 `self`를두면 객체에 바인딩되므로 속성 및 메서드로 선언된다. 이러한 속성과 메소드는 객체로만 접근 할 수 있습니다.
Variables and functions without `self` are local variables and functions inside the instance, and is not accessible. Attempting to do so results "AttributeError".
`self`가없는 변수 및 함수는 객체 내부의 지역 변수 및 함수이며 접근 할 수 없다. 이렇게되면 "AttributeError"가 발생한다.

```python
# 클래스 생성
class CLASS:
    def __init__(self, arg1, arg2):
        self.attr1 = arg1
        self.attr2 = None        # 속성값을 초기화해주지 않으면 에러가 발생한다.
        attr3 = arg2             # 지역 변수


# 객체화
instance = CLASS(1, 2)
''' 동등함: 
Class.__init__(self = instance, arg1 = 1, arg2 = 2, arg3 = 3)
'''

# 그러므로
instance.attr1		# >> 출력: 1
instance.attr2		# >> 출력: None
instance.attr3		# AttributeError: 'CLASS' 객체가 속성'C'를 가지고 있지 않음
```

### `__init__` 메서드

`__init__` 메소드는 객체를 생성하는 데 필요한 가장 중요한 메소드이다. 이름에서 알 수 있듯이 (* initialization *의 약어)이 메소드는 클래스에서 객체를 만들 때 자동으로 호출되며 객체 초기화에 필요한 인수의 수를 정의한다.

## 객체 속성/메서드

자체 표시를 위해`self`로 클래스 내에서 정상적으로 선언 된 모든 메소드 (및 속성)는 객체 메소드 (및 속성)이다. 따라서 객체 메소드를 선언해야하는 특별한 구문은 없다.

그러나 `self`변수가 유효한 객체 메소드 외부에서는 객체 속성을 정의 할 수 없다. 메소드 외부에서 선언 된 변수는 그 대신에 클래스 속성이 된다.
```python
# 클래스 생성
class CLASS:
    def __init__(self, arg1, arg2):
        # 인스턴스 속성
        self.attr1 = arg1
        self.attr2 = arg2
        self.attr3 = None

	# 인스턴스 메서드
    def method1(self, arg3):
        self.attr3 = arg3
```


## 클래스 속성/메서드

클래스 속성과 메소드는 객체화없이 객체와 클래스 모두에서 접근 할 수 있다. 클래스 속성은 클래스 정의없이 선언되며 메소드와 함께 들여 쓰기된다. `self` 변수는 사용되지 않는다.

클래스 메서드는 객체를 만들 필요없이 클래스만으로 접근 할 수있는 메서드이다.

|     구문     | 상세설명                              |
| :------------: | ---------------------------------------- |
| `@classmethod` | 클래스 메소드를 선언하는 데 사용되는 데코레이터 |

클래스 메소드는 위에서 언급한 데코레이터 구문에 의해 정의되지만, 메소드는 클래스 자체를 나타내는 매개 변수를 필요로한다 (인스턴스 메소드가 `self`매개 변수가 객체 자체를 언급하는 것처럼). 일반적으로`cls`로 사용된다.
```python
# 클래스 생성
class CLASS:
    # 클래스 속성
    attribute = value
    
    def __init__(self, arg1, arg2):
        self.attr1 = arg1
        self.attr2 = arg2
        self.attr3 = None

    def method1(self, arg3):
        self.attr3 = arg3
    
	# 클래스 메서드
    @classmethod
    def method2(cls, arg4):
        return arg4
    
    # 객체화를 위한 클래스 메서드
    @classmethod
    def method3(cls, x, y):
        return cls(x**2, y**2)
    
    
# 객체화
instance1 = CLASS(1, 2)
instance1.method1(4)

instance2 = CLASS.method3(1, 2)	# 객체화: arg1 = 1**1, arg2 = 2**2
instance2.method1(4)

# 그러므로...
CLASS.attribute			# >> 출력: value
CLASS.method2(3)		# >> 출력: 3

instance1.attribute	 	# >> 출력: value
instance1.attr1			# >> 출력: 1
instance1.attr2			# >> 출력: 2
instance1.attr3			# >> 출력: 4

instance2.attribute	 	# >> 출력: value
instance2.attr1			# >> 출력: 1 (= 1**2)
instance2.attr2			# >> 출력: 4 (= 2**2)
instance2.attr3			# >> 출력: 4
```

## 정적 메소드

정적 메소드는 객체화없이 호출 할 수 있고 `self` 및`cls`와 같이 자신을 호출하는 매개 변수없이 호출 할 수있는 메소드이다.

| 구문         | 상세설명                               |
| --------------- | ----------------------------------------- |
| `@staticmethod` | 정적메소드를 선언하는데 사용되는 데코레이터|

정적 메소드에는 자체 호출 할 매개 변수가 없으므로 정적 메소드는 클래스 및 객체의 속성에 접근하거나 수정할 수 없다. 이것은 정적 메소드를 클래스에 속하는 일반 함수와 동일하게 만든다.

```python
# 클래스 생성
class CLASS:
    def __init__(self, arg1, arg2):
        self.attr1 = arg1
        self.attr2 = arg2
        self.attr3 = None
        
    def method1(self, arg3)
        self.attr3 = arg3
        
    # 정적 메소드
    @staticmethod
    def method2(arg4):
        return True if arg4 is 4 else False


# 객체화
instance = CLASS(1, 2)
instance.method1(4)

# 그러므로...
instance.attr1			# >> 출력: 1
instance.attr2			# >> 출력: 2
instance.attr3			# >> 출력: 4

CLASS.method2(4)		# >> 출력: True
```

## 매직 메소드

매직 메소드는 이름의 양쪽에  dunder가있는 특수한 방법입이다. 이 방법은 일반적으로 연산자를 나타내며 연산자를 오버로드하여 연산자의 기능을 수정하는 데 사용된다.

예를 들어 초기화에 사용 된 `__init__` 메소드는 널리 사용되는 매직 메소드 중 하나이다. 아래 표에서 더 많은 것을 볼 수 있다:

| 연산자 | 이름                       | 매직메소드             |
| -------- | -------------------------- | ------------------------ |
| `+`      | 산술: 덧셈       | `__add__(self, arg)`     |
| `-`      | 산술: 뺄셈    | `__sub__(self, arg)`     |
| `*`      | 산술 : 곱셈 | `__mul__(self, arg)`     |
| `/`      | 산술 : 나눗셈       | `__truediv__(self, arg)` |
| `&`      | 논리: AND                 | `__and__(self, arg)`     |
| `^`      | 논리: XOR                 | `__xor__(self, arg)`     |
| `|`      | 논리: OR                  | `__or__(self, arg)`      |
| `()`     | 인자호출        | `__call__(self, arg)`    |

### 연산자 오버로딩

연산자 오버로딩은 특정 클래스 또는 스크립트의 일부에서 다르게 작동하도록 연산자를 사용자 정의하는 것을 의미한다. 매직 메소드는 연산자를 오버로드하는 데 사용되지만 오버로드 된 기능은 해당 특정 클래스에만 적용된다. 예를 들어,`x + y`는`x .__ add __ (y)`로 표현이 된다.

```python
# 클래스 생성
class CLASS:
    def __init__(self, arg1):
        self.A = arg1
        
    def __add__(self, arg2):
        return "\0".join([self.A, arg2.A])		#두 문자열 객체 사이에 "\0"추가

# 객체화
instance1 = CLASS("Hello")
instance2 = CLASS("World!")

instance1 + instance2		# >> 출력: "Hello World!"
```

## 상속

상속은 파생 된 서브 클래스 (자식 클래스)에 속성과 메소드를 제공하는 수퍼 클래스 (기본 클래스)의 동작이다. 수퍼 클래스와 서브 클래스 둘 다에 동일한 이름의 속성과 메소드가 존재하는 경우, 수퍼 클래스의 속성과 메소드가 서브 클래스에 의해 대체된다.

```python
# 수퍼클래스 생성
class SUPERCLASS:
    attr1 = value1
    attr2 = value2

# 서브클래스 생성
class SUBCLASS(SUPERCLASS):
    attr2 = "Hello World!"
    attr3 = value3

# 객체화  
instance = SUBCLASS()

# 그러므로...
instance.attr1		# >> 출력: value1
instance.attr2		# >> 출력: "Hello World!"
instance.attr3		# >> 출력: value3
```

### 수퍼 함수

`super ()`함수는 클래스 속성인 instance / class / static 메소드와 같은 수퍼 클래스 속성에 직접 접근하는 데 사용된다. 이 함수는 주로 수퍼 클래스 속성과 메서드를 재정의하는 것을 피하기 위해 사용된다.

```python
# 수퍼클래스 생성
class SUPERCLASS:
    def __init__(self, arg1):
        print("Hello World!")
        self.attr = arg1

# 서브클래스 생성
class SUBCLASS(SUPERCLASS):
    def __init__(self, arg2):
        print("Goodbye World?")


# 객체화
instance = SUBCLASS(3)

# 그러므로...
print(instance.attr)
```

```
"Goodbye World?"
AttributeError: 'SUBCLASS' object has no attribute 'attribute'
```

사실 `SUPERCLASS`의`__init __ ()`메소드는 두 개의 메소드가 같은 이름을 공유하기 때문에 `SUBCLASS`로 대체된다. 이것이 `print(Hello World")`가 나타나지 않았고 `self.attribute`가 상속에도 불구하고 오류를 일으키는 이유이다.

한편, 수퍼 함수를 사용할때  `SUPERCLASS`에서 직접 `__init__()`메소드를 호출 할 때 아래와 같이 한다.

```python
# 수퍼클래스 생성
class SUPERCLASS:
    def __init__(self, arg1):
        print("Hello World!")
        self.attribute = arg1

# 서브클래스 생성
class SUBCLASS(SUPERCLASS):
    def __init__(self, arg2):
        # 수퍼클래스로부터 "__init__()" 메소드 직접 상속
        super().__init__(arg2)
        print("Goodbye World?")


# 객체화
instance = SUBCLASS(3)

# 그러므로...
print(instance.attribute)
```

```
"Hello World!"
"Goodbye World?"
3
```

## 데이터 숨기기

이전에 객체 작성에서는 언급 된 캡슐화 서브 부분에서 데이터 숨기기라는 속성 및 메소드 접근에 대한 제한 사항이 제공된다. 그러나 파이썬에서는 데이터 숨기기가 보장되지 않으며 클래스 외부의 코드에서 쉽게 접근할 수 있다.

여전히, 클래스 이름 속성과 같은 수동 접근 방식이 클래스의 속성 및 메소드에 대한 접근을 방지 할 수 있다:

| 상징 | 예시       | 상세설명                                                 |
| :----: | ------------- | ------------------------------------------------------------ |
|  `_`   | `_attribute`  |이름을 다루지 않아도 속성 및 메소드에 접근하는 것은 모듈 가져 오기를 통해 전달되지만 클래스 외부의 코드에서는 전달되지 않는다. |
|  `__`  | `__attribute` | 이름 맹 글링 : 클래스 외부의 모듈 가져 오기 및 코드를 통해 접근 속성 및 메소드가 전달되지 않도록하여 `private`이 된다. |

### 프로퍼티

프로퍼티는 단일 메소드를 세 개의 개별 메소드 `getter`,`setter` 및`deleter`로 나누어 데이터 숨기기를 지원하는 데코레이터이다. 프로퍼티는 데코레이터 기호를 사용하여 선언되기 때문에 메소드에서만 사용할 수 있다.

| 메소드  | 구문            | 상세설명                                           |
| ------- | ----------------- | ----------------------------------------------------- |
| Getter  | `@property`       | 프로퍼티 속성에서 값을 가져 오는 메소드 |
| Setter  | `@method.setter`  | 프로퍼티 속성 값을 설정하는 메소드   |
| Deleter | `@method.deleter` | 프로퍼티 속성을 삭제하는 메소드              |

```python
# 클래스 생성
class CLASS:
    def __init__(self, arg1):
        self.attr1 = arg1
    
    # 정의: GETTER 메소드
    @property
    def method(self):
        return self.attr1
    
    # 정의: SETTER 메소드
    @method.setter
    def method(self, arg3):
        self.attr1 = arg3
    
    # 정의: DELETER 메소드
    @method.deleter
    def method(self):
        del self.attr1
        
# 객체화
instance = CLASS(3)

# 그러므로
print(instance.method)        # 예시: GETTER 메소드

instance.method = 1           # 예시: SETTER 메소드
print(instance.method)

del instance.method           # 예시: DELETER 메소드
print(instance.method)
```

```
3
1
AttributeError: 'CLASS' object has no attribute 'attr1'
```

사용자가 수정해서는 안되는 프로터리를 캡슐화하여 민감한 코드 사용을 구분하는 메소드는(`setter` 와 `deleter` 메소드와 같은) `setter`와`deleter`를 변경함에도 불구하고 `getter`메소드를 통해 메소드에 계속해서 접근할 수 있다.

`getter` 메소드는 프로퍼티에 필수지만`setter` 및`deleter`는 선택 사항이다: `getter` 메소드만 사용하면 수정할 수 없는 읽기 전용 메소드가 된다.