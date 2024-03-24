# Multidimensional Arrays

Multidimensional arrays are arrays of arrays. They are useful to implement other data structures, such as matrices.

### Declaration

```c
datatype array_name[number_of_rows][number_of_columns];
```

For example:

```c
int x[2][3];
```

In this declaration, a 2D array of 2 rows and 3 columns named x is created. The index x[0][0] refers to the first element, and x[1][2] refers to the last element.

## 2D Arrays

absctraction of 1D array. every element is an 1D array itself

`int x[3][4] = {{1,2,3,4},{5,6,7,8},{9,10,11,12}};`

it can also be said that we have defined 3 one dimensional arrays.

```
|  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10 | 11 | 12 |

|----0th element--------|------1st element------|----2nd element-----|
```

### Valid Unvalid Declarations

1. `int x[2][3] = {{1,2,3},{4,5,6}};` 

     - Valid

2. `int x[][3] = {{1,2,3},{4,5,6}};` 

     - Valid. 
     - This syntax is often used when the compiler can infer the first dimension from the number of initializers provided. In this case, since two inner arrays are provided, the compiler infers that the first dimension should be 2. Therefore, it's equivalent to the first declaration.

3. `int x[2][] = {{1,2,3},{4,5,6}};` 

      - Not Valid. 
      - In C, when you omit the size of one dimension, you must specify it for the outermost dimension.  compiler needs to know the size of each dimension in order to allocate memory properly. To understand why this is an issue, consider the initializer list {{1,2,3},{4,5,6}}. The compiler can infer that the first dimension of x should be 2 because there are two sets of curly braces. However, it cannot determine the size of the second dimension from the initializer list alone. In C/C++, arrays are stored contiguously in memory, so the compiler needs to know the size of each dimension to calculate the memory offsets correctly. When you omit the size of the second dimension, the compiler doesn't have enough information to calculate these offsets, resulting in a compilation error.


<!-- 4. `int x[][3] = {{1,2,3},{4,5,6}};`

   - Ask this doubt in class
   - LLMs sayins its valid. Amit sir saying no. -->


