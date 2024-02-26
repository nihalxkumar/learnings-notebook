# Input and Output

Standard Input and Output in C is done using the `printf` and `scanf` functions.

These functions are defined in the `stdio.h` header file.

## Format specifiers

Some format specifiers are as follows:

| Format Specifier | Description                                   |
|------------------|-----------------------------------------------|
| `%d`             | Integer                                       |
| `%f`             | Float                                         |
| `%c`             | Character                                     |
| `%s`             | String                                        |
| `%lf`            | Double                                        |
| `%x`             | Hexadecimal                                   |
| `%o`             | Octal                                         |
| `%u`             | Unsigned Integer                              |
| `%e`             | Scientific Notation                           |
| `%p`             | Pointer                                       |
| `%n`             | Number of characters written so far           |
| `%m`             | Error message corresponding to the last error |
| `%[]`            | Scanset                                       |
| `%*`             | Suppresses assignment                         |
| `%l`             | Long                                          |
| `%ll`            | Long Long                                     |
| `%h`             | Short                                         |
| `%hh`            | Char                                          |

#include <stdio.h>

standard input output header file

`#include` is a preprocessor directive which tells the compiler to include the contents of the file specified in the
program.

## Input

To obtain input from users within C programs, there are several built-in functions available. Four common methods
include `scanf`, `getchar`, `getch`, and `getche`. Each has its own characteristics and usage scenarios.

`scanf`: This function allows you to read formatted data from the standard input.

```C
int num;
scanf("%d", &num);
```

`getch`: reads a character from the console but does not display it on the screen.

`getche` echoes the character back to the console. It reads a character from the console and displays it on the screen
