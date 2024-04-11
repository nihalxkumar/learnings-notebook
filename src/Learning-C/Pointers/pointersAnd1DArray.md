# Pointers and 1D Array

```C
int a;
int x[5];

a = 5;
x = 5; // Error

// Name of array is a constant pointer to 1st element of array. 

printf("%u",x);
printf("%d",*x);
printf("%d",*x+1);
printf("%d",*(x+1));
```

```
2000000
2000004
5
6
0
```

1. `printf("%u\n", x);` - This statement would print the memory address of the array x. The %u format specifier is used to print an unsigned integer, which is the format of memory addresses.

2. `printf("%d\n", x+1);` - This statement would print the memory address of the second element of the array x. The x array is implicitly converted to a pointer to its first element, and adding 1 to that pointer advances it to the next element.

3. `printf("%d\n", *x);` - This statement would print the value of the first element of the array x. The * operator is used to dereference the pointer to the first element, which retrieves the value stored at that memory location.

4. `printf("%d\n", *x+1);` - This statement would print the value of the first element of the array x plus 1. The *x expression retrieves the value stored at the memory location pointed to by x, and the +1 expression increments that value by 1.

5. `printf("%d\n", *(x+1));` - This statement would print the value of the second element of the array x. The x array is implicitly converted to a pointer to its first element, and adding 1 to that pointer advances it to the next element. The * operator is then used to dereference the pointer to the second element, which retrieves the value stored at that memory location.


```admonish danger title = "Not Allowed"
x++; or ++x;

x--; or --x;
```

~~~admonish success title = "Equivalents"
```C
x[0] = *x = *(x+0)

x[1] = *(x+1) = *x+1

x[1] = 1[x] = *(1+x)
```
~~~

```c
#include <stdio.h>

int main() {
    int x[5] = {1, 3, 6, 9, 4};
    printf("%d\n", *x);
    printf("%d\n", *(x + 1));
    printf("%d\n", *x + 1);
    printf("%d\n", *(x + 1)+2;
    printf("%p\n", x);
    printf("%p\n", &x);
    printf("%p\n", x + 1);
    printf("%p\n", &x + 1);
    printf("%d\n", *x++);
    printf("%d\n", (*x)++);
    printf("%d\n", ++*x);
    printf("%d\n", *++x);

    return 0;
}
```

```
1
3
2
5
0x7ffee1234560
0x7ffee1234560
0x7ffee1234564
0x7ffee1234580
Error
1 
3
Error
```

1. `printf("%d\n", *x);`
   
   - prints the value stored at the address pointed to by `x`. Since `x` is an array, `*x` refers to the first element of the array, which is 1.

2. `printf("%d\n", *(x + 1));`
   
   - Prints the value stored at the address `x + 1`, which is the second element of the array, which is 3. The expression `x + 1` is a pointer arithmetic operation that moves the pointer to the next element of the array.

3. `printf("%d\n", *x + 1);` 
   
   - prints the sum of the first element of the array (1) and 1, resulting in 2.

4. `printf("%d\n", *(x + 1)+2);`
   
   - Prints the value of the second element of the array x (which is 3) plus 2, resulting in 5.

5. `printf("%p\n", x);`
   
   - Prints the address of the first element of the array, which is `0x7ffee1234560` (the actual address may vary).

6. `printf("%p\n", &x);`
   
   - Prints the address of the entire array, which is also `0x7ffee1234560`.

7. `printf("%p\n", x + 1);`
 
   - Prints the address of the second element of the array, which is `0x7ffee1234564`.

8.  `printf("%p\n", &x + 1);`
   
    - Prints the address of the memory location immediately after the array, which is `0x7ffee1234580`.

9.  `printf("%d\n", *x++);`

    - Error. The `x++` operation tries to increment the pointer `x`, but the result of `*x` is an rvalue, not an lvalue. The postfix increment operator `++` requires an lvalue as its operand, which can appear on the left side of an assignment, but the dereference operation `*x` produces an rvalue, which cannot be modified directly.

        ~~~admonish danger

        ```C
        *x++ != *(x++)
        ```
        ~~~

10. `printf("%d\n", (*x)++);`

    - First dereferences the pointer x to access the second element of the array, and then increments the value of that element. Prints 1 and increments the value as 2.

11. `printf("%d\n", ++*x);` 
    
    - First increments the value of the element (which is now 2), and then prints the new value 3.

12. `printf("%d\n", *++x);`

    - Not possible. Constant pointer.




