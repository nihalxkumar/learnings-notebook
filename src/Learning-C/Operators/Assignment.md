# Assignment

Assignment operators are used to assign values to variables. They not only perform the assignment but also allow for combining arithmetic or bitwise operations in a single step.

- `=` Assign
- `+=` Add and Assign
- `-=` Subtract and Assign
- `*=` Multiply and Assign
- `/=` Divide and Assign
- `%=` Modulus and Assign
- `<<=` Left Shift and Assign
- `>>=` Right Shift and Assign
- `&=` Bitwise AND and Assign
- `^=` Bitwise XOR and Assign
- `|=` Bitwise OR and Assign

These operators allow for combining arithmetic or bitwise operations with assignment in a single step.

## Types of Assignment Operators

1. Simple Assignment:
   - In simple assignment, a single variable is assigned a value using the = operator.

2. Compound Assignment:
   - Compound assignment operators combine arithmetic or bitwise operations with assignment. They operate on the variable itself, modifying its value in place.

## Rules for assignment operators

1. Single variable is allowed in LHS of assignment operator
2. Cascading of assignment operator
   - `int x=y=z=2;`
- Associativity of assignment operator is from Right to Left

---

Q. Swap values without introducing a third variable. `x = 5` and `y = 2`

Sol. There are many ways

```C
// Method 1: Using Arithmetic Operations
x = x + y; // x = 5 + 2 => 7
y = x - y; // y = 7 - 2 => 5
x = x - y; // x = 7 - 5 => 2
```

```C
// Method 2: Using Multiplication and Division
x = x * y; // x = 10
y = x / y; // y = 10/2 => 5
x = x / y; // x = 10/5 => 2
```