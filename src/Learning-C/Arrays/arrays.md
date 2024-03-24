# Arrays

An array in C is a collection of elements of the same data type stored in contiguous memory locations. Each element in an array is accessed by its index. 

Arrays in C are static, meaning their size is fixed upon declaration and cannot be changed during runtime.

Arrays in C do not support heterogeneous data storage. As such, we cannot store different values of different datatypes in an array.

Elements can be inputted in both row major and column major but stored only in row major fashion.

### Importantce of Arrays

* Easier storage, access and data management
* Useful to perform matrix operations
* useful to implement other data structures

### Declaration

```C
datatype array_name[array_size];
```

For example:

```C
int x[100];
```

In this declaration, an array of 100 integers named x is created. The index x[0] refers to the first element, and x[99] refers to the last element.

The variable's value is called subscript.

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

or

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
#include <string.h>

int scores[100];
memset(scores, 0, 100*sizeof(int));
```

### Accessing Elements

Elements in an array are accessed using square brackets `[]` notation with the index of the element. Arrays in C are zero-indexed, meaning the index of the first element is 0, and the index of the last element is `array_size - 1`. 

For example, to access the first and last elements of an array `x`:

```C
int first_element = x[0];
int last_element = x[99];
```

### Arguements to Functions

- Ordinary variables are passed by value
  - Values of the arguments passed are copied into the
parameters of the function.
  - Any change made to function parameters is not reflected in the original arguments
- Arrays are passed by reference
  - Changes made to the array passed in the called function are retained in the calling function

## Array Bounds Checking in C

In C, array bounds checking is performed only while writing to arrays, not while reading from them. This design choice prioritizes speed but requires programmers to be cautious about inadvertently accessing invalid memory locations.

---

#### A program which inputs positive integers and converts them into binary using arrays

```C
int n, i, j;
int x[16];
printf("Enter a positive integer: ");
scanf("%d", &n);

while(n!=0){
    x[i] = n%2;
    n = n/2;
    i++;
}
printf("Binary: ");

for(j=i-1; j>=0; j--){
    printf("%d", binary[j]);
}
```

doing the same without using arrays

```C
// using pow function 
#include <math.h>
int n, i=0, x, s=0
printf("Enter a positive integer: ");
scanf("%d", &n);

while(n!=0){
    x = n%2;
    n = n/2;
    s = s + pow(10, i)*x;
    i++;
}
printf("Binary: %d", s);
```

> #### Wrong Syntax
> float benchmarks[];
> 
> benchmarks = {2.35, 42.30, 60.03, 400.5, 0.001};
>
> The compiler has no clue how much space to reserve for our "benchmarks" array based on our first statement, and so even though we are providing all of that info in the very next line, compiler will demand that we provide the array size in the declaration line itself. Furthermore, arrays cannot be assigned values by listing them out using curly braces in any statement other than the declaration itself.
