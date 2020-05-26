# **PYTHON: FILE MANAGEMENT**

When using the Python in advanced scripting, such as use for scientific research and artificial intelligence, the input data that needs to be computed cannot be stored through console command of the Python and may need to read through files if necessary.

## Opening Files

Before reading or manipulating files via Python, the file must be opened firsthand. The `open()` function is used to open a file user want to open.

```python
open("filename.txt")
```

| OPTION | DESCRIPTION                        |
| ------ | ---------------------------------- |
| `r`    | Read mode (default)                |
| `w`    | Write mode (rewrites content)      |
| `a`    | Append mode (adding new content)   |
| `rb`   | Binary read mode (non-text files)  |
| `wb`   | Binary write mode (non-text files) |

The `close()` method is used to close currently opened files. Closing file in very important on avoiding wasting resource. Ensure the files are always closed even on exceptions by using try/except or with statement.

```python
file = open("file.txt", "r")
file.close()
```

### `with` Statement

The `with` statement creates temporary variable only available inside an indented code block of the `with` statement. When the file is opened using this statement, the file automatically closes at the end of the code block even if exceptions occur within it.

```python
with open("file.txt") as file:
    statements
```

### Context Manager

Context manager is an interface that allows support of `with` statement. There are two methods available for setting object method and function as context manager: (1) using `__enter__()` & `__exit__()` method pair and (2) using `contextlib` module.

```python
# CONTEXT MANAGER 1
class CLASS:
    def __init__(self):
        pass
    
    # EXECUTE UPON ENTERING "WITH"
    def __enter__(self):
        self.variable = expression
        return self.variable
    
    # EXECUTE UPON EXITING "WITH"
    def __exit__(self):
        statements
```

----

```python
from contextlib import contextmanager

# CONTEXT MANAGER 2 
class CLASS:
    def __init__(self):
        pass
    
    # "WITH" SUPPORTED FUNCTION/METHOD
    @contextmanager
    def method(self):
        self.variable = expression`
        yield self.variable
        statements
```

Context manager returns (or yields) attribute (or variable) when using `with` statement, which becomes a resource to be handled while within the statement. Having implicitly determined resource makes `as` keyword unnecessary, unless there is a need to alias the name.

```python
# INSTANTIATION
instance = CLASS()

with instance.method():
    # HANDLES "self.variable"
    statements
```

One of the actual implementation of this syntax can be found on chapter *TENSORFLOW: BASIC § TensorBoard* in [*PRGMING_TensorFlow*](./PRGMING_TensorFlow.md) document.

### Absolute & Relative Paths

Just as other programming languages are, Python have two different types of path: absolute and relative path. When designating a path, use double backslash `\\` as a single backslash is an escape character that can cause unwanted operation.

```python
variable = open("path\\file.txt")
```

## Reading Files

After opening the text-based file, Python can read lines of file's content using `read()` method. Argument inside the method represent the number of bytes the method will read.

Read method can be used on the same file over again, but it will continue from where Python last read. When there’s no argument, the read method reads the rest of the text from where it last left off.

```python
with open("path\\file.txt") as file:
    print(file.read(16))	# READ 16 BYTES FROM THE START OF THE CONTENT.
    print(file.read(4))		# READ 4 BYTES FROM THE POINT AFTER PREVIOUS 16 BYTES.
    print(file.read())		# READ THE REST OF THE TEXT AFTER PREVIOUS 4 BYTES.
    print(file.read())		# READ NO TEXT AS NO MORE CONTENT TO READ.
```

The `Readlines()` method is used to return a list of text of each line. The method do accepts argument, but it works exactly same as a read method: it designates how many bytes to read.

Don’t get confused with `Readline()`s method which only reads the first line in string.

```
<file.txt>
First line here.
Second line there.
Last line somewhere.
```

```python
with open("path\\file.txt") as file:
    print(file.readlines())
    print(file.readline())
```

```
['First line here.\n','Second line there.\n','Last line somewhere.']
First line here.
```

### Printing Line using Loop

Each line of text-base content can be retrieved using `for` loop statement:

```python
for file in variable:
    print(variable)
```

## Writing Files

In Python, file can be created or (over)written by the `write()` method of the text-based file object. There are two options user can choose when writing: overwrite and append.

Suppose there is a file with text content written as follows:

```
<file.txt>
First line here.
Second line there.
Last line somewhere.
```

Overwrite mode `w` deletes all of previously existing content and write down fresh from the beginning.

```python
with open("path\\file.txt", "w") as file:
    file.write("TEXT OVERWRITTEN!")
```

```
<file.txt>
TEXT OVERWRITTEN!
```

On the other hand, append mode `a` does not delete existing content but continue writing from the end.

```python
with open("path\\file.txt", "a") as file:
    file = file.write("TEXT APPENDED.")
    print(file)
```

```
<file.txt>
First line here.
Second line there.
Last line somewhere.TEXT APPENDED.
```

Upon successfully written, `write()` method returns the number of bytes written.

### Creating Files

New file can be created using the `write()` method which does not bound by just writing on existing file. Creating file is simply done by designating file name is doesn't exist on the specified path.

```python
with open("path\\new_file.txt", "w") as file:
    file.write("NEW FILE CREATED!")
```

```
<new_file.txt>
NEW FILE CREATED!
```