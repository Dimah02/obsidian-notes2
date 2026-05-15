
# Multidimensional Array 

```python
import numpy as np

array = np.array([1,2,3,4])

array = array * 2

print(array)

print(type(array))



# Zero dimentional Array 
array = np.array('A')

print(array)
# number of dimentions
print(array.ndim)

# One dim array

array = np.array(["a","b","c"])

print(array)
print(array.ndim)

# Two dim array
array = np.array([
	[1,2,3],
	[3,4,5],
	[5,6,7]
	])

print(array)
print(array.ndim)
print(array.shape)


# Three dim array
array = np.array([
	[[1,2,3],[3,4,5],[5,6,7]],
	[[11,22,33],[33,44,55],[55,66,77]],
	[[13,23,33],[33,43,53],[53,63,73]]
	])

print(array)
print(array.ndim)
print(array.shape)
print(array[0][0][0])

#multidimintion indexing 
#access elements same as above 
print(array[0,0,2])
print(array[2,2,2])

```


# Slicing 


```python
import numpy as np

array = np.array([
	[1,2,3,4],
	[5,6,7,8],
	[9,10,11,12],
	[13,14,15,16]
	])

#              (excelusive)
# array[start:end:step]

# first row
print(array[0])

# last row
print(array[-1])

# range first three 0 1 2 (3 is execlusive)
print(array[0:3])

# range from second row to last
print(array[1:4])

# even rows
print(array[0:4:2]) # you can ommit start and end when selecting all rows array[::2]

# reverse order
print(array[::-1])

# every second row revesed
print(array[::-2])


# Select all rows and access column zero
print(array[:,0])

# Select all rows and return last column
print(array[:,-1])


# Select all row but with three columns 
print(array[:, 0:3])

# Skip first column and print all other 
print(array[:, 1:4])

# every second column
print(array[:, 0::2])

# revese all columns 
print(array[:, ::-1])

# first two rows with first two columns , first quarter
print(array[0:2 , 0:2])

# second quarter
#            rows , columns
print(array[ 0:2 , 2: ])


# last two rows with first tow columns
print(array[2:, 0:2])

# last tow rows with the last two columns
print(array[2:, 2:])

# middle 2 * 2 square
print(array[1:3, 1:3])

```


# Arithmetic
## Scalar

```python
import numpy as np

# Scalar (linear algebra term and it mean a single value) arithmetic 

array = np.array([1,2,3])

# each value will have one added to it
print(array + 1)


print(array - 2)


print(array * 3)

print(array / 4)


print(array ** 5)

```

## Vectorized function
```python
# Vectorized math func (vector is a single dimention)
# we can apply a function to en entire array without writing a loop

# if I want to apply sqtr function to each number I can use a built in function in the library
print(np.sqrt(array))

array = np.array([1.01, 2.5, 3.99])

print(np.round(array))

print(np.floor(array))

print(np.ceil(array))

print(np.pi)

radii = np.array([1,2,3])

radii = radii ** 2  * np.pi

print(radii)
```

## Element-wise arithmetic

```python 
# Element-wise arithmetic

array1 = np.array([1,2,3])
array2 = np.array([4,5,6])

# we can apply operation between single lements between arrays

print(array1 + array2)

print(array1 - array2)

print(array1 * array2)

print(array1 / array2)

print(array1 ** array2)

# Comparison operators
# we can create boolean arrays and filtir data 

scores = np.array([91,55,100,73,82,64])

print(scores == 100)
# [False False  True False False False]

print(scores >= 60)

print(scores< 60)

# Selecting all elements in the array with score less than 60 and asigning it to zero
scores[scores < 60] = 0

print(scores)
#[ 91   0 100  73  82  64]
```






# Broadcasting
```python
import numpy as np

# Brodcasting allows NumPy to perform operations on arrays
# with different shapes by virtually expanding dimensions
# so they match the larger array's shape.

# The dimensions have the same size.
# OR
# One of the dimensions has a size of 1.

# (1,4) and (4,1) can be brodcasted
# (4,4) and (4,1) can be brodcasted becuase first dimensions are equal and for the second dimention they aer not but one of them of size one
# (2,4) and (4,1) can not be brodcaseted becuase first dimention are not equal and non of them equal one

array1 = np.array([[1,2,3,4]])
array2 = np.array([[1],[2],[3],[4]])

print(array1.shape)
print(array2.shape)

print(array1*array2)
```
# Aggregate functions
```python
import numpy as np

# Aggregate function = summarize data and typically return a single value

array = np.array([[1,2,3,4,5],
				[6,7,8,9,10]])

print(np.sum(array))

print(np.mean(array))

print(np.std(array))

print(np.var(array))

print(np.min(array))

print(np.max(array))

# position on minimum value
print(np.argmin(array))

# postion to the maximum value
print(np.argmax(array))

# Sum all Columns
print(np.sum(array,axis = 0))

# Summ all rows
print(np.sum(array, axis = 1))
```
# Filtering
```python
import numpy as np

# Filtering = Refers to the process of selecting 
#             elements from an array that match a given condition

ages = np.array([[21,17,19,20,16,30,18,65],
				 [39,22,15,99,18,19,20,21]])

# Boolean indexnig
tennagers = ages[ages < 18]

print(tennagers)

adults = ages[(ages>=18) & (ages <65)]

print(adults)

seniors = ages[ages >= 65]

print(seniors)

evens = ages[ages%2==0]

odds = ages[ages%2!=0]

print(evens)
print(odds)

# When filtering and creating a new array but you want to preserve the orignal shap use Where function
#                                 defualt value for false element that does not match the condition
adults = np.where(ages>=18 , ages,0)
print(adults)
```
# Random numbers

```python
import numpy as np

# random number generator
# Setting a seed will guarentee to produce the same results
# If seed was not set numpy will create one for you np.random.default_rng()
rng = np.random.default_rng(seed = 1)

# Random number between 1 and 6
print(rng.integers(low = 1,high = 7))

# 3 Random numbers (one dimentional array)
print(rng.integers(low = 1,high = 101, size = 3))

# 3 Random number in 2d array 3 rows and 2 columns
print(rng.integers(low = 1,high = 101, size = (3,2)))

# Floating points numbers
# to set the seed
np.random.seed(seed=1)
print(np.random.uniform())
print(np.random.uniform(low = -1,high = 1))
print(np.random.uniform(low = -1,high = 1,size=3))

# Shuffel an array
array = np.array([1,2,3,4,5])

rng = np.random.default_rng()
rng.shuffle(array)
print(array)

# Random choise
fruits = np.array(["apple","orange","banana","pineaaple"])

fruit = rng.choice(fruits)

print(fruit)

# two random choices
fruits = rng.choice(fruits, size=2)
print(fruits)
```