# Strings

Strings, represent arrays of characters and are fundamental for handling text data.

### Initialization

Strings in C can be initialized in a couple of ways:

```c
char x[3] = {'a', 'b', '\0'};
```

Here, '\0' denotes the null character, which terminates the string. It's essential for string manipulation and is represented by ASCII 0.

Alternatively:

```c
char x[3] = "ab";
```

This form automatically appends the null character at the end of the string.

It's crucial to ensure that the size of the array is one more than the number of characters in the string to accommodate the null character properly. Otherwise, it can result in compilation errors such as 'Too many initializers.'

```C
char x[10];
x = "abc";
printf("%s", x[6]);
// This will result in an L-value error
```

Attempting to assign a string directly to an array (x) will result in an L-value error. Instead, strings can only be assigned to pointers in C.


| gets()                                                               | scanf()                                                 |
| -------------------------------------------------------------------- | ------------------------------------------------------- |
| Accepts only input strings                                           | Accepts input for various data types                    |
| Recognizes space                                                     | doesn't recognize space                                 |
| No need for the '&' symbol                                           | Requires the '&' symbol for input variables             |
| Allows input of only one string at a time `gets(x/y) //not possible` | Can accept multiple strings at once `scanf("%s%s",x,y)` |
| <string.h>                                                           | <stdio.h>                                               |


Similar distinctions apply to output functions like `puts()` and `printf()`.

`puts()` automatically moves the cursor to the next line after printing the string, whereas `printf()` does not. These functions are essential for outputting strings efficiently in C programs.

