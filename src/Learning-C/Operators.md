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

1. [Arithmetic](Operators_Arithmetic.md)
2. [Assignment](Operators_Assignment.md)
3. [Relational](Operators_Relational.md)
4. [Logical](Operators_Logical.md)
5. [Increment](Operators_Increment.md)
6. [Decrement](Operators_Decrement.md)
7. [Shorthand](Operators_Shorthand.md)
8. [Ternary](Operators_Ternary)
9. [Size of operator](Operators_Sizeof.md)
10. [Miscellaneous](Operators_Misc)

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