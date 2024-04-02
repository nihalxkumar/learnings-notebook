# Pointers in C

pointers are variables that store memory addresses of another variable. They allow direct manipulation of memory, which is a powerful feature but also requires careful handling to avoid errors.

## Basic Pointer Syntax

- Declaring a pointer: `int *ptr;` declares a pointer named `ptr` that can point to an integer value.
  
- Dereferencing a pointer: `*ptr` refers to the value stored at the memory address pointed to by `ptr`.

## Understanding declarations

`int n;` to get an int just use n

`int n[3]` to get an int just use n[i]

`int foo(int n, float n1);` to get an int just call foo with related inputs.

`int *n;` to get an int just dereference n

### Void Pointers

- A pointer without an associated data type.
- Can point to any data type: int, float, char, long, structures, and more.
- Due to its generic nature, it cannot be dereferenced directly.

```C
int main(){
    generic  *ptr;
}
```

###### Distinguishing Between Void Pointers and Char Pointers

| Void Pointers                                                               | Character Pointers                                                    |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Truly generic. Can point to any data type                                   | Points to characters or bytes (given a byte is just an unsigned char) |
| Cannot be dereferenced directly since the data type it points to is unknown | Can be dereferenced directly                                          |
| Requires type casting before dereferencing                                  | Used for byte-level operations.                                       |


### Pass by Value and Pass by Reference

#### Pass by value

##### Advantages

1. Easy to understand
   - you just pass copies, nothing fancy to deference
2. Safe
   - Original data won't be modified by the called function

##### Disadvantages

3. Performance overhead
   - A big object like a struct to be copied it's really bad performance wise. Time consuming and memory intensive.
4. Short reach(Lack of direct acess)
   - Called functions can only modify local copies. (This can be a good thing too) k
Declarations tell us 'How to use'

#### Pass by reference

##### Advantages

1. Efficiency
   - You just pass an address, it can point to a gigantic structure, not a problem.
2. Direct access
   - can modify data outside the called function. This trick allows us to return multiple values from a function.

##### Disadvantages

1. Can be complex to understand
   - You have to dereference the pointer to get the value.

### Generic Data Handling and Memory Allocation

Type casting to VOID* is a way to pass any type of data to a function. aka generic. It's a way to pass data without knowing the type of data. "we'll let you know bro".

malloc is a function that allocates some memory in the heap. It redturns a void pointer doesn't care if you give the pointer a type. It's a way to allocate memory dynamically.

we can do `void * `arithmetic with a GNU extention. 

> GNU Extention refers to additional language features or behaviour provided by GCC that go beyond the standard C language.

GNU C provided an extention called Pointer Arithmetic on `void *` that allows performing arithmetic operations on `void *` pointers by treating them as byte pointers. This extention is by default enabled in GCC.

The pointer arithmetic is done is done in terms of the size of char(1 byte) rather than the size of the pointer type. 

### Quirks

#### Addition to a pointer

When you add an integer to a pointer, the pointer is incremented by the size of the data type it points to.

```C
#include <stdio.h>

int main()
{
    long array[3] = {1, 2, 3};
    long *p = array;
    printf("%ld\n", *(p + 1)); // prints 2, you can use p[..] or *(p + ..)
}
```

Addition to pointer is not valid in C as the sum of two memory addresses doesn't logically translate to any meaningful value in most contexts.

ation or division between pointers also doesn't make sense in C and will cause a compiler error.

#### Substraction to a pointer

Subtracting two pointers is valid in C, but only under certain circumstances. For instance:

- Subtracting two pointers gives you their difference in memory addresses.
- The result is then divided by the size of the pointer's data type.
- You can only subtract pointers of the same type

```C
#include <stdio.h>

int main() 
{
    long array[5] = {10, 20, 30, 40, 50};
    // Two pointers pointing to different positions in the array
    long *ptr_a = &array[1];  // Pointing to the value 20
    long *ptr_b = &array[3];  // Pointing to the value 40
    printf("Value at ptr_a: %ld\n", *ptr_a);  // Outputs: 20
    printf("Value at ptr_b: %ld\n", *ptr_b);  // Outputs: 40
    // Subtracting the pointers
    long difference = ptr_b - ptr_a;
    printf("Difference in positions: %ld\n", difference);  // Outputs: 2
    return 0;
}
```

Arrays decay into pointers, except when used with the `&` operator. Decaying allows for more efficient memory usage.

To keep it simple, Whenever you work with an array identifier, most likely you are working with an pointer to element 0.

`arr[1]` and `*(arr + 1)` are same

`arr[n]` == `*(arr + n)`

By decaying an array into a pointer, it allows for more efficient memory usage. When passing an array to a function, instead of creating a copy of the entire array, only the memory address of the first element is passed. This reduces the overhead of memory allocation and copying when dealing with large arrays.


## Function Pointers

Function pointers allow calling functions indirectly or taking their addresses.

The only 2 things we can do with a function is to either call it or take its address. 

So, if the name isn't followed by a `(`to signify a function call, then the name evaluates to the address of the function with no ambiguity.

```C
#include <stdio.h>

// Function prototypes
long long sum(int a, int b);
long long product(int a, int b);
// Define the function sum
long long sum(int a, int b)
{
    return a + b;
}
// Define the function product
long long product(int a, int b)
{
    return a * b;
}
int main()
{
    // Declare a function pointer called operation
    long long (*operation)(int, int);
    // Assign the address of the sum function to operation pointer
    operation = &sum;
    // Use the function pointer to invoke the sum function
    printf("Using function pointer: %lld\n", operation(5, 7)); // Outputs: 12
    // Just for demo, let's switch the function pointer to point to the product function
    operation = &product;
    printf("Using function pointer to multiply: %lld\n", operation(5, 7)); // Outputs: 35
    return 0;
}
```

Practical use case: 

1. Event Handlers: In UNIX-like operating systems, signal handlers often utilize function pointers.

2. Callbacks: After a task completes, you might want to execute a specific function. Callbacks, often implemented via function pointers, allow this.

## Double Pointers

- Double pointers are just pointers pointing to other pointers.

- They're useful when you need to modify pointer values within functions.

- Like pointers, they're a tool: powerful when used correctly, but they can be confusing. Practice helps solidify understanding.


#### Quirks

```C
char* str[20];
```

Is str a pointer to an array of 20 characters, or is it an array of 20 pointers to characters?

This declaration creates an array of 20 pointers to characters, not the other way around. Here's why:

The array notation ([]) applies more closely to the variable than the pointer notation (*).
In essence, we've defined 20 of whatever type precedes the array brackets.
To confirm this, you can print the size of the array.


## argv[] or **argv 

argv[] or **argv represent pointers to pointers in C.

```C
int main() {
   int *ptr;
   int *ptr1;
   int ***ptr2;
   int ****ptr3;
   int n = 42;

   ptr = &n;
   ptr1 = &ptr;
   ptr2 = &ptr2;
   ptr3 = &ptr3;

   return 0;
}
```

![alt text](image.png)

---

Resources to refer to:

- [Syntax Explained](https://cdecl.org/)
- [Syntax Visualized](https://www.dcode.fr/c-declaration-explained)
- [Binary representations of floating point formats](https://float.exposed)
- [Ocane's Article on pointers](https://medium.com/@jalal92/just-dereference-the-link-for-the-code-in-the-video-cdfc0c2d9547)
- 

