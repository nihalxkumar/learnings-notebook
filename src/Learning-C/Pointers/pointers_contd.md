# Pointers

Misc

### Distinguishing Between Void Pointers and Char Pointers

| Void Pointers                                                               | Character Pointers                                                    |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Truly generic. Can point to any data type                                   | Points to characters or bytes (given a byte is just an unsigned char) |
| Cannot be dereferenced directly since the data type it points to is unknown | Can be dereferenced directly                                          |
| Requires type casting before dereferencing                                  | Used for byte-level operations.                                       |


### Pass by Value and Pass by Reference

#### Pass by value

| Advantages                                                           | Disadvantages                                                                                                     |
| -------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Easy to understand - you can just pass copies, nothing to deference. | Performance overhead - A big object like a struct to be copied will be time and memory intensive.                 |
| Safe - Original data won't be modified by the called function        | Short reach(Lack of direct access) - Called functions can only modify local copies. This can be a good thing too. |

#### Pass by reference

| Advantages                                                                                                                   | Disadvantages                                                                        |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Efficiency  - You just pass an address, it can point to a gigantic structure, not a problem.                                 | Can be complex to understand - You have to dereference the pointer to get the value. |
| Direct access - can modify data outside the called function. This trick allows us to return multiple values from a function. |                                                                                      |

### Some Questions to revise concepts


Q. If float needs 4 bytes. `float **p` p++ will move the pointer by how many bytes?

Answer: 8 bytes

the pointer moves forward by the size of the data type it points to (4 bytes for a float), but since the pointer is incremented after the value is accessed, the pointer moves two memory locations forward (4 bytes for the float value and 4 bytes for the increment).

- In this case, p is a pointer to a pointer to a float.
- Each float takes up 4 bytes of memory.
- When you do p++, you are incrementing the pointer p to point to the next location in memory where a float pointer is stored.
- Since each float pointer takes up 4 bytes, incrementing p by 1 (using p++) will move the pointer to the next float pointer, which is 4 bytes away. This is why **p+2** will point to the memory location that is 8 bytes (2 * 4 bytes) away from the original p.

Q. `char **p;` p++ will move the pointer by how many bytes?

Answer: 1 byte

- In this case, p is a pointer to a pointer to a char.
- Each char takes up 1 byte of memory.
- When you do p++, you are incrementing the pointer p to point to the next location in memory where a char pointer is stored.
- Since each char pointer takes up 1 byte, incrementing p by 1 (using p++) will move the pointer to the next char pointer, which is 1 byte away. This is why **p+1** will point to the memory location that is 1 byte away from the original p.

Q. What will be the output of the following code snippet?
```C
int *p;
float x = 5.2;
p = &x;
printf("%d", *p);
```

Answer: Undefined behavior, garbage

- *p will attempt to interpret the bytes of the float x as an integer value.
- However, the size of a float (4 bytes) is different from the size of an int (also 4 bytes on most systems), and the bit patterns will be interpreted differently.
- This results in a completely different value being printed, which is usually some random garbage value that doesn't correspond to the original float value.
- For example, if x is 5.2, the bit pattern in memory might be something like 0x40a00000. When we try to print this as an int using %d, we'll get a completely different value, such as 1072693248, which is just garbage.

~~~admonish note
pointers have unary operators therfore associativity is right to left

```C
int *p;
int x = 5.2;
p = &x;
printf("%d", *(int*)p);
```

here if we had 

```C
printf("%f", (int*)*p);
```

It would result in a compilation error because of associativity rule.

Another case of associativity:

```C
printf("%u", (int*)p++);
```

This will result in an error because the compiler will try to add 1 to the pointer first and then typecast it to an integer pointer. To avoid this, we can use parentheses to enforce the correct order of operations:

```C
printf("%u", ((int*)p)++);
```

This will add 1 to the pointer p first and then typecast the result to an integer pointer.
~~~

Q. If P is a generic pointer then what does P+1 means?

```C
void *p;
int x;
p = &x;
printf("%u", p+1);
```
Answer: cannot increment value of void pointer unless, it is typecasted to a specific type.
For e.g. `printf("%u", (int*)p+1);`


Q. What will be the output of the following code snippet?
```C
int* p;
int x = 5;
p = &x;
printf("p: %p\n", p);
printf("p + 1: %p\n", p + 1);
printf("*p: %d\n", *p);
printf("*p + 1: %d\n", *p + 1);
printf("*(p+1): %d\n", *(p+1));
```

Answer: The output will have
memory address of x for p
memory address of x + 4 bytes for p + 1
value of x for *p which will be 5
value of x + 1 for *p + 1 which will be 6
garbage value for *(p+1) because it is not pointing to any valid memory location.


Q. How would you print the content of a memory location 2000?
Assume int takes 2 bytes and char takes 1 byte.

a) int *p = 2000;
   printf("%d", *p);

b) char *p1 = 2000;
    printf("%c", *p1);

c) both

d) none

Answer: b) char *p1 = 2000;
    printf("%c", *p1);

Explanation:
Option a) int *p = 2000; printf("%d", *p); is incorrect because it will result in contents of memory location 2000 and 2001 being printed as an integer.

Q. Imagine p is pointing to an integer. Which of the following expressions would print the contents of the location that p is pointing to and make p point to the next location in memory without modifying any data?

a) printf("%d", *p++);

b) printf("%d", (*p)++);

Answer. `(*p)++` increments the value that the pointer points to, while `*p++`increments the pointer itself to point to the next element.

a. `printf("%d", (*p)++);`
   1. This first dereferences the pointer p to get the value it points to.
   2. It then increments that value by 1 (post-increment).
   3. Finally, it prints the original value (before the increment) using the %d format specifier.
   4. So, this expression:
      - Accesses the value pointed to by p
      - Increments that value by 1
      - Prints the original, pre-incremented value

b. `printf("%d", *p++);`
 1. This first prints the value pointed to by p using the %d format specifier.
 2. It then increments the pointer p itself by the size of the type it points to (e.g. if p is a pointer to int, it would increment by 4 bytes).
 3. This first prints the value pointed to by p using the %d format specifier.
 4. It then increments the pointer p itself by the size of the type it points to (e.g. if p is a pointer to int, it would increment by 4 bytes).
 5. So, this expression:
    - Prints the value pointed to by p
    - Increments the pointer p to point to the next element in memory

> *(arr + 1) = arr[1]
> 
> int *a[5] mean “a” is an array of 5 integer pointers.

```c
#include <stdio.h>

int main() {
    int *ptr[3], i , iA[]={5,10,15}, iB[]={1,2,3}, iC[]={2,4,6};
    ptr[0]=iA; ptr[1]=iB; ptr[2]=iC;
    for(i=0; i<3 ; i++){
        printf("iA[%d]: address=%p data=%d", i, ptr[0]+i, *(ptr[0]+i));
        printf("iB[%d]: address=%p data=%d", i, ptr[0]+i, *(ptr[0]+i));
        printf("iC[%d]: address=%p data=%d", i, ptr[0]+i, *(ptr[0]+i));
    }

    return 0;
}
```
-----

Resources to refer to:

- [Syntax Explained](https://cdecl.org/)
- [Syntax Visualized](https://www.dcode.fr/c-declaration-explained)
- [Binary representations of floating point formats](https://float.exposed)
- [oceanO's Article on pointers](https://medium.com/@jalal92/just-dereference-the-link-for-the-code-in-the-video-cdfc0c2d9547)
