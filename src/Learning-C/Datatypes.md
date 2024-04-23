# Datatypes

Type of data which user wants to store in memory

## Primitive / Predefined / Builtin

### int

- negative numbers are stored in 2’s compliment notation.
- largest +ve number 32767 ($2^{15}-1$)
- for more we have to use modifiers
    -  unsigned (without a sign bit)
        - $0$ to $2^{32}-1$ i.e $0$ to $65535$
    - long
        - 4 bytes are allocated. Range $2^{31}$ to $2^{31}-1$
    - short
      - smallest -ve number -32768 ($-2^{15}$)
      - Range $-32768$ to $32767$
- Generalize nbits $-2^{n-1}$  to $2^{n-1} -1$
⭐ bound checking is not present in C

### float

- used to define variables which can store real numbers
  - $m*b^{e}$
      - `float x;` 4 bytes of memory allocated for x.
      - Range $-3.4 * 10^{38}$ to $3. 4 * 10^{38}$
      - no modifiers for float

### double

- used to define variables which can store real numbers and its range is more than float
- `double x;` 8 bytes of memory allocated for x.
  - Range $-3.4 * 10^{308}$ to $3. 4 * 10^{308}$
  - Only one modifier: Long.
    - 10 bytes of memory allocated
    - $-1.7 * 10^{4932}$ to $17 * 10^{4932}$

### char
  - used to define variables which can store character
  - `char x;` only 1 byte of memory is allocated for x.
  - $-2^7$ to $2^7-1$  => -128 to 127
  - Only one modifier Unsigned. One byte memory
      - $0$ to $2^8-1$ => 0 to 255
  - Character constant can initialize variable having char data
      - `char x='a';` here `a` is a character constant
      - `char x=a;` here `a` is a variable 
  - Character constant can be single or double ch long. It can’t be of triple characters.
      
### void

- non returnable functions & pointers

## User defined

- structure
- union
- enum

~~~admonish note
C uses extended ASCII code of 8bits.

because of escape sequences:
```c
char x = 97 // x = 9

char x = 'ab' // `x = 'a`
``` 
~~~