# Arithmetic

`+`, `-`, `*`, `/` (quotient operator), `%` (remainder operator or modulus)

## Divison and Modulus operator

> in $n/d$ if $n< d$ then output is $0$
>
> in $n \% d$ if $n<d$ then output is $n$

## Rules for arithmetic operators:-

1. Integer Divison
   - int $/$ int is always int

2. Modulus with Integers Only
   - Modulus operator cannot be used with floating point numbers as by default every float is treated as double. C is an
  expanding language.
    ```c
    // Example of incorrect usage:
    float result = 5.2 % 2; // Error
    ```

1. Operator Precedence
   - If more than 1 operator is present in an expression then [precedence rule](https://nihalxkumar.tech/Learning-C/Operators/Operators.html#general-order-of-precedence-from-high-to-low) will be applied.

4 Associativity
  - If multiple operations with the same precedence appear, the [associativity](https://nihalxkumar.tech/Learning-C/Operators/Operators.html#associativity) rule determines the order of evaluation.
  - Arithmetic Operators are left associative.