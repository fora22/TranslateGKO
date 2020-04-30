# **PYTHON: OBJECT-ORIENTED PROGRAMMING**

Previous chapter has explained and dealt with procedural and functional programming. The third scripting method, object-oriented programming (abbrev. OOP) is based around usage of classes and objects instead of functions.

## Object

Object (aka. instance) is a block of data which acts like a building brick; every object has its own attributes that are properties and capabilities of the object. The attribute can be accessed and utilized by `object.attribute` format.

The programming based around use of a custom objects is called *object-oriented programming*.

```python
# OBJECT "x" CALLING METHOD "append()" AVAILABLE IN STRING
x = [0 ,3 ,5 ,9]
print( x.append(13) )
```

```
[0, 3, 5, 9, 13]
```

### Method & Attribute

Below is a description of method and attribute of an object in Python.

* **Method**
    : method is an object-dependent function that is bounded by the object, meaning the object needs to be presented to use a method and cannot be used independently.

* **Attribute**
    : attribute is a features and properties of the object (including bounded function). Hence, methods are included as one of the attributes of the object. However, for easier understanding, this document will distinguish attribute as attribute without methods.

## Class

Class is used to create objects (aka. instance), hence can be deemed as an object’s blueprint. Classes are created first by a keyword `class` containing functions as method of the class in indented block.

```python
# CREATING CLASS
class CLASS∶
	global var			# GLOBAL VARIABLE: LINKED TO VARAIBLE OUTSIDE WITH SAME NAME
    attr0 = value		# CLASS ATTRIBUTE
    
    # INSTANCE INITIALIZATION (= CONSTRUCTOR)
    def __init__(self, arg1, arg2):
        # INSTANCE ATTRIBUTES
        self.attr1 = arg1
        self.attr2 = arg2
        
    # INSTANCE METHOD
    def method(self, arg3):
        """
        statements including var3
        """
        return arg3

var = "Hello World!"			# DECLARE VARIABLE (LINKED TO GLOBAL VARIABLE)
instance = CLASS(var1, var2)	# CREATE INSTANCE FROM THE CLASS

instance.method(var3)			# CALLING METHOD
instance.var					# CALLING ATTRIBUTE
```

```
var3
"Hello World!"
```

### `__init__` Method

The `__init__` method is the most important method in class which is used to create class constructor (like the *constructor* in C/C++ language). This method defines how many parameters the instance can have and also responsible for initializing attribute values for instance.

The `__init__` method automatically called only when instance is created from the class. Therefore, initialized attribute can only be access through instance, but not from the class directly. As oppose to this, attribute declared outside the `__init__` method is accessible from both instance and class.

### Global Variable

Variable assigned with `global` keyword represents global variable. This variable is linked to the variable outside the class but shares the same name.

Without `global` keyword, the variable inside the class becomes local variable. Local variable and variable declared outside the class will be irrelevant to each other.

## Instance Method

All methods (or attributes) that are declared normally within the class are instance methods (or attributes). There is no special syntax that need to declare for instance method.

Some may misunderstand instance method can be distinguished by checking whether the argument `self` is there or not. This is not true as `self` is purely an argument and has no power on defining the type of method or attribute. The detail information is explained under the subsection below.

### `self` Variable

The `self` variable is a conventional name to indicate a current instance, meaning it is not a keyword and the name can be set however developer wants. Variables with `self` prefix become instance attributes.

These instance attribute can be accessed only upon declaring an instance (like `this` pointer in C++ language). Variables without `self` prefix cannot be called from the instance as they are not an attribute but a plain local variables. Local variables cannot be called outside its scope of method, and attempting to do so results "AttributeError".

```python
# CREATING CLASS
class CLASS():
    def __init__(self, arg1, arg2, arg3):
        self.A = arg1
        self.B = arg2
        self.C
        D = arg3			# LOCAL VARIABLE
        
    def method(other, x)	# REPLACING "self" VARIABLE TO DIFFERENT NAME STILL WORKS.
    	other.C = x			# ATTRIBUTE "self.C" IS AVAILABLE IN DIFFERENT METHODS.


# INSTANTIATION
instance = CLASS(1, 2, 3)
instance.method(4)
'''EQUIVALENT: 
Class.__init__(self = instance, arg1 = 1, arg2 = 2, arg3 = 3)
Class.method_name(other = instance, x = 4)
'''

# THEREFORE...
CLASS.A			# AttributeError: type object 'Class' has no attribute 'A'

instance.A		# >> OUTPUT: 1
instance.B		# >> OUTPUT: 2
instance.C		# >> OUTPUT: 4
instance.D		# AttributeError: 'Class' object has no attribute 'D'
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