# **PYTHON: ITERABLE OBJECT**

Not just its simplicity that makes Python language useful, its iterable object is powerful and flexible than any other programming language can provide. While C++ has a iterable object called *array* and *vector*, Python has four iterable object that has same features but with slightly different properties.

## Iterable Object

An object with an `__iter__` method (Python3) which returns iterator object, eventually going through every data within the iterable object in sequence; called iteration.

### Iterator Object

An object with a `__next__` method (Python3) which automatically calls next element of data.

## List

List iterable object is used to store item in order along its index, irrelevant to data type. Defining the list object is done using a bracket ` []` by assigning values inside, comma separated. Bracket is also used to call an element at index location.

```python
lst = [int1, str2, lst3, any4, ... ]

print( lst )		# >> OUTPUT: [int1, str2, lst3, any4, ... ]
print( lst[0] )		# >> OUTPUT: int1
```

It is possible to change the existing value by reassigning individual element. Calling the element that is outside the range of list is not possible and will results error.

```python
lst = [int0, int1, int2]

lst[1] = int3		# >> RESULT: lst = [int0, int3, int2]
lst[3] = int4		# IndexError: list assignment index out of range
```

String data can be indexed like a list, where each element is a character consisting the string.

```python
variable ="Hello." 
print(variable[1])
```

```
e
```

A list can be added and multiplied, with operations exclusive to iterable objects. Operations below are not restricted to a list alone but can be applied to other iterable objects introduced later.

| OPERATOR | NAME           | DESCRIPTION                                                  |
| -------- | -------------- | ------------------------------------------------------------ |
| `+`      | Addition       | Merge two or more different lists to a single list.          |
| `*`      | Multiplication | Multiply the string by the number of integer (float does not work). |
| `in`     | Included       | Check if an item is in a list.                               |

```python
lst = [1, 2, 3]

# + OPERATOR
print( lst + [3, 4, 5] )	# >> OUTPUT: [1, 2, 3, 3, 4, 5]

# * OPERATOR
print( lst * 3 )			# >> OUTPUT: [1, 2, 3, 1, 2, 3, 1, 2, 3]

# in OPERATOR
print( 1 in lst )			# >> OUTPUT: True
print( 2 not in lst )		# >> OUTPUT: False
```

Following are functions that does certain features to and for a list (or more like iterable) object.

| FUNCTION      | EXAMPLE                             | DESCRIPTION                                                  |
| ------------- | ----------------------------------- | ------------------------------------------------------------ |
| `len()`       | `len(lst)`                          | Find the length of the `lst` list by counting elements.      |
| `all()`       | `all([condition for index in lst])` | Return `True` when all elements inside the `lst` list meets `condition`. |
| `any()`       | `any([condition for index in lst])` | Return `True` when any element inside the `lst` list meets `condition`. |
| `enumerate()` | `enumerate(lst)`                    | Iterates elements inside the `lst` list with sequencing.     |
| `list()`      | `list(iterable)`                    | Convert an iterable object to a list; creates empty list if `iterable` is not presented. |

```python
lst = [10, 9, 8, 7, 6]

# ALL() FUNCTION
if all( [var > 5 for var in lst] ):
	print("Numbers are all above 5.")		# >> OUTPUT: Numbers are all above 5.

# ANY() FUNCTION
if any( [ var % 2 ==  0 for var in lst] ):
	print("At least one number is even.")	# >> OUTPUT: At least one number is even.
    
# ENUMERATE() FUNCTION
for var in enumerate(lst):
	print(var)								# >> OUTPUT: (0,10)
    										# >>		 (1,9)
        									# >>		 (2,8)
            								# >>		 (3,7)
                							# >>		 (4,6)
```

Since list is an (iterable) object, it also has methods it can access to perform certain features:

| METHOD     | EXAMPLE                 | DESCRIPTION                                             |
| ---------- | ----------------------- | ------------------------------------------------------- |
| `append()` | `lst.append(data)`      | Add `data` at the end of the `lst` list.                |
| `insert()` | `lst.insert(int, data)` | Add `data` at `int` element location of the `lst` list. |
| `index()`  | `lst.index(data)`       | Find the smallest number of location of *data*.         |

```python
lst = [10, 9, 8, 7, 6]

# APPEND() METHOD
print( lst.append("7") )		# >> OUTPUT: [10, 9, 8, 7, 6, "7"]

# INSERT() METHOD
print( lst.insert(1,"7") )		# >> OUTPUT: [10, "7", 9, 8, 7, 6]

# INDEX() METHOD
print( lst.index(8) )			# >> OUTPUT: 2
```

### List Comprehension

List can be generated using a `for` loop and `if` condition syntax when elements have certain rule/pattern.

| SYNTAX          | EXAMPLE                                  |
| --------------- | ---------------------------------------- |
| `[ for in if ]` | `lst[elem for index in rng if condtion]` |

This creates a list according to the `elem` utilizing variable `var` in a range given by the range object `rng` when the `condition` is true; `if` statement in comprehension is optional.

```python
lst =[i**2 for i in range(5)]
lst =[i**2 for i in range(5) if (i**2)%2==0]
```

```
[0, 1, 4, 9, 16]
[0, 4, 16]
```

### List Slice

List slicing is one of the powerful tool Python has advantage over other programming languages. Slicing the list extracts portion of the original list, thus creates smaller list.

|  SYNTAX   | EXAMPLE                                 |
| :-------: | --------------------------------------- |
| `[ : : ]` | `lst[start_elem : end_elem : interval]` |

Slicing starts from `start_elem` (inclusive) until `end_elem` (exclusive) with interval of `interval`. All thee arguments do not have to be filled to slice the list.

```python
lst =[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
print( lst[2:8] )		# >> OUTPUT: [2, 3, 4, 5, 6, 7]

# SLICE FROM/UNTIL THE END OF THE LIST
print( lst[2:] )		# >> OUTPUT: [2, 3, 4, 5, 6, 7, 8, 9]
print( lst[:8] )		# >> OUTPUT: [0, 1, 2, 3, 4, 5, 6, 7]

# SLICE WITH SKIPPING SOME ELEMENTS WITH INTERVAL
print( lst[::2] )		# >> OUTPUT: [0, 2, 4, 6, 8]
print( lst[2:8:3] )		# >> OUTPUT: [2, 5]

# REVERSE INTERVAL
print( lst[7:3:-1] )	# >> OUTPUT: [7, 6, 5, 4]
```

## Tuple

Tuple iterable object is used to store item in order just like a list, but cannot change value of elements after its initialization. This property of iterable object is called immutable (opp. mutable). Tuple use parentheses `()` or even without any to distinguish itself from the List.

```python
tpl =(data0, data1, data2)
print( tpl )		# >> OUTPUT: (data0, data1, data2)
print( tpl[0] )		# >> OUTPUT: data0

# ALTERNATIVE: tuple without parentheses
tpl = data0, data1, data2
print( tpl )		# >> OUTPUT: (data0, data1, data2)
print( tpl[0] )		# >> OUTPUT: data0
```

Because tuple is a constant version of a list, the data inside cannot be changed. The error will occur when such effort is made.

```python
tpl = [data0, data1, data2]
tpl[1] = data3
```

```
TypeError: 'tuple' object does not support item assignment
```

Tuple operation can be referred from operation, function, and method table in *List* section.


### Unpacking Tuple

Unpacking tuple means assigning individual element in tuple to variables or another tuples. Placing asterisk `*` on prefix of a variable would return multiple number of elements as a list. This will be explained in *Parameters & Arguments* article section.

```python
var0, var1, *var2, var3 = [data0, data1, data2, data3, data4, data5]

print(var0)		# >> OUTPUT: data0
print(var1)		# >> OUTPUT: data1
print(var2)		# >> OUTPUT: [data2, data3, data4]
print(var3) 	# >> OUTPUT: data5
```

## Dictionary

Dictionary is an iterable object with data structured to maps the key elements to its value. Because of this property, dictionary does not call value by numerical index but through keys. Dictionary uses curly bracket `{}` to distinguish itself from other iterable objects.

```python
dictionary = {key0:value0, key1:value1, key2:value2}

print( dictionary[key0] )	# >> OUTPUT: value0
print( dictionary[key1] )	# >> OUTPUT: value1
print( dictionary[key3] )	# KeyError: key3
```

Mutable object (e.g. list and dictionary) cannot be used as a key element; only immutable object is allowed. However, mutable object can still be used as a value of the key.

```python
dictionary = {list0:value0, key1:value1}
```

```
TypeError: unhashable type: 'list'
```

It is possible to change the existing value of a key within a dictionary. Unlike list object, creating new key and assigning its value is also possible without needing any help from a method.

```python
dictionary = {key0:value0, key1:value1, key2:value2}
dictionary[key1] = value3
dictionary[key4] = value4
```

```
{key0:value0, key1:value3, key2:value2, key4:value4}
```

Operations for a dictionary is same as other iterable objects but have slight difference:

| OPERATOR | NAME                     | DESCRIPTION                                                  |
| -------- | ------------------------ | ------------------------------------------------------------ |
| `in`     | Included (key exclusive) | Check if the key is in a dictionary. However, it does not check the value. |

```python
dictionary = {key0:value0, key1:value1}

print( key0 in dictionary )			# >> OUTPUT: True
print( value1 in dictionary )		# >> OUTPUT: False
print( key3 not in dictionary )		# >> OUTPUT: True
```

Dictionary can have its own functions and methods to execute certain features of dictionary:

| OPERATION | EXAMPLE                             | DESCRIPTION                                                  |
| --------- | ----------------------------------- | ------------------------------------------------------------ |
| `get()`   | `dictionary.get(key,[description])` | Find the key and get its value; additional description can be added when the key is not found (`None` by default). |
| `dict()`  | `name=dict()`                       | Can create empty dictionary.                                 |

```python
dictionary = {key0:value0, key1:value1}

print( dictionary.get(key0) )						# >> OUTPUT: value0
print( dictionary.get(key2) )						# >> OUTPUT: None
print( dictionary.get(key3, "not in dictionary") )	# >> OUTPUT: not in dictionary
```

## Set

Set is an iterable object that guarantees uniqueness, meaning it does not allow duplicate data to exist within the object. Just like dictionary, set uses curly bracket `{}` to assign values but without key-value pair. Due to the reasons above, set is much faster to check the data than a list.

```python
set0 = {data0, data1, data2, data1}
print(set0)
```

```
{data0, data1, data2}
```

Set have mathematical operations which works exactly like mathematical set.

| OPERATION | NAME                 | DESCRIPTION                                                  |
| --------- | -------------------- | ------------------------------------------------------------ |
| `|`       | Union                | Returns the combined of two sets.                            |
| `&`       | Intersection         | Returns data which only exist in both sets.                  |
| `-`       | Difference           | Returns data which only exist in subtrahend and not in minuend. |
| `^`       | Symmetric difference | Return data exclusive to each set, but not both.             |

```python
set0 = {1, 2, 3, 4, 5, 6}
set1 = {4, 5, 6, 7, 8, 9}

print(set0 | set1)
# >> OUTPUT: {1, 2, 3, 4, 5, 6, 7, 8, 9}

print(set0 & set1)
# >> OUTPUT: {4, 5, 6}

print(set0 - set1)
print(set1 - set0) 
# >> OUTPUT: {1, 2, 3}
# >> OUTPUT: {7, 8, 9}

print(set0 ^ set1)
# >> OUTPUT: {1, 2, 3, 7, 8, 9}
```

Set can have its own functions and methods to execute certain features of set.

| FUNCTION | EXAMPLE         | DESCRIPTION                                                  |
| -------- | --------------- | ------------------------------------------------------------ |
| `set()`  | `set(iterable)` | Function which creates set: list and tuple should be with bracket `[]` and parentheses `()`. Dictionary is not included in this case. |

The function above is necessary when creating an empty set, as `{}` creates an empty dictionary instead. Meanwhile, the methods used by set object are as follows:

| METHOD     | EXAMPLE            | DESCRIPTION                                                  |
| ---------- | ------------------ | ------------------------------------------------------------ |
| `add()`    | `set.add(data)`    | Add `data` at the end of the set.                            |
| `remove()` | `set.remove(data)` | Remove `data` in the set.                                    |
| `pop()`    | `set.pop([key1])`  | Randomly selected element [or `key1` ] is popped or removed from the set. |

```python
set0 = set( [data0, data1, data2, data1] )
print( set0 )			# >> OUTPUT: {data0, data1, data2}

set0.add( data3 )
set0.remove( data0 )
print( set0 )			# >> OUTPUT: {data1, data2, data3}

print( set0.pop() )		# >> OUTPUT: data1 (randomly popped)
print( set0 )			# >> OUTPUT: {data0, data2}
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