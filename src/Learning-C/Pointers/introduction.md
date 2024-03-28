# Pointers

pointers are variables that store memory addresses. They allow direct manipulation of memory, which is a powerful feature but also requires careful handling to avoid errors.

#### Basic Pointer Syntax

- Declaring a pointer: `int *ptr;` declares a pointer named `ptr` that can point to an integer value.
- Dereferencing a pointer: `*ptr` refers to the value stored at the memory address pointed to by `ptr`.

#### Understanding declarations

`int n;` to get an int just use n

`int n[3]` to get an int just use n[i]

`int foo(int n, float n1);` to get an int just call foo with related inputs.

`int *n;` to get an int just dereference n


### Pass by Value and Pass by Reference

#### Pass by value

##### Advantages

1. Easy to understand
   1. you just pass copies, nothing fancy to deference
2. Safe
   1. Original data won't be modified by the called function

##### Disadvantages

3. Performance overhead
   1. A big object like a struct to be copied it's really bad performance wise. Time consuming and memory intensive.
4. Short reach(Lack of direct acess)
   1. Called functions can only modify local copies. (This can be a good thing too) k
Declarations tell us 'How to use'

#### Pass by reference

##### Advantages

1. Efficiency
   1. You just pass an address, it can point to a gigantic structure, not a problem.
2. Direct access
   1. can modify data outside the called function. This trick allows us to return multiple values from a function.

##### Disadvantages

1. Can be complex to understand
    1. You have to dereference the pointer to get the value.


Type casting to VOID* is a way to pass any type of data to a function. aka generic. It's a way to pass data without knowing the type of data. "we'll let you know bro".

malloc is a function that allocates some memory in the heap. It returns a void pointer doesn't care if you give the pointer a type. It's a way to allocate memory dynamically.

we can do `void * `arithmetic with a GNU extention. 

> GNU Extention refers to additional language features or behaviour provided by GCC that go beyond the standard C language.

GNU C provided an extention called Pointer Arithmetic on `void *` that allows performing arithmetic operations on `void *` pointers by treating them as byte pointers. This extention is by default enabled in GCC.

The pointer arithmetic is done is done in terms of the size of char(1 byte) rather than the size of the pointer type. 


