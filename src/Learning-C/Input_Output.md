# Input and Output

Standard Input and Output in C is done using the `printf` and `scanf` functions.

These functions are defined in the `stdio.h` header file.

## Format specifiers

Some format specifiers are as follows:

| Format Specifier | Description                                   |
| ---------------- | --------------------------------------------- |
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


#### Standard functions for input

`getc()` can read from any source (keyboard, files, etc)

`getchar()` can read only from keyboard


#### Non standard functions for input

`getch()`: r reads a single character from the standard input stream (usually the keyboard) without echoing it to the screen. It doesn't let the input go into buffer. 

`getche()`: is similar to getch(), but it does echo the character to the screen.

#### Standard functions for output

`printf()`: is most liberal in terms of reading strings.

`putc()`: writes a single character to the standard output stream. Can redirect output to any source (keyboard, files, etc) also, it accepts two arguments, the character to be written and the file pointer where the character is to be written.

`putchar()`: is a macro, not a function. Simplified version of putc(). reads until it encounters a newline character or EOF(negative integer).

#### Non standard functions for output

`gets()`: reads a line of text from the standard input stream, but it is no longer recommended due to potential security vulnerabilities.

`fgets()`: is a safer alternative to gets(), which reads a line of text from a given input stream and stores it in a buffer.

`putch()`: reads until it encounters a newline character or EOF.

