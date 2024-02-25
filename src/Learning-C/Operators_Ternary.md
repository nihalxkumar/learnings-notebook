# Ternary

Conditional operator that takes three operands. It is also known as the conditional operator because it evaluates a
condition and returns one of two values based on the result of the evaluation. The ternary operator is represented by
the question mark (?) and the colon (:).

`condition ? expression1 : expression2;`

The condition is evaluated first. If the condition is true, then expression1 is executed, and its value is returned. If
the condition is false, then expression2 is executed, and its value is returned.

```C
int num = 5;
num % 2 == 0 ? printf("Even") : printf("Odd");
```

Advantageous over the if-else statement. It is concise, easy to read, and saves time and effort.

Useful to assign a value to a variable based on a condition.

Associativity is from Right to Left.

---

```C
a = 10?0?2:3:1
```

First step go from right to left and draw paratheses around the `?` and `:`

```C
a = 10 ? (0 ? 2 : 3) : 1;
```

Now, evaluate the condition from left to right.

```C
a = 10 ? (0 ? 2 : 3) : 1;
// any non zero value is true. we have 10 so, we will go to the first expression.
// Now we evaluate the nested ternary operator (0 ? 2 : 3).
// Since 0 is considered false, we move to the second expression which is 3.
// Therefore, a is assigned the value 3.
a = 3
```

