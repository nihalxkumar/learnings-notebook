# Operators

Operators are symbols used to manipulate data.

In the expression `z = x + y`, `z`, `x`, and `y` are operands, while `=` and `+` are operators.

## Operators Based on the Number of Operands

1. **Unary**
    - 1 operand
    - Examples: `x++`, `++x`, `+x`, `-x`

2. **Binary**
    - 2 operands
    - Examples: `x + y`, `x - y`, `x! = y`, `x==y`

3. **Ternary**
    - 3 operands
    - Only one operator: `?:`

## Operators on basis of functions

1. [Arithmetic](./Arithmetic.md)
2. [Assignment](./Assignment.md)
3. [Relational](./Relational.md)
4. [Logical](./Logical.md)
5. [Increment](./Increment.md)
6. [Decrement](./Decrement.md)
7. [Shorthand](./Shorthand.md)
8. [Ternary](./Ternary)
9. [Size of operator](./Sizeof.md)
10. [Miscellaneous](./Misc)

### General order of Precedence from high to low:

1. Postfix operators (all have the same precedence, so sequences of operators will be evaluated left-to-right)
    - array subscript operator`[]`
    - function call operator`()`
    - component selection operators`.`and`->`
    - postfix`++`and`--`
2. Unary operators (all have the same precedence, so sequences of operators will be evaluated left-to-right)
    - prefix`++`and`--`
    - `sizeof`
    - bitwise negation operator`~`
    - logical negation operator`!`
    - unary sign operators`-`and`+`
    - address-of operator`&`
    - dereference operator`*`
3. Cast expressions`(`_type name_`)`
4. Multiplicative operators`*`,`/`,`%`
5. Additive operators`+`and`-`
6. Shift operators`<<`and`>>`
7. Relational operators`<`,`>`,`<=`,`>=`
8. Equality operators`==`and`!=`
9. Bitwise AND`&`
10. Bitwise XOR`^`
11. Bitwise OR`|`
12. Logical AND`&&`
13. Logical OR`||`
14. Conditional operator`?:`
15. Assignment operators`=`,`+=`.`-=`,`*=`,`/=`,`%=`,`<<=`,`>>=`,`&=`,`^=`,`|=`
16. Sequential (comma) operator`,`

So, expressions like`*x++`are parsed as`*(x++)`, since the postfix`++`has higher precedence than the unary`*`.

Similarly,`sizeof x + 1`is parsed as`(sizeof x) + 1`, since`sizeof`has higher precedence than addition.

An expression like`p++->x`is parsed as`(p++)->x`; both postfix`++`and`->`operators have the same precedence, so they're
parsed from left to right.

When in doubt, use parentheses.

### Associativity

Associativity refers to the order in which operators of the same precedence are evaluated in an expression. 

There are two types of associativity: left associativity and right associativity.

1. **Left Associativity**:
    
   *   For operators with left associativity, evaluation proceeds from left to right. This means that if multiple operators of the same precedence appear consecutively in an expression, they are evaluated from left to right.
    
    ```c
    int result = 10 - 5 + 2;
    ```
    
    In this expression, both the subtraction (`-`) and addition (`+`) operators have the same precedence. Since they are left-associative, the subtraction operation `10 - 5` is evaluated first, followed by the addition operation `5 + 2`.
    
2. **Right Associativity**:
    
    *   Conversely, for operators with right associativity, evaluation occurs from right to left. This means that if multiple operators of the same precedence appear consecutively, they are evaluated from right to left.
    
    ```c
    `int result = 2 ^ 3 ^ 2;`
    ```
    
    In this expression, the bitwise XOR operator (`^`) has right associativity. Therefore, the evaluation starts from the rightmost operator `3 ^ 2`, and then the result is XORed with `2`.
    
Understanding associativity is crucial for correctly interpreting expressions and determining the order of operations. It helps in writing code that produces the expected results and avoids ambiguity in complex expressions.