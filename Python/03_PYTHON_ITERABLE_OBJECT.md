# **PYTHON: ITERABLE OBJECT**

Not just its simplicity that makes Python language useful, its iterable object is powerful and flexible than any other programming language can provide. While C++ has a iterable object called *array* and *vector*, Python has four iterable object that has same features but with slightly different properties.

## Iterable Object

Iterable object is used to store collection of data, and is defined by an object that has `__iter__` method (Python3) which returns iterator object. Iterator is an object which automatically calls next element of data, thus iterates every data within the iterable object in sequence.

One of the special feature of iterable object is it can access and/or modify stored data using a bracket `[]`. String object introduced in *PYTHON: BASIC § String Data Type* is also an iterable object.

```python
variable = "Hello World!" 
print(variable[1])
```

```
e
```

### Iterable Slicing

Slicing is one of the powerful feature Python has advantage over other programming languages on handling a group of data such as iterable object. Slicing iterable can only extract desired portion of the original.

|  SYNTAX   | EXAMPLE                            |
| :-------: | ---------------------------------- |
| `[ : : ]` | `iterable[start : end : interval]` |

Slicing starts from `start` (inclusive) until `end` (exclusive) with interval of `interval`. All thee arguments do not have to be filled to slice an iterable.

```python
variable = "Hello World!"
print(variable[2:8])	# >> OUTPUT: "llo Wo"

# SLICE FROM/UNTIL THE END OF THE LIST
print(variable[2: ])	# >> OUTPUT: "llo World!"
print(variable[ :8])	# >> OUTPUT: "Hello Wo"

# SLICE WITH SKIPPING SOME ELEMENTS WITH INTERVAL
print(variable[ : :2])	# >> OUTPUT: "HloWrd"
print(vairalbe[2:8:2])	# >> OUTPUT: "oW"

# REVERSE INTERVAL
print(variable[8:2:-1])	# >> OUTPUT: "roW ol"
```

## Range

Range iterable object stores a number in sequenced pattern by specifying starting number (inclusive), ending number (exclusive), and sequencing interval. Range object is created using the `range()` function:

| FUNCTION  | EXAMPLE                      | DESCRIPTION                                                  |
| --------- | ---------------------------- | ------------------------------------------------------------ |
| `range()` | `range(start, end,interval)` | Creates a range object that has `legnth` number of sequence of integer starting from default `start = 0`.<br /><br />*[OPTIONAL: Sequence starts from `start_num` number (not an index) with `interval`. For easier understanding, refer to the sample code below.]* |

```python
variable = range(3, 10, 2)

variable[0]		# >> OUTPUT: 3
variable[1]		# >> OUTPUT: 5
variable[2]		# >> OUTPUT: 7
variable[3]		# >> OUTPUT: 9
```

## List

List iterable object stores item in sequence along its index, irrelevant to data type. Assigning value to a list is done using a bracket ` []` by with values in order, comma separated. Bracket is also used to call an element at index location.

```python
lst = [value1, value2, value3, value4, ... ]

print(lst)			# >> OUTPUT: [value1, value2, value3, value4, ... ]
print(lst[0])		# >> OUTPUT: value1
```

It is possible to change the existing value by reassigning individual element. Calling the element that is outside the range of list is not possible and will results error.

```python
lst = [value1, value2, value3]

lst[1] = value4		# >> RESULT: lst = [value1, value4, value3]
lst[3] = value5		# IndexError: list assignment index out of range
```

List can be created programmatically if the elements observe specific sequencing pattern, called **List Comprehension**. This requires `for` loop with optional `if` conditional statement.

| SYNTAX          | EXAMPLE                                          |
| --------------- | ------------------------------------------------ |
| `[ for in if ]` | `lst[element for index in iterable if condtion]` |

This creates a list containing `elem` data based on variable `index` from `iterable` object while the `condition` is true; `if` statement in comprehension is optional.

```python
lst = [i**2 for i in range(5)]
lst = [i**2 for i in range(5) if (i**2) % 2 == 0]
```

```
[0, 1, 4, 9, 16]
[0, 4, 16]
```

### List Operation

A list can be added and multiplied, with operations exclusive to iterable objects. Operations below are not restricted to a list alone but can be applied to other iterable objects introduced later.

| OPERATOR | NAME           | DESCRIPTION                                                  |
| -------- | -------------- | ------------------------------------------------------------ |
| `+`      | Addition       | Merge two or more different lists to a single list.          |
| `*`      | Multiplication | Multiply the string by the number of integer (float does not work). |
| `in`     | Included       | Check if an item is in a list.                               |

```python
lst = [value1, value2, value3]

# + OPERATOR
print(lst + [value3, value4])	 # >> OUTPUT: [value1, value2, value3, value3, value4]

# * OPERATOR
print(lst * 2)				   	# >> OUTPUT: [value1, value2, value3, value1, value2, value3]

# in OPERATOR
print(value1 in lst)		   	# >> OUTPUT: True
print(value2 not in lst)		# >> OUTPUT: False
```

Following are functions that does certain features to and for a list (or more like iterable) object.

| FUNCTION      | EXAMPLE                             | DESCRIPTION                                                  |
| ------------- | ----------------------------------- | ------------------------------------------------------------ |
| `len()`       | `len(lst)`                          | Find the length of the `lst` list by counting elements.      |
| `all()`       | `all([condition for index in lst])` | Return `True` when all elements inside the `lst` list meets `condition`. |
| `any()`       | `any([condition for index in lst])` | Return `True` when any element inside the `lst` list meets `condition`. |
| `enumerate()` | `enumerate(lst)`                    | Iterates elements inside the `lst` list with sequencing.     |
| `list()`      | `list(iterable)`                    | Convert an iterable object (such as string and range) to a list; creates empty list if `iterable` is not presented. |

```python
lst = [10, 9, 8, 7, 6]

# ALL() FUNCTION
if all( [var > 5 for var in lst] ):
    print("Numbers are all above 5.")		   # >> OUTPUT: Numbers are all above 5.

# ANY() FUNCTION
if any( [ var % 2 ==  0 for var in lst] ):
    print("At least one number is even.")	   # >> OUTPUT: At least one number is even.
    
# ENUMERATE() FUNCTION
for var in enumerate(lst):
    print(var)								 # >> OUTPUT: (0,10)
                                                # >>		 (1,9)
                                                # >>		 (2,8)
                                                # >>		 (3,7)
                                                # >>		 (4,6)
```

Since list is an (iterable) object, it also has methods it can use to perform certain features:

| METHOD     | EXAMPLE                    | DESCRIPTION                                                |
| ---------- | -------------------------- | ---------------------------------------------------------- |
| `append()` | `lst.append(value)`        | Add `value` at the end of the `lst` list.                  |
| `insert()` | `lst.insert(index, value)` | Add `value` at `index` element location of the `lst` list. |
| `index()`  | `lst.index(value)`         | Find the smallest number of location of `value`.           |

## Tuple

Tuple iterable object is used to store item in order just like a list, but cannot change value after initialization. This property of iterable object is called immutable (opp. mutable). Tuple use parentheses `()` or even without any to distinguish itself from other iterable.

```python
tpl = (value1, value2, value3)
print(tpl)			# >> OUTPUT: (value1, value2, value3)
print(tpl[0])		# >> OUTPUT: value1

# ALTERNATIVE: tuple without parentheses
tpl = value1, value2, value3
print(tpl)			# >> OUTPUT: (value1, value2, value3)
print(tpl[0])		# >> OUTPUT: value1
```

Because tuple is a constant version of a list, the data inside cannot be changed. The error will occur when such effort is made.

```python
tpl = (value1, value2, value3)
tpl[1] = value4
```

```
TypeError: 'tuple' object does not support item assignment
```

Tuple operation can be referred from operation, function, and method table in *PYTHON: ITERABLE OBJECT § List Operation* subsection.


### Unpacking Tuple

Unpacking tuple means assigning individual element in tuple to variables or another tuples. Placing asterisk `*` on prefix of a variable would return multiple leftover elements as a list object. This will be explained in *PYTHON: FUNCTIONAL PROGRAMMING § Parameters & Arguments* subsection.

```python
variable1, variable2, *variable3, variable3 = [value1, value2, value3, value4, value5]

print(variable1)		# >> OUTPUT: value1
print(variable2)		# >> OUTPUT: value2
print(variable3)		# >> OUTPUT: [value3, value4]
print(variable3)		# >> OUTPUT: value5
```

## Dictionary

Dictionary is an iterable object that has indexing `key` data and `value` data paired as a single element. Dictionary does not call value by integer index but through `key`. Dictionary uses curly bracket `{}` to distinguish itself from other iterable.

```python
dictionary = {key1: value1, key2: value2, key3: value3}

print(dictionary[key1])		# >> OUTPUT: value1
print(dictionary[key2])		# >> OUTPUT: value2
print(dictionary[key4])		# KeyError: key4
```

Mutable object (e.g. list and dictionary) cannot be used as `key` of the element; only immutable object is allowed. However, mutable object can still be used as a `value` of the element.

```python
dictionary = {lst1: value1, key2: value2}
```

```
TypeError: unhashable type: 'list'
```

It is possible to change the existing `value` of the `key` within a dictionary. Unlike list object, creating new `key` data and assigning its `value` is also possible without needing any help from a method.

```python
dictionary = {key1: value1, key2: value2, key3: value3}
dictionary[key1] = value4
dictionary[key5] = value5
```

```
{key1: value1, key2: value2, key3: value3, key5: value5}
```

Operations for a dictionary is same as other iterable objects but have slight difference:

| OPERATOR | NAME                     | DESCRIPTION                                                  |
| -------- | ------------------------ | ------------------------------------------------------------ |
| `+`      | Addition                 | Merge two or more different lists to a single list.          |
| `*`      | Multiplication           | Multiply the string by the number of integer (float does not work). |
| `in`     | Included (key exclusive) | Check if the key is in a dictionary. However, it does not check the value. |

```python
dictionary = {key1: value1, key2: value2}

print(key1 in dictionary )			# >> OUTPUT: True
print(value2 in dictionary )		# >> OUTPUT: False
print(key3 not in dictionary )		# >> OUTPUT: True
```

Dictionary have its own function and method to execute certain features exclusive for dictionary:

| OPERATION | EXAMPLE                             | DESCRIPTION                                                  |
| --------- | ----------------------------------- | ------------------------------------------------------------ |
| `get()`   | `dictionary.get(key,[description])` | Find the key and get its value; additional description can be added when the key is not found (`None` by default). |
| `dict()`  | `dictionary=dict()`                 | Can create empty dictionary.                                 |

```python
dictionary = {key1: value1, key2: value2}

print(dictionary.get(key0))							# >> OUTPUT: value1
print(dictionary.get(key2))							# >> OUTPUT: None
print(dictionary.get(key3, "not in dictionary"))	  # >> OUTPUT: not in dictionary
```

## Set

Set is an iterable object that guarantees uniqueness, meaning it does not allow duplicate element within the object. Just like dictionary, set uses curly bracket `{}` to assign values but without `key`-`value` pair. Due to the reasons above, set is much faster to check the elements than list.

```python
st = {value1, value2, value3}
print(st)
```

```
{value1, value2, value3}
```

Set have mathematical operations available which works exactly like mathematical set.

| OPERATION | NAME                 | DESCRIPTION                                                  |
| --------- | -------------------- | ------------------------------------------------------------ |
| `|`       | Union                | Returns the combined of two sets.                            |
| `&`       | Intersection         | Returns data which only exist in both sets.                  |
| `-`       | Difference           | Returns data which only exist in subtrahend and not in minuend. |
| `^`       | Symmetric difference | Return data exclusive to each set, but not both.             |

```python
set1 = {1, 2, 3, 4, 5, 6}
set2 = {4, 5, 6, 7, 8, 9}

print(set1 | set2)		# >> OUTPUT: {1, 2, 3, 4, 5, 6, 7, 8, 9}

print(set1 & set2)		# >> OUTPUT: {4, 5, 6}

print(set1 - set2)		# >> OUTPUT: {1, 2, 3}
print(set2 - set1)		# >> OUTPUT: {7, 8, 9}

print(set1 ^ set2)		# >> OUTPUT: {1, 2, 3, 7, 8, 9}
```

Set have its own function to execute certain features exclusive for set:

| FUNCTION | EXAMPLE         | DESCRIPTION                                                  |
| -------- | --------------- | ------------------------------------------------------------ |
| `set()`  | `set(iterable)` | Function which creates a set: list and tuple assigned with parentheses `()` are allowed, but dictionary is not possible. |

The function above is necessary when creating an empty set, as `{}` creates an empty dictionary instead. Meanwhile, the methods used by set object are as follows:

| METHOD     | EXAMPLE             | DESCRIPTION                                                 |
| ---------- | ------------------- | ----------------------------------------------------------- |
| `add()`    | `set.add(value)`    | Add `value` at the end of the set.                          |
| `remove()` | `set.remove(value)` | Remove `value` in the set.                                  |
| `pop()`    | `set.pop()`         | Randomly selected element is popped (removed) from the set. |

```python
st = set([value1, value2, value3, value1])
print(st)				# >> OUTPUT: {value1, value2, value3}

set0.add(value4)
set0.remove(value1)
print(st)				# >> OUTPUT: {value2, value3, value4}

print(st.pop())			# >> OUTPUT: value2 (randomly popped)
print(st)				# >> OUTPUT: {value3, value4}
```

## Generator

Generator is an iterable object that can be created by developer using `yield` and `for` loop statement. Generator is especially useful due to its absence of memory restrictions, allowing generator to yield infinite number of data.

```python
# CREATING THE GENERATOR.
def generator_function():
    var = 0
    while var < 5
        yield var
        var += 1

# ITERATING GENERATOR ELEMENT-BY-ELEMENT.
for var in generator_function():
    print(var)

# CONVERSION TO "LIST" DATA TYPE.
lst = list(generator_function())
print(lst)
```

```
0
1
2
3
4
[0, 1, 2, 3, 4]
```

### `yield` Keyword

A keyword used to create a generator; keyword returns the value when iterated by `for` loop statement.

# **파이썬: 이터러블 객체**

파이썬 언어를 유용하게 만드는 것은 단순함뿐만이 아니라, 이터러블 객체는 다른 프로그래밍 언어가 제공할 수 잇는 것보다 강력하고 유연한다. C++은 *array*와 *vector*라고 하는 반복 가능한 객체를 가지고 있는 반면, 파이썬은 기능은 같지만 속성은 약간 다른 4개의 반복 가능한 객체를 가지고 있다.

## 이터러블 객체

이터러블 객체는 수집한 데이터를 저장하는데 사용되며 반복기 객체를 반환하며 `__iter__` 메서드(파이썬 3)를 가진 객체에 의해 정의된다. 반복기는 데이터의 다음 요소를 자동으로 호출하는 객체로, 반복 가능한 객체 내의 모든 데이터를 순차적으로 반복한다.

이터러블 객체의 특징 중 하나는 브라캣 `[]`을 사용하여 저장된 데이터에 액세스 또는 수정이 가능하다는 것이다. *파이썬: 기초 문자열 자료형*에 도입된 문자열 객체도 반복 가능한 객체다.

```python
variable = "Hello World!" 
print(variable[1])
```

```
e
```

### 이터러블 객체의 슬라이싱

슬라이싱은 파이썬이 이터러블 객체와 같은 데이터 그룹을 처리하는데 있어 다른 프로그래밍 언어보다 뛰어난, 강력한 기능 중 하나이다. 이터러블 객체의 슬라이싱은 원본에서 원하는 부분만 추출할 수 있다.

|  구문     | 예시                            |
| :-------: | ---------------------------------- |
| `[ : : ]` | `이터러블 객체[시작 : 끝 : 간격]` |

슬라이싱은 `시작`(포함)에서 `끝`(제외)까지이며, 간격은 `간격`이다. 많은 인수를 슬라이싱 하기 위해 많은 인수 전부다 채울 필요는 없다.

```python
variable = "Hello World!"
print(variable[2:8])	# >> 출력: "llo Wo"

# SLICE FROM/UNTIL THE END OF THE LIST 
print(variable[2: ])	# >> 출력: "llo World!"
print(variable[ :8])	# >> 출력: "Hello Wo"

# SLICE WITH SKIPPING SOME ELEMENTS WITH INTERVAL
print(variable[ : :2])	# >> 출력: "HloWrd"
print(vairalbe[2:8:2])	# >> 출력: "oW"

# REVERSE INTERVAL
print(variable[8:2:-1])	# >> 출력: "roW ol"
```

## 범위(Range)

범위 이터러블 객체는 시작 번호(포함), 끝 번호(제외) 및 순서 간격을 지정하여 숫자 시퀀스를 저장한다. 범위 객체는 `range()` 함수를 사용하여 생성된다.

| 함수      | 예시                        | 설명                                                  |
| --------- | ---------------------------- | ------------------------------------------------------------ |
| `range()` | `range(start, end,interval)` | `length` 갯수를 가지고있으며 기본 `start = 0`에서 시작하는 정수 시퀀스 범위 객체를 만든다.<br /><br />*[옵션: 시퀀스은 `interval`이 아닌 `start_num` 번호에서 시작한다. 이해하기 쉽도록 아래의 샘플 코드를 참고하기 바람]* |

```python
variable = range(3, 10, 2)

variable[0]		# >> 출력: 3
variable[1]		# >> 출력: 5
variable[2]		# >> 출력: 7
variable[3]		# >> 출력: 9
```

## 리스트(List)

데이터 유형과 관계 없이 이터러블 객체가 인덱스를 따라 항목을 순서대로 나열한다. 리스트에 값을 할당하는 작업은 쉼표로 구분된 순서대로 브라캣 ` []`을 사용하여 수행된다. 또한 브라캣은 인덱스 위치에서 원소를 호출하는데 사용된다.

```python
lst = [value1, value2, value3, value4, ... ]

print(lst)			# >> ㅊ: [value1, value2, value3, value4, ... ]
print(lst[0])		# >> ㅊ: value1
```

개별 원소를 재할당하여 기존 값을 변경할 수 있다. 리스트 범위를 벗어난 요소를 호출할 수 없으므로, 호출한다면 오류가 발생한다.

```python
lst = [value1, value2, value3]

lst[1] = value4		# >> 결과: lst = [value1, value4, value3]
lst[3] = value5		# IndexError: list assignment index out of range
```

원소가 **리스트 컴프리헨션**라는 특정 시퀀스 패턴을 발견할 경우 프로그래밍 방식으로 리스트를 만들 수 있다. 이를 위해서는 `if`조건문(선택가능)이 있는 `for`루프가 필요하다.

| 구문          | 예시                                          |
| --------------- | ------------------------------------------------ |
| `[ for in if ]` | `lst[element for index in iterable if condtion]` |

이는 변수`index`에 근거한 `원소`데이터를 포함하고 있는 이터러블 객체를 만들며 동시에 `조건`은 참이며; `if`문은 컴프리헨션에서 선택적이다.

```python
lst = [i**2 for i in range(5)]
lst = [i**2 for i in range(5) if (i**2) % 2 == 0]
```

```
[0, 1, 4, 9, 16]
[0, 4, 16]
```

### List Operation

A list can be added and multiplied, with operations exclusive to iterable objects. Operations below are not restricted to a list alone but can be applied to other iterable objects introduced later.

| OPERATOR | NAME           | DESCRIPTION                                                  |
| -------- | -------------- | ------------------------------------------------------------ |
| `+`      | Addition       | Merge two or more different lists to a single list.          |
| `*`      | Multiplication | Multiply the string by the number of integer (float does not work). |
| `in`     | Included       | Check if an item is in a list.                               |

```python
lst = [value1, value2, value3]

# + OPERATOR
print(lst + [value3, value4])	 # >> ㅊ: [value1, value2, value3, value3, value4]

# * OPERATOR
print(lst * 2)				   	# >> ㅊ: [value1, value2, value3, value1, value2, value3]

# in OPERATOR
print(value1 in lst)		   	# >> ㅊ: True
print(value2 not in lst)		# >> ㅊ: False
```

Following are functions that does certain features to and for a list (or more like iterable) object.

| FUNCTION      | EXAMPLE                             | DESCRIPTION                                                  |
| ------------- | ----------------------------------- | ------------------------------------------------------------ |
| `len()`       | `len(lst)`                          | Find the length of the `lst` list by counting elements.      |
| `all()`       | `all([condition for index in lst])` | Return `True` when all elements inside the `lst` list meets `condition`. |
| `any()`       | `any([condition for index in lst])` | Return `True` when any element inside the `lst` list meets `condition`. |
| `enumerate()` | `enumerate(lst)`                    | Iterates elements inside the `lst` list with sequencing.     |
| `list()`      | `list(iterable)`                    | Convert an iterable object (such as string and range) to a list; creates empty list if `iterable` is not presented. |

```python
lst = [10, 9, 8, 7, 6]

# ALL() FUNCTION
if all( [var > 5 for var in lst] ):
    print("Numbers are all above 5.")		   # >> OUTPUT: Numbers are all above 5.

# ANY() FUNCTION
if any( [ var % 2 ==  0 for var in lst] ):
    print("At least one number is even.")	   # >> OUTPUT: At least one number is even.
    
# ENUMERATE() FUNCTION
for var in enumerate(lst):
    print(var)								 # >> OUTPUT: (0,10)
                                                # >>		 (1,9)
                                                # >>		 (2,8)
                                                # >>		 (3,7)
                                                # >>		 (4,6)
```

Since list is an (iterable) object, it also has methods it can use to perform certain features:

| METHOD     | EXAMPLE                    | DESCRIPTION                                                |
| ---------- | -------------------------- | ---------------------------------------------------------- |
| `append()` | `lst.append(value)`        | Add `value` at the end of the `lst` list.                  |
| `insert()` | `lst.insert(index, value)` | Add `value` at `index` element location of the `lst` list. |
| `index()`  | `lst.index(value)`         | Find the smallest number of location of `value`.           |

## Tuple

Tuple iterable object is used to store item in order just like a list, but cannot change value after initialization. This property of iterable object is called immutable (opp. mutable). Tuple use parentheses `()` or even without any to distinguish itself from other iterable.

```python
tpl = (value1, value2, value3)
print(tpl)			# >> OUTPUT: (value1, value2, value3)
print(tpl[0])		# >> OUTPUT: value1

# ALTERNATIVE: tuple without parentheses
tpl = value1, value2, value3
print(tpl)			# >> OUTPUT: (value1, value2, value3)
print(tpl[0])		# >> OUTPUT: value1
```

Because tuple is a constant version of a list, the data inside cannot be changed. The error will occur when such effort is made.

```python
tpl = (value1, value2, value3)
tpl[1] = value4
```

```
TypeError: 'tuple' object does not support item assignment
```

Tuple operation can be referred from operation, function, and method table in *PYTHON: ITERABLE OBJECT § List Operation* subsection.


### Unpacking Tuple

Unpacking tuple means assigning individual element in tuple to variables or another tuples. Placing asterisk `*` on prefix of a variable would return multiple leftover elements as a list object. This will be explained in *PYTHON: FUNCTIONAL PROGRAMMING § Parameters & Arguments* subsection.

```python
variable1, variable2, *variable3, variable3 = [value1, value2, value3, value4, value5]

print(variable1)		# >> OUTPUT: value1
print(variable2)		# >> OUTPUT: value2
print(variable3)		# >> OUTPUT: [value3, value4]
print(variable3)		# >> OUTPUT: value5
```

## Dictionary

Dictionary is an iterable object that has indexing `key` data and `value` data paired as a single element. Dictionary does not call value by integer index but through `key`. Dictionary uses curly bracket `{}` to distinguish itself from other iterable.

```python
dictionary = {key1: value1, key2: value2, key3: value3}

print(dictionary[key1])		# >> OUTPUT: value1
print(dictionary[key2])		# >> OUTPUT: value2
print(dictionary[key4])		# KeyError: key4
```

Mutable object (e.g. list and dictionary) cannot be used as `key` of the element; only immutable object is allowed. However, mutable object can still be used as a `value` of the element.

```python
dictionary = {lst1: value1, key2: value2}
```

```
TypeError: unhashable type: 'list'
```

It is possible to change the existing `value` of the `key` within a dictionary. Unlike list object, creating new `key` data and assigning its `value` is also possible without needing any help from a method.

```python
dictionary = {key1: value1, key2: value2, key3: value3}
dictionary[key1] = value4
dictionary[key5] = value5
```

```
{key1: value1, key2: value2, key3: value3, key5: value5}
```

Operations for a dictionary is same as other iterable objects but have slight difference:

| OPERATOR | NAME                     | DESCRIPTION                                                  |
| -------- | ------------------------ | ------------------------------------------------------------ |
| `+`      | Addition                 | Merge two or more different lists to a single list.          |
| `*`      | Multiplication           | Multiply the string by the number of integer (float does not work). |
| `in`     | Included (key exclusive) | Check if the key is in a dictionary. However, it does not check the value. |

```python
dictionary = {key1: value1, key2: value2}

print(key1 in dictionary )			# >> OUTPUT: True
print(value2 in dictionary )		# >> OUTPUT: False
print(key3 not in dictionary )		# >> OUTPUT: True
```

Dictionary have its own function and method to execute certain features exclusive for dictionary:

| OPERATION | EXAMPLE                             | DESCRIPTION                                                  |
| --------- | ----------------------------------- | ------------------------------------------------------------ |
| `get()`   | `dictionary.get(key,[description])` | Find the key and get its value; additional description can be added when the key is not found (`None` by default). |
| `dict()`  | `dictionary=dict()`                 | Can create empty dictionary.                                 |

```python
dictionary = {key1: value1, key2: value2}

print(dictionary.get(key0))							# >> OUTPUT: value1
print(dictionary.get(key2))							# >> OUTPUT: None
print(dictionary.get(key3, "not in dictionary"))	  # >> OUTPUT: not in dictionary
```

## Set

Set is an iterable object that guarantees uniqueness, meaning it does not allow duplicate element within the object. Just like dictionary, set uses curly bracket `{}` to assign values but without `key`-`value` pair. Due to the reasons above, set is much faster to check the elements than list.

```python
st = {value1, value2, value3}
print(st)
```

```
{value1, value2, value3}
```

Set have mathematical operations available which works exactly like mathematical set.

| OPERATION | NAME                 | DESCRIPTION                                                  |
| --------- | -------------------- | ------------------------------------------------------------ |
| `|`       | Union                | Returns the combined of two sets.                            |
| `&`       | Intersection         | Returns data which only exist in both sets.                  |
| `-`       | Difference           | Returns data which only exist in subtrahend and not in minuend. |
| `^`       | Symmetric difference | Return data exclusive to each set, but not both.             |

```python
set1 = {1, 2, 3, 4, 5, 6}
set2 = {4, 5, 6, 7, 8, 9}

print(set1 | set2)		# >> OUTPUT: {1, 2, 3, 4, 5, 6, 7, 8, 9}

print(set1 & set2)		# >> OUTPUT: {4, 5, 6}

print(set1 - set2)		# >> OUTPUT: {1, 2, 3}
print(set2 - set1)		# >> OUTPUT: {7, 8, 9}

print(set1 ^ set2)		# >> OUTPUT: {1, 2, 3, 7, 8, 9}
```

Set have its own function to execute certain features exclusive for set:

| FUNCTION | EXAMPLE         | DESCRIPTION                                                  |
| -------- | --------------- | ------------------------------------------------------------ |
| `set()`  | `set(iterable)` | Function which creates a set: list and tuple assigned with parentheses `()` are allowed, but dictionary is not possible. |

The function above is necessary when creating an empty set, as `{}` creates an empty dictionary instead. Meanwhile, the methods used by set object are as follows:

| METHOD     | EXAMPLE             | DESCRIPTION                                                 |
| ---------- | ------------------- | ----------------------------------------------------------- |
| `add()`    | `set.add(value)`    | Add `value` at the end of the set.                          |
| `remove()` | `set.remove(value)` | Remove `value` in the set.                                  |
| `pop()`    | `set.pop()`         | Randomly selected element is popped (removed) from the set. |

```python
st = set([value1, value2, value3, value1])
print(st)				# >> OUTPUT: {value1, value2, value3}

set0.add(value4)
set0.remove(value1)
print(st)				# >> OUTPUT: {value2, value3, value4}

print(st.pop())			# >> OUTPUT: value2 (randomly popped)
print(st)				# >> OUTPUT: {value3, value4}
```

## Generator

Generator is an iterable object that can be created by developer using `yield` and `for` loop statement. Generator is especially useful due to its absence of memory restrictions, allowing generator to yield infinite number of data.

```python
# CREATING THE GENERATOR.
def generator_function():
    var = 0
    while var < 5
        yield var
        var += 1

# ITERATING GENERATOR ELEMENT-BY-ELEMENT.
for var in generator_function():
    print(var)

# CONVERSION TO "LIST" DATA TYPE.
lst = list(generator_function())
print(lst)
```

```
0
1
2
3
4
[0, 1, 2, 3, 4]
```

### `yield` Keyword

A keyword used to create a generator; keyword returns the value when iterated by `for` loop statement.