# **파이썬: 객체지향 프로그래밍**

이전 챕터에서는 절차적 및 함수형 프로그래밍을 소개하고 설명하였다. 세 번째 프로그래밍 방법인 객체지향 프로그래밍(object-oriennted programming, 일명 OOP)은 함수 대신 클래스와 객체 사용을 기반으로 한다.

## 객체

객체(object 혹은 instance)는 건물의 벽돌 역할을 하는 데이터 블록이다. 모든 객체 안에는 자신만의 성질과 성능을 일컫는 속성을 가진다. 속성은 `object.attribute` 형식으로 접근하여 활용할 수 있다.

사용자 정의 객체의 사용에 기반한 프로그래밍을 *객체지향 프로그래밍*이라고 한다.

```python
# 문자열 메소드 "append()"를 객체 "x"에서 호출
x = [0 ,3 ,5 ,9]
print( x.append(13) )
```

```
[0, 3, 5, 9, 13]
```

### 메소드 및 속성

다음은 파이썬 객체의 메소드 및 속성에 관한 설명이다.

* **메소드**
    : 메소드는 객체 한정 종속함수로써 객체가 없이 독립적인 함수처럼 사용할 수 없으며, 객체가 있어야만 사용할 수 있다.
    
* **속성**
    : 속성은 객체가 가지는 특성과 성질이며, 여기에는 객체한정 종속 함수도 포함된다. 따라서 메소드도 속성 중 하나로 속한다. 하지만 본 문서에서는 이해를 돕기 위해 속성을 *메소드를 제외한 속성*으로 구별한다.

## 클래스

클래스는 객체들을 생성하는데 사용되므로 객체의 도면으로 간주될 수 있다. 클래스는 들여쓰기 블록에서 클래스의 메소드로 함수를 포함하는 키워드 `class` 에 의해 먼저 생성된다.

```python
# 클래스 생성하기
class CLASS∶
	global var		    # 전역 변수 : 이름 같은 외부 변수와 연결된다.
    attr0 = value	    # 클래스 속성
    
    # 객체 초기화(= 생성)
    def __init__(self, arg1, arg2):
        # 객체 속성들
        self.attr1 = arg1
        self.attr2 = arg2

    # 객체 메소드
    def method(self, arg3):
        """
        statements including var3
        """
        return arg3

var = "Hello World!"			# 변수 선언(전역변수와 연결)
instance = CLASS(var1, var2)	# 클래스로 부터 객체 생성
instance.method(var3)	        # 메소드 호출
instance.var					# 속성 호출
```

```
var3
"Hello World!"
```

### `__init__`메소드

`__init__` 메소드는 클래스 생성자를 만드는데 사용되는 클래스에서 가장 중요한 메소드이다 (C / C ++ 언어의 생성자). 이 메소드는 객체가 가질 수 있는 매개 변수의 수를 정의하고 또한 객체에 대한 속성 값을 초기화하는 데에 사용된다.

`__init__` 메소드는 클래스에서 객체가 생성될 때만 자동으로 호출된다.따라서 초기화 된 속성은 객체를 통해서만 사용할 수 있으며 클래스에서는 직접 사용할 수 없다. 이와는 다르게 `__init__` 메소드 외부에서 선언 된 속성은 객체와 클래스 모두 사용할 수 있다.

### 전역 변수

`global` 키워드가 할당 된 변수는 전역 변수가 된다. 이 변수는 클래스 외부의 변수에 연결되어 있지만 동일한 이름을 공유한다.

`global` 키워드가 없으면 클래스 내부의 변수가 지역변수가 된다. 지역변수와 클래스 외부에서 선언된 변수는 서로 영향을 끼치지 않는다.

## 객체 메소드

클래스 내에서 일반적으로 선언된 모든 메소드(혹은 속성)는 객체 메소드(혹은 속성)이다. 객체 메소드를 선언에 필요한 특별한 구문이 없다.

 일부에서는 `self`라는 인자가 있는지 여부를 확인함으로써 객체 메소드를 구별할 수 있다고 오해한다. `self`가 순전히 인자이고 메소드 또는 속성의 타입을 정의 할 힘이 없기 때문에 이것은 사실이 아니다. 더 자세한 정보는 아래에 설명되어 있다.

### `self` 변수

`self` 변수는 현재 객체를 나타내는 일반적인 이름으로, 키워드가 아니며 개발자가 원하는대로 이름을 설정할 수 있다. `self` 접두사가 있는 변수들은 객체 속성이 된다. 이 객체 속성은 객체를 선언 할 때만 사용할 수 있다(C ++ 언어의`this` 포인터).`self` 접두사가 없는 변수들은 속성이 아니라 단순한 지역 변수이기에 객체에서 부를 수 없다. 지역 변수는 메소드의 범위를 벗어나 호출할 수 없으며, 이를 시도하면 "AttributeError"의 결과가 나오게 된다.

```python
# 클래스 생성하기
class CLASS():
    def __init__(self, arg1, arg2, arg3):
        self.A = arg1
        self.B = arg2
        self.C
        D = arg3		    # 지역 변수
    def method(other, x)	# 다른 이름으로 변수"self"를 교체해도 여전히 작동한다.
    	other.C = x			# 속성 "self.c"는 다른 메소드로 사용 가능하다.


# 객체화
instance = CLASS(1, 2, 3)
instance.method(4)
'''EQUIVALENT: 
Class.__init__(self = instance, arg1 = 1, arg2 = 2, arg3 = 3)
Class.method_name(other = instance, x = 4)
'''

# 그러므로...
CLASS.A			# AttributeError: 객체 유형 'Class'가 'A'속성을 가지고있지 않다.
instance.A		# >> 출력 : 1 
instance.B	    # >> 출력 : 2
instance.C		# >> 출력 : 4
instance.D	    # AttributeError: 'Class' 객체가 'D'속성을 가지고 있지 않다.
```

## 클래스 메소드

객체를 생성할 필요없이 클래스만으로 사용할 수있는 메소드이다.

|     구문     | 설명                              |
| :------------: | ---------------------------------------- |
| `@classmethod` | 클래스 메소드를 선언하는데 사용되는 데코레이터.|

클래스 메소드는 위에서 언급 한 데코레이터 구문에 의해 정의되지만, 메소드는 클래스 자체를 나타내는 매개 변수도 필요한데 일반적으로 cls로 작성된다 (객체 메소드가 self 매개변수로 객체 자체를 언급하는 것과 동일)."

```python
# 클래스 생성하기
class CLASS:
    def __init__(self, arg1, arg2):
        self.A = arg1
        self.B = arg2
        self.C
        
	def method1(self, arg3):
        self.C = arg3
    
    # 클래스 메소드 정의하기
    @classmethod
    def method2(cls, arg4):
        return arg4
    
    # 객체화를 위해 클래스 메소드 생성하기
    @classmethod
    def method3(cls, x, y):
        return cls(x**2, y**2)
    
    
# 객체화
instance1 = CLASS(1, 2)
instance1.method1(4)

instance2 = CLASS.method3(1, 2)	# 객체 : arg1 = 1**1, arg2 = 2**2
instance2.method1(4)

# 그러므로...
instance1.A			# >> 출력 : 1
instance1.B			# >> 출력 : 2
instance1.C			# >> 출력 : 4

instance2.A			# >> 출력 : 1 (= 1**2)
instance2.B			# >> 출력 : 4 (= 2**2)
instance3.C			# >> 출력 : 4

CLASS.method2(3)	# >> 출력 : 3
```

## 정적 메소드

객체화 없이 호출 할 수 있지만 `self` 및`cls`처럼 자신을 호출하는 매개변수 없이 호출 할 수있는 메소드이다.

| 구문          | 설명                               |
| --------------- | ----------------------------------------- |
| `@staticmethod` | 정적메소드를 선언하는데 사용되는 데코레이터.|

정적메소드가 자체 호출 할 매개 변수를 가지지 않기 때문에,정적메소드는 클래스 와 객체의 속성을 사용하거나 수정할 수 없다. 이것은 정적메소드를 클래스에 속하는 일반 함수로 여길수 있다.

```python
# 클래스 생성하기
class CLASS:
    def __init__(self, arg1, arg2):
        self.A = arg1
        self.B = arg2
        self.C
        
	def method1(self, arg3)
    	self.C = arg3
        
    @staticmethod
	def method2(arg4):
        return True if arg4 is 4 else False


# 객체화
instance = CLASS(1, 2)
instance.method1(4)

#그러므로...
instance.A		    # >> 출력 : 1
instance.B			# >> 출력 : 2
instance.C			# >> 출력 : 4
CLASS.method2(4)	# >> 출력 : True
```

## 매직 메소드 

매직 메소드는 이름 앞과 뒤에 언더스코어(_) 두개가 연속으로 붙어있는 특별한 메소드이다. 이러한 메소드는 일반적으로 연산자를 나타내며 연산자의 기능을 수정하기 위해 연산자 오버로딩이 사용된다.

이전에 객체 초기화에 사용 된`__init__` 메소드는 널리 사용되는 매직 메소드 중 하나이다. 아래 표에서 더 많은 것을 볼 수 있다:

| 연산자 | 이름           | 매직 메소드               |
| -------- | -------------- | -------------------------- |
| `+`      | 덧셈       | `__add__(self, other)`     |
| `-`      | 뺄셈    | `__sub__(self, other)`     |
| `*`      | 곱셈 | `__mul__(self, other)`     |
| `/`      | 나눗셈       | `__truediv__(self, other)` |
| `&`      | AND            | `__and__(self, other)`     |
| `^`      | XOR            | `__xor__(self, other)`     |
| `|`      | OR             | `__or__(self, other)`      |

### 연산자 오버로딩

연산자 오버로딩이란 특정 클래스 또는 스크립트의 일부에서 다르게 작동하도록 연산자를 사용자 정의하는 것을 의미한다. 매직 메소드는 연산자를 오버로드하는데 사용되지만 오버로드된 기능은 오직 특정 클래스에서만 적용된다. 예를 들어,`x + y`는`x .__ add __ (y)`로 표현된다.

```python
class CLASS:
    def __init__(self, arg1):
        self.A = arg1
        
    def __add__(self, arg2):
        return "&".join([self.A, arg2])		# 두 문자열 객체 사이에 "&" 삽입

    
var1 = CLASS("Hello")
var2 = CLASS("World!")
print(var1 + var2)
```

```
Hello&World!
```

## 상속

상속은 슈퍼 클래스가 속성과 메소드를 파생 된 서브 클래스에 제공(상속)하는 특징이다.

속성과 메소드 및 상속 클래스를 상속하는 모든 클래스를 각각 슈퍼 클래스 (기본 클래스)와 하위 클래스 (하위 클래스)라고 한다. 슈퍼 클래스와 서브 클래스 둘 다 동일한 이름의 속성과 메소드가 존재하면, 슈퍼 클래스의 속성은 서브 클래스의 속성으로 대체된다.

상속은 여러 인스턴스들을 통해 수행 할 수 있지만 순환 상속을 가질 수는 없다.

```python
class SUPERCLASS:
    def __init__(self, arg1, arg2):
        self.A = arg1
        self.B = arg2

        
# 파생 된 서브클래스(그러나 상속은 아직 없다)
class SUBCLASS (SUPERCLASS):
    def __init__(self, x, y):
        super().__init__(y, x)	# 슈퍼클래스의 속성과 메소드의 상속
        """EQUIVALENT:
        super(SUBCLASS, self).__init__(arg1 = y, arg2 = x)
        """
        self.A = x
        self.C = y


# 객체화
instance = SUBCLASS(1, 3)

instance.A		# >> 출력 : 1(상속받은 "self.A = 3"이지만 서브 클래스로 인해 덮어쓰기 됨)
instance.B		# >> 출력 : 1(슈퍼클래스로부터 속성 "B"가 상속 됨)
instance.C		# >> 출력 : 3
```

### 슈퍼 함수

`super ()` 함수는 슈퍼클래스에서 속성들이나 메소드들을 직접 호출한다. 이 함수 없이`instance.B`는 `SUBCLASS`객체 안에 `B` 속성이 없다고하는 "AttributeError"를 초래하게 된다.

하나의 기본클래스 상속에는 다음과 같은 구문이 사용된다:

```python
class SUBCLASS(SUPERCLASS):
    super().__init__()
    super().attribute
```

### 다이아몬드 문제

다이아몬드 문제는 하나의 슈퍼클래스(`SUBCLASS`)에서 파생된 두 클래스(`INTERCLASS1` 와 `INTERCLASS2`)로부터 하나의 서브클래스(`SUPERCLASS`)가 상속되는 상속논리 문제를 말한다. 이 경우, 슈퍼 클래스로부터의 상속이 서브 클래스로 두 번 발생할 수 있다.

이 발생은 `super ()`함수를 사용하여 막을 수 있다.

```python
# 슈퍼클래스
class SUPERCLASS:
    def __init__():
        print("START SUPERCLASS __INIT__")
        print("----")
        print("END SUPERCLASS __INIT__")
        
        
# 슈퍼클래스에서 파생된 두 중간 클래스들
class INTERCLASS1(SUPERCLASS):
    def __init__():
        print("START INTERCLASS1 __INIT__")
        super().__init__()
        print("")
        
        
class INTERCLASS2(SUPERCLASS):
    def __init__():
        print("START INTERCLASS2 __INIT__")
        super().__init__()
        print("END INTERCLASS2 __INIT__")
        
        
# 두 중간 클래스들에서 파생된 슈퍼 클래스
class SUBCLASS(INTERCLASS1, INTERCLASS2):
    def __init__():
        print("START SUBCLASS __INIT__")
        super().__init__()
        print("END SUBCLASS __INIT__")
        
        
# 객체화
instance = SUBCLASS()
```

```
START SUBCLASS __INIT__
START INTERCLASS1 __INIT__
START INTERCLASS2 __INIT__
START SUPERCLASS __INIT__
----
END SUPERCLASS __INIT__
END INTERCLASS2 __INIT__
END INTERCLASS1 __INIT__
END SUBCLASS __INIT__
```

위의 결과는 슈퍼클래스가 한 번만 상속됨을 보여준다. 이는 상속패턴을 인식하는 슈퍼클래스 `super()` 함수 때문이고 슈퍼클래스로부터 추가적인 상속을 스킵한다.

## 캡슐화

캡슐화는 (1) 속성과 메소드를 하나의 클래스 데이터로 결합하고, (2) 이러한 속성과 메소드(일명 데이터 숨기기)에 대한 직접 접근을 제한하는 기본 개념의 하나이다. 이 특징은 외부 코드로부터 클래스의 갑작스런 수정을 방지한다.

### 데이터 숨기기

캡슐화는 파이썬 클래스에서도 구현되지만, 외부 코드는 이러한 속성과 메소드에 제한이 없으므로 액세스 할 수 있다. 클래스에 가능한 숨겨져야하는 속성과 메소드가있는 경우 이름 변환과 같은 메소드가 일반적으로 파이썬에서 사용된다.

| 상징 | 예시       | 설명                                                  |
| :----: | ------------- | ------------------------------------------------------------ |
|  `_`   | `_attribute`  | 이름을 다루지 않더라도 속성 및 메소드에 대한 엑세스가 모듈 가져 오기를 통해 전달되는 것을 막을 수 있지만 클래스 외부의 코드에서 전달되지 않는다. |
|  `__`  | `__attribute` | 이름 변경: 이는 속성 및 메서드에 대한 엑세스가 모듈 가져오기 및 클래스 외부의 코드를 통해 전달되는 것을 예방해서 "전용 "이 된다. |


### 프로퍼티

프로퍼티는 메소드를 직접 수정없이 메소드를 업데이트 할 수있는 데코레이터이다. 이 때문에 프로퍼티는 데이터를 직접 변경할 수 없어서 메소드가 읽기 전용으로 보인다.

| 구문      | 설명                           |
| ----------- | ------------------------------------- |
| `@property` | 프로퍼티를 선언하는 데 사용되는 데코레이터. |

프로퍼티는 데코레이터 기호를 사용하여 선언된다. 즉, 메서드를 위해 특별히 사용된다. 프로퍼티의 특별한 특성 중 하나는 `self` 변수를 제외하고 객체에서 자신을 호출하는 인자를 취하지 않는다는 것이다. 비록 프로터피는 메소드를 기본으로 두지만 프로퍼티를 호출하는 구문은 속성과 같다. :`instance.attribute`

```python
class CLASS:
    def __init__(self, arg1, arg2):
        self.A = arg1
        self.B = arg2
        
    @property
    def method(self):
        return True
    
    
 # 객체화
instance = CLASS(1, 3)
instance.method				# >> 출력: True
instance.method = False	    # AttributeError: 속성을 설정할 수 없다.
```

프로퍼티는 캡슐화에 사용되는 세 다른 메소드로 구성된다 : `getter`, `setter`, 그리고 `deleter`.

| 메소드  | 구문            | 설명                                           |
| ------- | ----------------- | ----------------------------------------------------- |
| Getter  | `@property`       | 프로퍼티 속성에서 값을 가져 오는 메소드 |
| Setter  | `@method.setter`  | 프로퍼티 속성 값을 설정하는 메소드   |
| Deleter | `@method.deleter` | 프로퍼티 속성을 삭제하는 방법               |

```python
# 클래스 생성하기
class CLASS:
    def __init__(self, arg1, arg2):
        self.A = arg1
        self.B = arg2
        
    @property			# GETTER 메소드
    def method(self):
        return self.A
        
    @method.setter		# SETTER 메소드
    def method(self, arg3):
        statements
        
    @method.deleter		# DELETER 메소드
    def method(self):
        del self.A
```

`setter` 메소드는 프로퍼티 정의가 필요하지 않은 프로퍼티 속성을 수정하는 데 사용된다. 그러나 하나의 함수가 둘 이상의 메소드 (값 설정 및 리턴 값 전용 메소드)로 분리되므로 사실이 아니다.

이 메소드들과 함께 이 프로퍼티를 사용하면 사용자가 수정해서는 안되는 민감한 코드 (예 :`setter` 메소드)를 캡슐화하면서, 업데이트된 기능에도 불구하고 일정한 API 사용자가 액세스할 수 있다.
