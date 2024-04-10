# Pointers and 1D Array

```C
int a;
int x[5];

a = 5;
x = 5; // Error
```
Name of array is a constant pointer to 1st element of array. 

```admonish note title = "Not Allowed"
x++; or ++x;
x--; or --x;
```

`printf("%u\n", x);` - This statement would print the memory address of the array x. The %u format specifier is used to print an unsigned integer, which is the format of memory addresses.

`printf("%d\n", x+1);` - This statement would print the memory address of the second element of the array x. The x array is implicitly converted to a pointer to its first element, and adding 1 to that pointer advances it to the next element.

`printf("%d\n", *x);` - This statement would print the value of the first element of the array x. The * operator is used to dereference the pointer to the first element, which retrieves the value stored at that memory location.

`printf("%d\n", *x+1);` - This statement would print the value of the first element of the array x plus 1. The *x expression retrieves the value stored at the memory location pointed to by x, and the +1 expression increments that value by 1.

`printf("%d\n", *(x+1));` - This statement would print the value of the second element of the array x. The x array is implicitly converted to a pointer to its first element, and adding 1 to that pointer advances it to the next element. The * operator is then used to dereference the pointer to the second element, which retrieves the value stored at that memory location.

```
2000000
2000004
5
6
0
```

```admonish info
x[0] = *x = *(x+0)
x[1] = *(x+1) = *x+1
x[1] = 1[x] = *(1+x)
```

```c
#include <stdio.h>

int main() {
    int x[5] = {1, 3, 6, 9, 4};
    printf("%d\n", *x);
    printf("%d\n", *(x + 1));
    printf("%d\n", *x + 1);
    printf("%p\n", x);
    printf("%p\n", &x);
    printf("%p\n", x + 1);
    printf("%p\n", &x + 1);
    printf("%d\n", *x++);
    printf("%d\n", *x++);
    printf("%d\n", (*x)++);
    printf("%d\n", ++*x);
    printf("%d\n", *++x);

    return 0;
}

`printf("%d\n", *x);` - Prints the first element of the array, which is 1.
`printf("%d\n", *(x + 1));` - Prints the second element of the array, which is 3. The expression x + 1 is a pointer arithmetic operation that moves the pointer to the next element of the array.
`printf("%d\n", *x + 1);` - Prints the first element of the array (1) plus 1, which is 2.
`printf("%p\n", x);` - Prints the address of the first element of the array, which is 0x7ffee1234560 (the actual address may vary).
`printf("%p\n", &x);` - Prints the address of the entire array, which is also 0x7ffee1234560.
`printf("%p\n", x + 1);` - Prints the address of the second element of the array, which is 0x7ffee1234564.
`printf("%p\n", &x + 1);` - Prints the address of the element after the array, which is 0x7ffee1234580.
`printf("%d\n", *x++);` - Prints the first element (1), then increments the pointer to the second element.
`printf("%d\n", *x++);` - Prints the second element (3), then increments the pointer to the third element.
`printf("%d\n", (*x)++);` - Increments the value of the third element (6) by 1, then prints the new value (7).
`printf("%d\n", ++*x);` - Increments the value of the fourth element (9) by 1, then prints the new value (10).
`printf("%d\n", *++x);` - Increments the pointer to the fifth element, then prints the value of the fifth element (4).
