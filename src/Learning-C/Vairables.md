# Variables in C Programming

A variable in C is a type of container that can hold a particular type of value, and its type is defined by its data type.


For example: `int x;`

Here, x is a variable of integer type, so it can hold only one integer value at a time.

Memory is allocated for a variable when it is defined, and the size of the allocation depends on the compiler. Generally, 2 bytes are allocated for an integer variable. The value that was present in those 2 bytes before assigning a value to the variable is known as a garbage value.

In C, when you assign a value to a variable, you are actually copying the value to the memory location that the variable represents.

~~~admonish
When you assign a value to a variable, you are essentially giving that value a name. So, when you write a = b;, you are saying "give the value that b refers to the name a".
```C
int a = 1;
int b = 2;
a = b; // This doesn't mean b is assigned to a.
```
~~~

Variables in C are memory locations that hold values. When you assign a value to a variable in C, you are actually copying the value to the memory location that the variable represents.

#### Basic terms related to variables

1. Definition
   - Allocates memory for a variable
   - For example, in `int x;` 2 bytes are allocated for x.

2. Declaration
   - Means providing information to the compiler about the data type of the variable. 
   - For example, in `int x;`, the information is given to the compiler that the data type of x is int.


3. Initialization
   - Assigns an initial value to a variable at the time of declaration.
   - `data_type variable_name = value;`
   - For example, `int x = 1;`
   - Note:
     - Static initialization happens at compile time.
     - Dynamic initialization happens at runtime.

### Define and Declare

| Define | Declare | Possible     |
| ------ | ------- | ------------ |
| - [x]  | - [x]   | Obviously    |
| - [ ]  | - [x]   | Possible     |
| - [x]  | - [ ]   | Not possible |
| - [ ]  | - [ ]   | Very nice    |

### Sign bit and range

- The first bit is known as the sign bit. It’s the most significant bit.
- 0 represents a positive value, and 1 represents a negative value.
- Range is determined by $2^{slots}-1$ 

C is an expanding language where byte allocation depends on the compiler. While bytes are cheap for us, C prioritizes accuracy and range at the cost of efficiency and memory.
