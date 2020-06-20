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

## Static Method

Static method is a method that can be called without instantiation, but without parameter to call itself like `self` and `cls`.

| SYNTAX          | DESCRIPTION                               |
| --------------- | ----------------------------------------- |
| `@staticmethod` | Decorator used to declare static methods. |

Since static method does not have a parameter to call itself, static method cannot access or modify any attribute from class and instance. This makes static method identical to normal function belonged to class.

```python
# CREATING CLASS
class CLASS:
    def __init__(self, arg1, arg2):
        self.attr1 = arg1
        self.attr2 = arg2
        self.attr3 = None
        
    def method1(self, arg3)
        self.attr3 = arg3
        
    # STATIC METHOD
    @staticmethod
    def method2(arg4):
        return True if arg4 is 4 else False


# INSTANTIATION
instance = CLASS(1, 2)
instance.method1(4)

# THEREFORE...
instance.attr1			# >> OUTPUT: 1
instance.attr2			# >> OUTPUT: 2
instance.attr3			# >> OUTPUT: 4

CLASS.method2(4)		# >> OUTPUT: True
```

## Magic Method

Magic method is a special method which has Double UNDERscores(dunder) on both side of its name. These method generally represents operator, and are used when overloading operator to modify the operator's functionality. 

Previously encountered `__init__` method used for instance initialization is one of the widely used magic method. More can be seen on the table below:

| OPERATOR | NAME                       | MAGIC METHOD             |
| -------- | -------------------------- | ------------------------ |
| `+`      | Arithmetic: Addition       | `__add__(self, arg)`     |
| `-`      | Arithmetic: Subtraction    | `__sub__(self, arg)`     |
| `*`      | Arithmetic: Multiplication | `__mul__(self, arg)`     |
| `/`      | Arithmetic: Division       | `__truediv__(self, arg)` |
| `&`      | Logic: AND                 | `__and__(self, arg)`     |
| `^`      | Logic: XOR                 | `__xor__(self, arg)`     |
| `|`      | Logic: OR                  | `__or__(self, arg)`      |
| `()`     | Calling argument(s)        | `__call__(self, arg)`    |

### Operator Overloading

Overloading operator means customizing operator to function differently on certain classes or portion of the script. Magic method is used to overload operator but overloaded functionality is only exclusive to that specific class. As an example, `x + y`  is expressed as `x.__add__(y)` .

```python
# CREATING CLASS
class CLASS:
    def __init__(self, arg1):
        self.A = arg1
        
    def __add__(self, arg2):
        return "\0".join([self.A, arg2.A])		# INSERT "\0" BETWEEN TWO STRING OBJECTS.

# INSTANTIATION
instance1 = CLASS("Hello")
instance2 = CLASS("World!")

instance1 + instance2		# >> OUTPUT: "Hello World!"
```

## Inheritance

Inheritance is an act of superclass (base class) providing attributes and methods to derived subclass (child class). When the same name of attributes and methods exists on both superclass and subclass, attributes and methods from superclass are overridden by subclass's.

```python
# CREATING SUPERCLASS
class SUPERCLASS:
    attr1 = value1
    attr2 = value2

# CREATING SUBCLASS
class SUBCLASS(SUPERCLASS):
    attr2 = "Hello World!"
    attr3 = value3

# INSTANTIATION  
instance = SUBCLASS()

# THEREFORE...
instance.attr1		# >> OUTPUT: value1
instance.attr2		# >> OUTPUT: "Hello World!"
instance.attr3		# >> OUTPUT: value3
```

### Super Function

The `super()` function is used to access the superclass properties, such as class attributes instance/class/static methods directly. This function is mainly used to avoid overriding superclass attributes and methods.

```python
# CREATING SUPERCLASS
class SUPERCLASS:
    def __init__(self, arg1):
        print("Hello World!")
        self.attr = arg1

# CREATING SUBCLASS
class SUBCLASS(SUPERCLASS):
    def __init__(self, arg2):
        print("Goodbye World?")


# INSTANTIATION
instance = SUBCLASS(3)

# THEREFORE...
print(instance.attr)
```

```
"Goodbye World?"
AttributeError: 'SUBCLASS' object has no attribute 'attribute'
```

Originally, the `__init__()` method in `SUPERCLASS` would have been overridden by `SUBCLASS` since both methods share the same name. This is the reason `print(Hello World")` did not appeared and `self.attribute` cause an error despite inheritance.

On the other hand, when using super function to called the `__init__()` method directly from the `SUPERCLASS`

```python
# CREATING SUPERCLASS
class SUPERCLASS:
    def __init__(self, arg1):
        print("Hello World!")
        self.attribute = arg1

# CREATING SUBCLASS
class SUBCLASS(SUPERCLASS):
    def __init__(self, arg2):
        # DIRECTLY INHERITING "__init__()" METHOD FROM SUPERCLASS
        super().__init__(arg2)
        print("Goodbye World?")


# INSTANTIATION
instance = SUBCLASS(3)

# THEREFORE...
print(instance.attribute)
```

```
"Hello World!"
"Goodbye World?"
3
```

## Data Hiding

Previously on *Encapsulation* subsection mentioned creating an object provides restriction on accessing attributes and methods, called *Data Hiding*. In Python, however, data hiding is not guaranteed and can be accessed easily from the code outside the class.

Still, manual approach such as name mangling is possible to prevent access to attributes and methods of the class:

| SYMBOL | EXAMPLE       | DESCRIPTION                                                  |
| :----: | ------------- | ------------------------------------------------------------ |
|  `_`   | `_attribute`  | Though not a name mangling, it can prevent accessing attributes and methods from being passed via module import but not from codes outside the class. |
|  `__`  | `__attribute` | Name mangling: this prevents accessing attributes and methods from being passed via module import and codes outside the class, thus becomes "private". |

### Properties

Property is a decorator that supports data hiding by dividing a single method into three separate methods: `getter`, `setter`, and `deleter`. Because property is declared using decorator symbol, it can only be used on method.

| METHOD  | SYNTAX            | DESCRIPTION                                           |
| ------- | ----------------- | ----------------------------------------------------- |
| Getter  | `@property`       | Method for getting the value from property attribute. |
| Setter  | `@method.setter`  | Method for setting the value of property attribute.   |
| Deleter | `@method.deleter` | Method for deleting property attribute.               |

```python
# CREATING CLASS
class CLASS:
    def __init__(self, arg1):
        self.attr1 = arg1
    
    # DEFINITION: GETTER METHOD
    @property
    def method(self):
        return self.attr1
    
    # DEFINITION: SETTER METHOD
    @method.setter
    def method(self, arg3):
        self.attr1 = arg3
    
    # DEFINITION: DELETER METHOD
    @method.deleter
    def method(self):
        del self.attr1
        
# INSTANTIATION
instance = CLASS(3)

# THEREFORE
print(instance.method)        # EXAMPLE: GETTER METHOD

instance.method = 1           # EXAMPLE: SETTER METHOD
print(instance.method)

del instance.method           # EXAMPLE: DELETER METHOD
print(instance.method)
```

```
3
1
AttributeError: 'CLASS' object has no attribute 'attr1'
```

Separating method using property encapsulate sensitive code that shouldn't be modified by the user (such as `setter` and `deleter` method), while providing constant access to the method via `getter` method despite any changes were made on `setter` and `deleter`.

Although `getter` method is essential in property, the `setter` and `deleter` are optional; using `getter` method alone would make unmodifiable read-only method.