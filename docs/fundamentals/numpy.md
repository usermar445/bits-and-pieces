# Cheatsheet Numpy

## Python functions

To create integer sequences, use `range()`, eg:
```
range(0,10)
```
Two signatures are possible `range(stop)` or `range(start, stop, step=1)`. It is always **including** *start* and
**exlcluding** *stop*.
See [documentation](https://docs.python.org/3/library/functions.html#func-range).


## Numpy functions
### Creating arrays
Create a length-10 integer array filled with zeros:
```
np.zeros(10, dtype=int)
```
Create a 3x5 floating-point array filled with ones:
```
np.ones((3,5), dtype=float)
```
Create a 3x5 array filled with 3.14:
```
np.full((3, 5), 3.14)
```
Create an array filled with a linear sequence. 
Starting at 0, ending at 20, stepping by 2. 
(this is similar to the built-in range() function). **including start, excluding stop**:
```
np.arange(0, 20, 2)
```
Create an array of five values evenly spaced between 0 and 1:
```
np.linspace(0, 1, 5)
```
Create a 3x3 array of uniformly distributed random values between 0 and 1:
```
np.random.random((3, 3))
```
Create a 3x3 array of normally distributed random values with mean 0 and standard deviation 1:
```
np.random.normal(0, 1, (3, 3))
```
Create a 3x3 array of random integers in the interval [0, 10):
```
np.random.randint(0, 10, (3, 3))
```
Create a 3x3 identity matrix:
```
np.eye(3)
```
Create an uninitialized array of three integers. The values will be whatever happens to already exist at that memory:
```
np.empty(3)
```

### Array attributes
Number of dimensions:
```
ndarray.ndim
```
Shape (size of each dimension):
```
ndarray.shape
```
Size (total size of array, i.d. number of elements):
```
ndarray.size
```

### Indexing
**Single dimension array**
```
a[2]
```
or use negative indexes:
```
a[-2]
```
**Multi-dimensional arrays**
The logic is always:
```
x[row, column]
```
Example:
```
a[2, 0]
```
Assigning values, e.g. `x[2,0]=3` modify the original array. Assigning other numerical types get truncated to 
the `dtype` of the array.

### Slicing
```
x[start:stop:step]
```
**Attention:** Slicing does refer not to the index but the number of element (?).


**One-dimensional array**
First five elements (including index):
```
x[:5]
```
Elements after index 5:
```
x[5:]
```
Every other element:
```
x[::2]
```
Every other element starting at index 1:
```
x[1::2] 
```
Negative `step`, reverses the array (**swaps start and stop**)! E.g. all elements, reversed:
```
x[::-1]
```
Reversed every other from index 5:
```
x[5::-2] 
```

**Multi-dimensional array**:
Two rows, three columns:
```
x2[:2, :3]
```
All rows, every other column:
```
x2[:3, ::2]
```
Reversed dimension together:
```
x2[::-1, ::-1]
```

**Accessing rows and columns:**
First column:
```
x2[:, 0]
```
First row:
```
x2[0, :]
x2[0]
```
Are equivalent but only for rows.

### Copying
**Attentions**: Subarrays are no-copy views, id. that even when a subarray is "copied" and then modified, the **original**
array is modified. To copy an array use `copy()`.


### Reshaping
```
np.arange(1, 10).reshape((3, 3))
```

### Concatenation
```
x = np.array([1, 2, 3])
y = np.array([3, 2, 1])
np.concatenate([x, y])
```

For arrays of different dimensions, it is better to use `np.vstack()` or `np.hstack()`.

### Splitting

Use `np.split()`, `np.hsplit()` or `np.vsplit()`. Example:
```
```

### UFunctions
See book.

### Aggregation
**Attention: Aggegation of multi-dimentional arrays**:
```
x.min(axis=0)
```
Returns the minimium *along the columns*. The axis keyword specifies the dimension of the *array that will be collapsed*,
rather than the dimension that will be returned. So specifying `axis=0` means that the first axis will be collapsed: 
for two-dimensional arrays, this means that values within each column will be aggregated.

### Broadcasting
(from the book)

Broadcasting in NumPy follows a strict set of rules to determine the interaction between the two arrays:

- Rule 1: If the two arrays differ in their number of dimensions, the shape of the one with fewer dimensions is padded with ones on its leading (left) side. 
- Rule 2: If the shape of the two arrays does not match in any dimension, the array with shape equal to 1 in that dimension is stretched to match the other shape. 
- Rule 3: If in any dimension the sizes disagree and neither is equal to 1, an error is raised.

### (Boolean) Masks
(see book)

### Fancy indexing

### Sorting

