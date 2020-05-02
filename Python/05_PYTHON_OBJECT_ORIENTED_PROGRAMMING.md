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

Class is used to create objects (aka. instance), hence can be deemed as an object’s blueprint. Classes are created first by a keyword `class` containing functions as method of the class in indented block.

클래스는 객체(일명. 인스턴스)들을 생성하는데 사용되므로 객체의 도면으로 간주될 수 있다. 클래스는 들여쓰기 블록에서 클래스의 메서드로 함수를 포함하는 키워드 `class` 에 의해 먼저 생성된다.

```python
# CREATING CLASS
# 클래스 생성하기
class CLASS∶
	global var			# GLOBAL VARIABLE: LINKED TO VARAIBLE OUTSIDE WITH SAME NAME
                        # 전역 변수 : 이름 같은 외부 변수와 연결된다.
    attr0 = value		# CLASS ATTRIBUTE
                        # 클래스 속성
    
    # INSTANCE INITIALIZATION (= CONSTRUCTOR)
    # 인스턴스 초기화(= 생성)
    def __init__(self, arg1, arg2):
        # INSTANCE ATTRIBUTES
        # 인스턴스 속성들
        self.attr1 = arg1
        self.attr2 = arg2
        
    # INSTANCE METHOD
    # 인스턴스 메소드
    def method(self, arg3):
        """
        statements including var3
        """
        return arg3

var = "Hello World!"			# DECLARE VARIABLE (LINKED TO GLOBAL VARIABLE)
                                #변수 선언(전역변수와 연결)
instance = CLASS(var1, var2)	# CREATE INSTANCE FROM THE CLASS
                                # 클래스로 부터 인스턴스 생성
instance.method(var3)			# CALLING METHOD
                                # 메소드 호출
instance.var					# CALLING ATTRIBUTE
                                # 속성 호출
```

```
var3
"Hello World!"
```

### `__init__` Method
`__init__`메소드

The `__init__` method is the most important method in class which is used to create class constructor (like the *constructor* in C/C++ language). This method defines how many parameters the instance can have and also responsible for initializing attribute values for instance.

`__init__` 메소드는 클래스 생성자를 만드는데 사용되는 클래스에서 가장 중요한 메소드이다 (C / C ++ 언어의 생성자). 이 메소드는 인스턴스가 가질 수있는 매개 변수의 수를 정의하고 또한 인스턴스에 대한 속성 값을 초기화해야 한다.

The `__init__` method automatically called only when instance is created from the class. Therefore, initialized attribute can only be access through instance, but not from the class directly. As oppose to this, attribute declared outside the `__init__` method is accessible from both instance and class.

`__init__` 메소드는 클래스에서 인스턴스가 생성 될 때만 자동으로 호출된다.따라서 초기화 된 속성은 인스턴스를 통해서만 액세스 할 수 있으며 클래스에서는 직접 액세스 할 수 없다. 이와는 다르게 `__init__` 메소드 외부에서 선언 된 속성은 인스턴스와 클래스 모두 액세스 할 수 있다.

### Global Variable
전역 변수

Variable assigned with `global` keyword represents global variable. This variable is linked to the variable outside the class but shares the same name.

`global` 키워드가 할당 된 변수는 전역 변수를 나타낸다. 이 변수는 클래스 외부의 변수에 연결되어 있지만 동일한 이름을 공유한다.

Without `global` keyword, the variable inside the class becomes local variable. Local variable and variable declared outside the class will be irrelevant to each other.

`global` 키워드가 없으면 클래스 내부의 변수가 지역변수가 된다. 지역변수와 클래스 외부에서 선언된 변수는 서로 관련이 없다.

## Instance Method
인스턴스 메소드

All methods (or attributes) that are declared normally within the class are instance methods (or attributes). There is no special syntax that need to declare for instance method.

클래스 내에서 정상적으로 선언된 모든 메소드(혹은 속성)는 인스턴스 메소드(혹은 속성)이다. 인스턴스 메소드를 선언해야하는 특별한 구문은 없다.

Some may misunderstand instance method can be distinguished by checking whether the argument `self` is there or not. This is not true as `self` is purely an argument and has no power on defining the type of method or attribute. The detail information is explained under the subsection below.

 일부에서는 `self`라는 인자가 있는지 여부를 확인함으로써 인스턴스 메소드를 구별할 수 있다는 오해를 불러오기도 한다. `self`가 순전히 인수이고 메소드 또는 속성의 타입을 정의 할 힘이 없기 때문에 이것은 사실이 아니다. 더 자세한 정보는 
 아래에 설명되어 있다.

### `self` Variable
`self` 변수

The `self` variable is a conventional name to indicate a current instance, meaning it is not a keyword and the name can be set however developer wants. Variables with `self` prefix become instance attributes.

`self` 변수는 현재 인스턴스를 나타내는 일반적인 이름으로, 키워드가 아니며 개발자가 원하는대로 이름을 설정할 수 있다. `self` 접두사가 있는 변수들은 인스턴스 속성이 된다.

These instance attribute can be accessed only upon declaring an instance (like `this` pointer in C++ language). Variables without `self` prefix cannot be called from the instance as they are not an attribute but a plain local variables. Local variables cannot be called outside its scope of method, and attempting to do so results "AttributeError".

이 인스턴스 속성은 인스턴스를 선언 할 때만 액세스 할 수 있다(C ++ 언어의`this` 포인터).`self` 접두사가 없는 변수들은 속성이 아니라 단순한 지역 변수이기에 인스턴스에서 부를 수 없다. 지역 변수는 메소드의 범위를 벗어나 호출할 수 없으며, 이를 시도하면 "AttributeError"의 결과가 나오게 된다.

```python
# CREATING CLASS
# 클래스 생성하기
class CLASS():
    def __init__(self, arg1, arg2, arg3):
        self.A = arg1
        self.B = arg2
        self.C
        D = arg3			# LOCAL VARIABLE
                            # 지역 변수
    def method(other, x)	# REPLACING "self" VARIABLE TO DIFFERENT NAME STILL WORKS.
                            # 다른 이름으로 변수"self"를 교체해도 여전히 작동한다.
    	other.C = x			# ATTRIBUTE "self.C" IS AVAILABLE IN DIFFERENT METHODS.
                            # 속성 "self.c"는 다른 메소드로 사용 가능하다.


# INSTANTIATION
# 인스턴드화
instance = CLASS(1, 2, 3)
instance.method(4)
'''EQUIVALENT: 
Class.__init__(self = instance, arg1 = 1, arg2 = 2, arg3 = 3)
Class.method_name(other = instance, x = 4)
'''

# THEREFORE...
# 그러므로...
CLASS.A			# AttributeError: type object 'Class' has no attribute 'A'
                # AttributeError: 객체 유형 'Class'가 'A'속성을 가지고있지 않다.
instance.A		# >> OUTPUT: 1
                # >> 출력 : 1 
instance.B		# >> OUTPUT: 2
                # >> 출력 : 2
instance.C		# >> OUTPUT: 4 
                # >> 출력 : 4
instance.D		# AttributeError: 'Class' object has no attribute 'D'
                # AttributeError: 'Class' 객체가 'D'속성을 가지고 있지 않다.
```

## Class Method

A method which can be accessed through class alone without needs of creating an instance.

|     SYNTAX     | DESCRIPTION                              |
| :------------: | ---------------------------------------- |
| `@classmethod` | Decorator used to declare class methods. |

Though class method is defined by the decorator syntax mentioned above, the method also requires parameter to indicate the class itself (just like instance method have `self` parameter to mention instance itself), conventionally written as `cls`.

```python
# CREATING CLASS
class CLASS:
    def __init__(self, arg1, arg2):
        self.A = arg1
        self.B = arg2
        self.C
        
	def method1(self, arg3):
        self.C = arg3
    
    # DEFINING CLASS METHOD
    @classmethod
    def method2(cls, arg4):
        return arg4
    
    # DEFINING CLASS METHOD FOR INSTANTIATION
    @classmethod
    def method3(cls, x, y):
        return cls(x**2, y**2)
    
    
# INSTANTIATION
instance1 = CLASS(1, 2)
instance1.method1(4)

instance2 = CLASS.method3(1, 2)	# INSTANTIATE: arg1 = 1**1, arg2 = 2**2
instance2.method1(4)

# THEREFORE...
instance1.A			# >> OUTPUT: 1
instance1.B			# >> OUTPUT: 2
instance1.C			# >> OUTPUT: 4

instance2.A			# >> OUTPUT: 1 (= 1**2)
instance2.B			# >> OUTPUT: 4 (= 2**2)
instance3.C			# >> OUTPUT: 4

CLASS.method2(3)	# >> OUTPUT: 3
```

## Static Method

A method that can be called without instantiation, but without parameter to call itself like `self` and `cls`.

| SYNTAX          | DESCRIPTION                               |
| --------------- | ----------------------------------------- |
| `@staticmethod` | Decorator used to declare static methods. |

Since static method does not have a parameter to call itself, static method cannot access or modify any attribute from class and instance. This makes static method identical to normal function belonged to class.

```python
# CREATING CLASS
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


# INSTANTIATION
instance = CLASS(1, 2)
instance.method1(4)

# THEREFORE...
instance.A			# >> OUTPUT: 1
instance.B			# >> OUTPUT: 2
instance.C			# >> OUTPUT: 4

CLASS.method2(4)	# >> OUTPUT: True
```

## Magic Method

Magic method is a special method which has Double UNDERscores(dunder) on both side of its name. These method generally represents operator, and are referenced to overload operator to modify the operator's functionality. 

Previously encountered `__init__` method used for instance initialization is one of the widely used magic method. More can be seen on the table below:

| OPERATOR | NAME           | MAGIC METHOD               |
| -------- | -------------- | -------------------------- |
| `+`      | Addition       | `__add__(self, other)`     |
| `-`      | Subtraction    | `__sub__(self, other)`     |
| `*`      | Multiplication | `__mul__(self, other)`     |
| `/`      | Division       | `__truediv__(self, other)` |
| `&`      | AND            | `__and__(self, other)`     |
| `^`      | XOR            | `__xor__(self, other)`     |
| `|`      | OR             | `__or__(self, other)`      |

### Operator Overloading

Overloading operator means customizing operator to function differently on certain classes or portion of the script. Magic method is used to overload operator but overloaded functionality is only exclusive to that specific class. As an example, `x + y`  is expressed as `x.__add__(y)` .

```python
class CLASS:
    def __init__(self, arg1):
        self.A = arg1
        
    def __add__(self, arg2):
        return "&".join([self.A, arg2])		# INSERT "&" BETWEEN TWO STRING OBJECTS.

    
var1 = CLASS("Hello")
var2 = CLASS("World!")
print(var1 + var2)
```

```
Hello&World!
```

## Inheritance

Inheritance is act of superclass providing (inheriting) attributes and methods to derived subclass.

Any class that inherits attributes and methods and class that derives from are called superclass (base class) and subclass (child class) respectively. When the same name of attributes and methods exists on both superclass and subclass, superclass's attributes are overwritten by attributes of subclass.

Inheritance can be done through multiple instances but cannot have circular inheritance.

```python
class SUPERCLASS:
    def __init__(self, arg1, arg2):
        self.A = arg1
        self.B = arg2

        
# DERIVE SUBLCASS (BUT NO INHERITANCE YET)
class SUBCLASS (SUPERCLASS):
    def __init__(self, x, y):
        super().__init__(y, x)	# INHERITING SUPERCLASS'S ATTRIBUTES AND METHODS
        """EQUIVALENT:
        super(SUBCLASS, self).__init__(arg1 = y, arg2 = x)
        """
        self.A = x
        self.C = y


# INSTANTIATION  
instance = SUBCLASS(1, 3)

instance.A		# >> OUTPUT: 1 (ALTHOUGH INHERITED "self.A = 3", OVERWRITTEN BY SUBCLASS)
instance.B		# >> OUTPUT: 1 (ATTRIBUTE "B" INHERITED FROM SUPERCLASS)
instance.C		# >> OUTPUT: 3
```

### Super Function

The `super()` function calls the attributes or methods from its superclass directly. Without this function, the `instance.B` will cause "AttributeError" saying no attribute `B` exist within `SUBCLASS` instance. 

The following syntax is used for single base class inheritance:

```python
class SUBCLASS(SUPERCLASS):
    super().__init__()
    super().attribute
```

### Diamond Problem

Diamond problem refers to the inheritance logic problem where a single subclass (`SUBCLASS`) is inherited from two classes (`INTERCLASS1` and `INTERCLASS2`) derived from a single superclass (`SUPERCLASS`). In such case, it is likely that inheritance from superclass occurs twice to the subclass.

This occurrence can be prevented using `super()` function:

```python
# SUPERCLASS
class SUPERCLASS:
    def __init__():
        print("START SUPERCLASS __INIT__")
        print("----")
        print("END SUPERCLASS __INIT__")
        
        
# TWO INTERMEDIATE CLASSES DERIVED FROM SUPERCLASS
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
        
        
# SUBCLASS DERIVED FROM TWO INTERMEDIATE CLASSES
class SUBCLASS(INTERCLASS1, INTERCLASS2):
    def __init__():
        print("START SUBCLASS __INIT__")
        super().__init__()
        print("END SUBCLASS __INIT__")
        
        
# INSTANTIATION
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

The result above shows the superclass is only inherited once, this is due to `super()` function recognizing the inheritance pattern and skips extra inheritance from superclass.

## Lifecycle of Object

Object has three stages of lifecycle:

1. **Definition**
    : a stage of creating class using keyword `class`.
2. **Instantiation**
    : creating an instance through `__init__` magic method.
3. **Destruction**
    : Python automatically deletes instance once the number of variables referring to the instance counts down to zero, called reference count. Manual instance deletion can be done by `del` statement (aka. `__del__`  method). This process of instance deletion is called *garbage collection*.

## Encapsulation

Encapsulation is one of the fundamental concept which (1) combines attributes and methods into a single class data, and/or (2) restricts direct access to these attributes and methods (aka. data hiding). This feature prevents accidental modification on class from code outside.

### Data Hiding

Despite encapsulation is also implemented on Python classes, external code can still access to these attributes and methods as they are not restricted. If there are attributes and methods in class that needs to be hidden as possible, method such as name mangling is conventionally used in Python.

| SYMBOL | EXAMPLE       | DESCRIPTION                                                  |
| :----: | ------------- | ------------------------------------------------------------ |
|  `_`   | `_attribute`  | Though not a name mangling, it can prevent accessing attributes and methods from being passed via module import but not from codes outside the class. |
|  `__`  | `__attribute` | Name mangling: this prevents accessing attributes and methods from being passed via module import and codes outside the class, thus becomes "private". |

### Properties

Properties is a decorator that allows method to be updated without modifying the method directly. Because of this, property does not permitted direct change of data which makes the method seems read-only.

| SYNTAX      | DESCRIPTION                           |
| ----------- | ------------------------------------- |
| `@property` | Decorator used to declare properties. |

Property is declared using decorator symbol, meaning it is used specifically for method. One of the special feature of property is it does not take any argument except `self` variable to call itself from instance. Although property is based on method, syntax to call property is same as attribute: `instance.attribute`.

```python
class CLASS:
    def __init__(self, arg1, arg2):
        self.A = arg1
        self.B = arg2
        
    @property
    def method(self):
        return True
    
    
 # INSTANTIATION 
instance = CLASS(1, 3)
instance.method				# >> OUTPUT: True
instance.method = False		# AttributeError: can't set attribute
```

Properties are consist of three different method used for encapsulation: `getter`, `setter`, and `deleter`.

| METHOD  | SYNTAX            | DESCRIPTION                                           |
| ------- | ----------------- | ----------------------------------------------------- |
| Getter  | `@property`       | Method for getting the value from property attribute. |
| Setter  | `@method.setter`  | Method for setting the value of property attribute.   |
| Deleter | `@method.deleter` | Method for deleting property attribute.               |

```python
# CREATING CLASS
class CLASS:
    def __init__(self, arg1, arg2):
        self.A = arg1
        self.B = arg2
        
    @property			# GETTER METHOD
    def method(self):
        return self.A
        
    @method.setter		# SETTER METHOD
    def method(self, arg3):
        statements
        
    @method.deleter		# DELETER METHOD
    def method(self):
        del self.A
```

The `setter` method is used to modify the property attribute which may seems like defining property is unnecessary. However, this is not true as a single function is separated into more than one method: method exclusive for setting value and returning value.

Using the property with these methods encapsulate sensitive codes that shouldn't be modified by the user (such as `setter` method), while maintaining constant API user can access despite having updated function.
