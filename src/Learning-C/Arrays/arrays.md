# Arrays

An array in C is a collection of elements of the same data type stored in contiguous memory locations. Each element in an array is accessed by its index. Arrays in C are static, meaning their size is fixed upon declaration and cannot be changed during runtime.

Elements can be inputted in both row major and column major but stored only in row major fashion.

### Declaration

data_type array_name[array_size];

with `int x[100]` an array of 100 integers is created.

`int` is the data type of the array.

`x` is the name of the array.

`100` is the size or number of elements of the array.

x[0] is the first variable and x[99] is the last element.

The variable's value is called subscript. For x[0] and x[5] the subscript is 0 and 5 respectively.

All the variables are independent of each other. Changing one variable does not affect the other.



`x[100] = {0, 1}` is an array of 100 elements with the first 2 elements initialized to 0 and 1. The rest of the elements are initialized to 0.


### Initialization 

Arrays in C can be initialized during declaration or afterward using the following syntax:

```c
int x[3];
x[0] = 5;
x[1] = 3;
x[2] = 1;
```

```c
int x[3] = {5, 3, 1};
```

Dynamic initialization of arrays is also possible using loops. For example, to initialize all elements of an array scores to 0:

```C
int scores[100];
for (int i = 0; i < 100; i++) {
    scores[i] = 0;
}
```

Alternatively, the `memset` function from the `<string.h>` library can be used to set all elements of an array to a specific value, such as 0:

```C
// at the top of your source code
#include <string.h>

int scores[100];
memset(scores, 0, 100*sizeof(int));
```

### Accessing Elements

Elements in an array are accessed using square brackets `[]` notation with the index of the element. Arrays in C are zero-indexed, meaning the index of the first element is 0, and the index of the last element is `array_size - 1`. For example, to access the first and last elements of an array `x`: