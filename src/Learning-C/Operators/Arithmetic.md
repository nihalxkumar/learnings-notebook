# Arithmetic

`+`, `-`, `*`, `/` (quotient operator), `%` (remainder operator or modulus)

> in $n/d$ if $n< d$ then output is $0$
>
> in $n \% d$ if $n<d$ then output is $n$

Rules for arithmetic operators:-

- int/int is always int

- Modulus operator cannot be used with floating point numbers as by default every float is treated as double. C is an
  expanding language.  `5.2%2` => Error

If more than 1 operator is present in an expression then precedence rule will be applied.

PEMDAS stands for

- Parentheses
- Exponents
- Multiplication
- Division
- Addition and Subtraction

If multiple operations with the same precedence appear, they are typically performed from left to right.