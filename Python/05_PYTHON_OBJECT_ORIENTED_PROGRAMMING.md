# **파이썬: 객체지향 프로그래밍**

이전 챕터에서는 절차적 및 함수형 프로그래밍을 소개하고 설명하였다. 세 번째 프로그래밍 방법인 객체지향 프로그래밍(object-oriennted programming, 일명 OOP)은 함수 대신 클래스와 객체 사용을 기반으로 한다.


## 객체

이전 챕터에서는 (데이터를 저장할 수 있는)변수와 (데이터를 처리 할 수 있는)함수를 소개했다. 일명 개체는 이러한 변수와 기능을 하나의 데이터로 캡슐화하는 데이터 블록이다.

사용자 정의 객체의 사용에 기반한 프로그래밍을 *객체지향 프로그래밍*이라고 한다.

```python
x = [0, 3, 5, 9]
print(x.index(5))
# index() 메소드를 사용하여 값 5에 대한 위치를 반환한다
```

```
2
```

## 캡슐화

캡슐화는 객체의 핵심으로 아래의 역할을 가진다.

1. 변수와 함수를 하나의 객체로 결합한다
2. 외부 코드에서 우연치 않은 수정을 방지하기 위해 이러한 변수 및 함수에 대한 직접 접근을 제한한다


### 속성과 메서드

객체에 캡슐화 된 변수와 함수는 다르게 호출된다:

* **속성** 은 객체 종속 변수이며 `object.attribute`형식으로 접근한다.
* **메서드** 은 객체 종속 함수이며 `object.method()`형식으로 접근한다.

## 클래스

클래스는 객체를 만드는데 사용되므로 객체의 청사진으로 간주 될 수 있다. 클래스는 키워드`class`를 사용하여 만들어지며 내부는 객체의 속성과 메소드가 되는 변수와 함수가 정의되어 있다.

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

`self` 변수는 객체 자체를 나타내는 일반적인 이름이다. 변수 또는 함수에 `self`를두면 객체에 종속되므로 속성 및 메서드로 선언된다. 이러한 속성과 메소드는 객체로만 접근 할 수 있다.

`self`가없는 변수 및 함수는 객체 내부의 지역 변수 및 함수이며 외부에서 접근 할 수 없다. 이렇게되면 "AttributeError"가 발생한다.

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
CLASS.__init__(self = instance, arg1 = 1, arg2 = 2, arg3 = 3)
'''

# 그러므로
instance.attr1		# >> 출력: 1
instance.attr2		# >> 출력: None
instance.attr3		# AttributeError: 'CLASS' 객체가 속성'C'를 가지고 있지 않음
```

### `__init__` 메서드

`__init__` 메소드는 객체를 생성하는 데 필요한 가장 중요한 메소드이다. 이름에서 알 수 있듯이 (*initialization*의 약어) 해당 메소드는 클래스에서 객체를 만들 때 자동으로 호출되며 객체 초기화에 필요한 인수의 수를 정의한다.

## 객체 속성/메서드

자체 표시를 위해`self`로 클래스 내에서 정상적으로 선언 된 모든 메소드(및 속성)는 객체 메소드(및 속성)이다. 객체 메소드를 선언해야하는 특별한 구문은 없다.

그러나 `self`변수가 유효한 객체 메소드 외부에서는 객체 속성을 정의 할 수 없다. 메소드 외부에서 선언 된 변수는 그 대신에 클래스 속성이 된다.
```python
# 클래스 생성
class CLASS:
    def __init__(self, arg1, arg2):
        # 객체 속성
        self.attr1 = arg1
        self.attr2 = arg2
        self.attr3 = None

	# 객체 메서드
    def method1(self, arg3):
        self.attr3 = arg3
```


## 클래스 속성/메서드

클래스 속성은 클래스 정의 내에서 객체 메소드와 동일한 들여쓰기에서 선언된다.

클래스 메소드는 객체를 만들 필요없이 클래스만으로 접근 할 수있는 메소드이다.

|     구문     |설명                              |
| :------------: | ---------------------------------------- |
| `@classmethod` | 클래스 메소드를 선언하는 데 사용되는 데코레이터 |

클래스 메소드는 위에서 언급한 데코레이터 구문에 의해 정의되지만, 메소드는 클래스 자체를 나타내는 매개변수를 필요로한다.(객체 메소드가 `self`매개 변수가 객체 자체를 언급하는 것처럼). 일반적으로`cls`로 사용된다.
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
    
	# 클래스 메소드
    @classmethod
    def method2(cls, arg4):
        return arg4
    
    # 객체화를 위한 클래스 메소드
    @classmethod
    def method3(cls, x, y):
        return cls(x**2, y**2)
    
    
# 객체화
instance1 = CLASS(1, 2)
instance1.method1(4)

# 객체화: arg1 = 1**1, arg2 = 2**2
instance2 = CLASS.method3(1, 2)
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

| 구문         |설명                               |
| --------------- | ----------------------------------------- |
| `@staticmethod` | 정적 메소드를 선언하는데 사용되는 데코레이터|

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

매직 메소드는 이름의 양쪽에  dunder가있는 특수한 방법이다. 이 방법은 일반적으로 연산자를 나타내며 연산자를 오버로드하여 연산자의 기능을 수정하는데 사용된다.

예를 들어 초기화에 사용 된 `__init__` 메소드는 널리 사용되는 매직 메소드 중 하나이다. 아래 표에서 더 많은 것을 볼 수 있다:

| 연산자 | 이름                       | 매직 메소드             |
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
        return "\0".join([self.A, arg2.A]) # 두 문자열 객체 사이에 "\0" 추가

# 객체화
instance1 = CLASS("Hello")
instance2 = CLASS("World!")

instance1 + instance2		# >> 출력: "Hello World!"
```

## 상속

상속은 파생 된 서브클래스 (자식 클래스)에 속성과 메소드를 제공하는 슈퍼클래스 (기반 클래스)의 동작이다. 슈퍼클래스와 서브클래스 둘 다에 동일한 이름의 속성과 메소드가 존재하는 경우, 슈퍼클래스의 속성과 메소드가 서브클래스에 의해 대체된다.

```python
# 슈퍼클래스 생성
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

### 슈퍼 함수

`super ()`함수는 슈퍼클래스의 클래스 속성과 객체/클래스/정적 메소드에 직접 접근하는데 사용된다.이 함수는 주로 수퍼 클래스 속성과 메서드를 재정의하는 것을 피하기 위해 사용된다.

```python
# 슈퍼클래스 생성
class SUPERCLASS:
    def __init__(self, arg1):
        print("Hello World!")
        self.attribute = arg1

# 서브클래스 생성
class SUBCLASS(SUPERCLASS):
    def __init__(self, arg2):
        print("Goodbye World?")


# 객체화
instance = SUBCLASS(3)

# 그러므로...
print(instance.attribute)
```

```
"Goodbye World?"
AttributeError: 'SUBCLASS' object has no attribute 'attribute'
```
`SUPERCLASS`의 `__init __ ()`메소드가 `SUPERCLASS`로 상속되었으나 `SUPERCLASS`는 이미 `__init __ ()`메소드를 가지고 있어 결과적으로 오버로드되어 상속이 되지 않은 것처럼 보이는거다.
이것이 `print(Hello World")`가 나타나지 않고 `self.attribute`가 상속에도 불구하고 오류를 일으키는 이유이다.

한편, 슈퍼 함수를 사용하여 `SUPERCLASS`의`__init__()` 메소드를 직접 불러오기 위해서 다음과 같이 사용한다.

```python
# 슈퍼클래스 생성
class SUPERCLASS:
    def __init__(self, arg1):
        print("Hello World!")
        self.attribute = arg1

# 서브클래스 생성
class SUBCLASS(SUPERCLASS):
    def __init__(self, arg2):
        # 슈퍼클래스로부터 "__init__()" 메소드 직접 상속
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

캡슐화는 파이썬 클래스에서도 구현되지만, 외부 코드는 이러한 속성과 메소드가 제한되지 않기에 여전히 접근 가능하다. 클래스에 가능한 한 숨겨져야 하는 속성과 메소드가 있는 경우 일반적으로 "이름뒤섞기"와 같은 메소드가 파이썬에서 사용된다.

| 기호 | 예시       | 설명                                                 |
| :----: | ------------- | ------------------------------------------------------------ |
|  `_`   | `_attribute`  |"이름 뒤섞기"란 기법이 아니지만, 클래스가 모듈로써 불러올 경우에 대하여 접속이 제한된다 |
|  `__`  | `__attribute` | "이름 뒤섞기" : 모듈로써 접근과 클래스 외부에서의 접근을 제한한다. |

### 프로퍼티

프로퍼티는 단일 메소드를 세 개의 개별 메소드 `getter`,`setter` 및`deleter`로 나누어 데이터 숨기기를 지원하는 데코레이터이다. 프로퍼티는 데코레이터 기호를 사용하여 선언되기 때문에 메소드에서만 사용할 수 있다.

| 메소드  | 구문            | 설명                                           |
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

속성 값 설정 및 삭제는 매우 민감한 코드이므로 함부로 건들면 안된다.이러한 민감한 코드를 프로퍼티를 통해 나누면 사용자는 `getter` 메소드만을 통해서 기능을 사용할 수 있으며, 그 뒤에서 개발자는 `setter`메소드 및 `deleter`메소드를 통해 계속적으로 작업이 가능하다.

`getter` 메소드는 프로퍼티에 필수지만`setter` 및`deleter`는 선택 사항이다: `getter` 메소드만 사용하면 수정할 수 없는 읽기 전용 메소드가 된다.