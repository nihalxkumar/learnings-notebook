# User Defined Datatypes

They provide a way to encapsulate different types of data under a single name, enhancing code readability, maintainability, and organization. 

In C, user-defined datatypes primarily include structures, typedef, unions, and enumerations.

## Structures

A structure is a composite data type that allows you to group variables of different types under a single name. It enables you to create a new datatype to suit your specific needs.

#### Syntax:

```c
struct structure_name {
    data_type member1;
    data_type member2;
    // Additional members...
} structure_variable1, structure_variable2, ...;
```

#### Example:

```C
struct student {
    int roll_no;
    char name[50];
    float marks;
} s1, s2;
```

#### Accessing Structure Members:

```C
s1.roll_no = 1;
strcpy(s1.name, "John");
s1.marks = 85.5;
```

> Arrays and pointers can also be members of a structure, enabling you to store collections or references within a structure.

## Typedef

The typedef keyword allows you to create aliases for existing data types, making your code more readable and portable.

```C
typedef existing_data_type new_data_type;
```
#### Example:

```C
typedef struct student {
    int roll_no;
    char name[50];
    float marks;
} Student;

Student s1, s2;
```

## Unions

Similar to a structure, but it allows storing different data types in the same memory location. The memory allocated is equal to the size of the largest member.

#### Syntax: 

```C
union union_name {
    data_type member1;
    data_type member2;
    // Additional members...
} union_variable;
```

Unions are particularly useful in scenarios where you need to conserve memory, such as in embedded systems programming.

## Enumerations

Enumerations provide a way to define sets of named integer constants. It makes the code more readable and maintainable by assigning meaningful names to numeric values.

#### Syntax:

```C 
enum enum_name {
    value1,
    value2,
    // Additional values...
} enumeration_variable;
```

#### Example:

```C
enum Days {
    SUNDAY,
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY
} day;

day = MONDAY;
```

Enumerations are commonly used to represent a set of related named constants, such as days of the week or error codes.

## Bit-Fields

Bit-fields allow you to specify the size of individual members within a structure in terms of the number of bits they occupy, rather than full bytes. This feature is particularly useful when working with memory-constrained systems or when dealing with hardware-level programming where specific bits in a register need to be accessed or manipulated.

#### Syntax:

```C
struct {
    type [member_name] : width;
};
```

#### Example:

```C
struct {
    unsigned int flag1 : 1;
    unsigned int flag2 : 1;
    unsigned int bits : 4;
} status;
```

#### Accessing Bit-Fields:

```C
status.flag1 = 1; // Setting flag1
status.bits = 0xA; // Setting bits to 1010
```

Bit-fields allow for more efficient usage of memory by packing multiple variables into a single byte or word. However, they come with some limitations, such as platform-dependency and potential compiler optimizations.
