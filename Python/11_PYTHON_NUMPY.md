# **PYTHON: NUMPY**

NumPy is an extremely powerful and useful library used in Python which supports multi-dimensional matrix (aka. NumPy array). As one of the best known scientific libraries, it is implemented on other well-recognized libraries such as [Matplotlib](https://matplotlib.org/), [TensorFlow](https://www.tensorflow.org/), et cetera.

To install NumPy library, open command prompt window and enter the command below: 

```
python -m pip install numpy
```

Since NumPy is a huge scientific library and is still growing, this chapter will briefly introduce basic usage of the array. For more information on its API, refer to the following URL: https://numpy.org/

## NumPy Array

NumPy array is a very flexible matrix. Compared to Python's List iterable object, the array has better performance both advantageous in faster speed and efficient memory management.

Declaration of the NumPy array is be done as follows:

```python
import numpy as np

# NUMPY DECLARATION
variable = np.ndarray(shape = (2, 3))
print(variable)
```

```
[[800191312     32765 800196048]
 [    32765 870097920     32765]]
```

This creates NumPy array object based on the given size, but its value is randomly generated.

Initialization of the NumPy array is done as follows:

```python
import numpy as np

# NUMPY INITIALIZATION 
variable = np.array([[1, 2, 3], [4, 5, 6]])
print(variable)
```

```
[[1 2 3]
 [4 5 6]]
```

This creates NumPy array object based on the given value, but has disadvantage on creating the array with huge size or deeper dimension. 

More NumPy methods exist that is used to create the array with better convenience:

| NUMPY ARRAY             | DESCRIPTION                                                  |
| ----------------------- | ------------------------------------------------------------ |
| `np.zeros(shape)`       | Create a NumPy filled with number 0 with the size of `shape`. |
| `np.ones(shape)`        | Create a NumPy filled with number 1 with the size of `shape`. |
| `np.eye(N)`             | Create a NumPy identity matrix of `N` x `N` size.            |
| `np.full(shape, value)` | Create a NumPy filled with `value` with the size of `shape`. |

### NumPy Element

While accessing elements of NumPy array is similar to Python's iterable object, but its syntax is different:

```python
import numpy as np
variable = np.array([[1, 2, 3], [4, 5, 6]])

print(variable[0])		# >> OUTPUT: [1, 2, 3]
print(variable[0, 1])	# >> OUTPUT: 2
```

### NumPy Shape

Shape of the NumPy cannot be extracted using method of Python's iterable object such as `len()`. Instead, NumPy has its own attribute containing length of each dimension.

```python
import numpy as np
variable = np.array([[1, 2, 3], [4, 5, 6]])

variable.shape		# >> OUTPUT: (2, 3)
variable.shape[0]	# >> OUTPUT: 2
```

## NumPy Indexing

The term "indexing" means slicing the array to specific range only. Each dimension is indexed using colon `:` and are distinguished via comma `,`. Indexing shares the same rules as slicing of iterable object.

* `n:m` : start indexing from n^th^ element (included) to m^th^ element (excluded)
* `:` : start indexing from beginning to the end, thus skip indexing.

```python
import numpy as np
variable = np.array([[1, 2, 3], [4, 5, 6]])

print(variable[:, 1:-1])
```

```
[[1 2]
 [4 5]]
```