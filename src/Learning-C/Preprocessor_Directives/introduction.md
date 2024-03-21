# Preprocessor Directives

Manipulating source code before it undergoes compilation. These directives serve to modify or augment the source code in various ways, facilitating efficient development and customization of programs. 

`.c` -> `preprocessor` -> pure high level `c` -> `compiler` -> `assembly machine code`

## File Inclusion

One of the fundamental tasks of the preprocessor is to include header files into the source code using the #include directive. This directive allows for modularization and reuse of code by incorporating external files containing function prototypes, declarations, and definitions.`

```C
#include <stdio.h>
#include "myheader.h"
```

## Macro

Macros provide a powerful mechanism for defining reusable code snippets, constants, or inline functions using the `#define` directive. These macros undergo substitution by their respective definitions before the actual compilation process begins.

Before compilation macro template will be replaced with the macro expansion in the entire program.

macro template is also known as symbolic constant i.e it can't be changed during program execution.

```C
#define SQR(x) x*x

void main(){
    int y = 5, z;
    z = y / SQR(y); 
    // z = y / y * y;
    // z = 5 / 5 * 5;
    // z = 1 * 5;
    printf("%d", z); 
}
```

```C
#define MAX(a, b) ((a) > (b) ? (a) : (b))

void main() {
    int x = 10, y = 20;
    int max_value = MAX(x, y);
    printf("Maximum value is %d", max_value);
}
```

| `const int x = 10;`                                            | `#define N 10`         |
| -------------------------------------------------------------- | ---------------------- |
| memory is needed                                               | no memory is needed    |
| Scope can be local or global depending on where  it is defined | Scope is always global |

