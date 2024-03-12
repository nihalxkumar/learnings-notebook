# Size of operator

It returns the size of its operand, which can be a data type, a variable, or an expression. The result of the sizeof
operator is of type size_t, which is an unsigned integer type defined in the <stddef.h> header file.

essential for writing portable and efficient code in C programming. It helps you avoid hardcoding sizes and ensures that
your code adapts to different environments and architectures. Additionally, it is useful for dynamically allocating
memory based on the size of data types.

```C
#include <stdio.h>

int main() {
    printf("Size of int: %zu bytes\n", sizeof(int)); // 4 bytes
    printf("Size of char: %zu bytes\n", sizeof(char)); // 1 byte
    printf("Size of float: %zu bytes\n", sizeof(float)); // 4 bytes
    printf("Size of double: %zu bytes\n", sizeof(double)); // 8 bytes

    return 0;
}
```
