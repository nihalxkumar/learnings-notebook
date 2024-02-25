# Assignment

`=`, `+=`, `-=`, `*=`, `/=`, `%=`, `<<=`, `>>=`, `&=`, `^=`, `|=`

These operators allow for combining arithmetic or bitwise operations with assignment in a single step.

- 2 types of assignment
    - Simple
    - Compound

Rules for assignment operators

1. Single variable is allowed in LHS of assignment operator
2. Cascading of assignment operator

- `int x=y=z=2;`
- Associativity of assignment operator is from Right to Left

---

Q. Swap values without introducing a third variable. `x = 5` and `y = 2`

Sol. There are many ways

```C
x = x + y; // x = 5 + 2 => 7
y = x - y; // y = 7 - 2 => 5
x = x - y; // x = 7 - 5 => 2
```

```C
x = x * y; // x = 10
y = x / y; // y = 10/2 => 5
x = x / y; // x = 10/5 => 2
```