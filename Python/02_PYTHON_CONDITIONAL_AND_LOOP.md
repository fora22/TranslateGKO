# **PYTHON: CONDITIONAL AND LOOP**

Line-by-line sequential code execution programming is also known as *procedural programming*. It is the basic programming style using mostly with conditional and loops statements and additional functions for assistance.

This chapter introduce list of conditional and loop statements essential in Python programming.

## Indentation
Indentation is used to delimit (mark the limits or boundaries) blocks of code. Simply put, it is used to distinguish where the block of code belongs to. Indentation is inserted on the section of code after colon `:`.

Beware as placement of indentation can change the script entirely.

```python
# IDENTATION ON THE SECOND PRINT. 
if 1 < 0:
	print("Condition is False.") 
	print("End of IF statement.")
print("The End.") 

# NO INDENTATION ON THE SECOND PRINT.
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

## `if` Statement

Conditional `if` statement runs code if the condition is true. When the condition evaluates `True`, the statements are carried out but otherwise ignored.

```python
if condition:
	statements
```

### `else` Statement

Conditional `else` statement must be followed after `if` statement as it cannot be used alone. The statement contains code that is called when the condition evaluates `False`. The `else` statement is not indented along with `if` statement.

```python
if condition:
	statements
else:
	statements
```
Chaining `if` and `else` statement is possible in series of conditioning as follows:

```python
if condition: 
	statements
else:
	if condition:
		statements
	else condition:
		statements
```

### `elif` Statement

Conditional `elif` statement is a combination of `if` and `else` statement; when the first condition evaluates `false`, the `elif` statement provides second (or more) chance to evaluate condition different from the first one. 

```python
if condition: 
	statements
elif condition:
	statments:
else:
	statements
```

However, this is not the same as chain of `else`-`if` conditional statement as that is a combination of two different conditional set, while `elif` statement guarantees a single conditional set.

### Ternary Operator

Conditional statement can be expressed simply using ternary operator as shown below:

```python
var = True_return if condition else False_return
```

The vocabulary *ternary* represents the statement takes three arguments. Ternary operator should not be overused as it reduces readability, but useful on variable assignment.

## `while` Loop

The `while` loop statement repeatedly execute statements inside (aka. iterate) as long as the condition holds. The loop ends once the condition evaluates `False`.

```python
while condition:
	statements
```
The `else` statement may follow after a `while` loop statement, which will be executed when the loop statement has successfully finished its iteration (by conditional mean).

```python
# FINISHED LOOP: completed iteration
while index < 10:
	index += 1
	if index == 999:
		break
	else:
		print("First...successful!")

# FINISHED LOOP: forece-escaped via break statement
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

### `break` Statement

The `break` statement can be used to end a loop prematurely, before complete iteration is made. When encountered inside a loop, immediately escapes from the loop but does not break from its outer loop.

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

### `continue` Statement

The `continue` statement skips the rest of the statement below in the loop and jumps back to the conditioning part. This maintains the loop iteration rather than escaping the loop like `break` statement.

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


## `for` Loop

The `for` loop statements repeatedly execute statements inside (aka. iterate) as long as it is in the valid range. The loop ends once the range object is out of range integer.

```python
for index in iterable:
	statements
```

Here, a local variable `index` obtains integer from `iterable` iterable object and execute statements one-by-one until running all the values inside the object. The `iterable` doesn’t have to be an iterable object: string object can also work, which returns character comprising the string object instead.

```python
for var in range(3, 9, 2):
	print("Hello World" , var)
```

```
Hello World 3
Hello World 5
Hello World 7
```

Just like the `while` loop statement, `break` and `continue` can be used in `for` loop as well since it is the same loop-iterating statement.

The `else` statement may follow after a `for` loop statement, which will be executed when the loop statement has successfully finished its iteration (by running out of range).

```python
# FINISHED LOOP: completed iteration
for index in range(10):
	if index == 999:
		break
	else:
		print("First...successful!")

# FINISHED LOOP: forece-escaped via break statement
while index in range(10):
	if index == 5:
		break
	else:
		print("Second...successful!")
```

```
First...successful!
```

### **`range()` Function**

A function that creates a sequential list of integers, called "range" object.

| FUNCTION  | EXAMPLE                             | DESCRIPTION                                                  |
| --------- | ----------------------------------- | ------------------------------------------------------------ |
| `range()` | `range(start_num, length,interval)` | Creates a range object that has `legnth` number of sequence of integer starting from 0.<br /><br />OPTIONAL: Sequence starts from `start_num` number (not an index) with `interval`. For easier understanding, refer to the sample code below. |
| `list()`  | `list(rng)`                         | Convert range object `rng` to list.                          |

```python
print(range(10)) 

print(list(range(10)))

print(list(range(4,10)))

print(list(range(4,10,2)))
```

```
range(0,10)            # Range object (one of a types of iterable object)
[0,1,2,3,4,5,6,7,8,9]
[4,5,6,7,8,9]
[4,6,8]
```

A yet explained `for` loop statement executes code while in valid range, and `range()` function creates a range object that can provide a valid range of iteration.

```python
for var in range(3, 9, 2):
	print("Hello World" , var)
```

```
Hello World 3
Hello World 5
Hello World 7
```

## Exception

Exception is an error-exclusive conditional statement: the statement checks whether something goes wrong due to incorrect coding or input, stopping the program immediately. There are some statements that can be used to handle the script errors as follows.

### `try`/`except` Statement

The `try`/`except` statement is used to handle exceptions, and to call certain statements when an exception occurred. There are additional statements that can be used together with the pair:

| KEYWORD   | DESCRIPTION                                                  |
| --------- | ------------------------------------------------------------ |
| `try`     | A block of code to be checked for exception.                 |
| `except`  | A code to be executed when certain exception occurs.         |
| `else`    | [OPTIONAL: A code to be executed when the code has passed with no error (exception) occurred.] |
| `finally` | [OPTIONAL: A block of code executed no matter what exception has occurred, and even when there’s no error.] |

```python
try:
	statements
except exception_type_1:
	statements
except exception_type_2:
	statements
except:			# UNCONDITIONAL EXCEPTION LOCATES LAST.
	statements
finally:
	statements
```

Even after `try`/`except` statement is executed, the program does not stop and continues onward.

### `raise` Statement

The `raise` statement is used to raise exception intentionally, but manually. As the statement raises error, it also stops the runtime immediately, preventing anymore further execution thereafter.

```python
# EXPLICITLY RAISE EXCEPTION: can be used alone, even inside an 'except' code above.
raise

# PROVIDE DETAIL DESCRIPTION ON EXPLICITLY RAISED EXCEPTION
raise exception_description
```

### `assert` Statement

The `assert` statement checks expressions of code for validity (aka. assertion). When tested expression is valid with no problem, assertion returns `True`. When assertion returns `False`, an exception is raised.

```python
Print(0)
assert TRUE_expression
Print(1)
assert FALSE_expression,"exception_type"
Print(2)
```

```
0
1
AssertionError: exception_type
```

## `pass` Statement

The `pass` statement is a null operation that does nothing when executed. This comes useful by inserting it where the code will be placed but hasn’t been written yet.