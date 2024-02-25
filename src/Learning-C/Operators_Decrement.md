# Decrement

The decrement operator `--` decreases the value of the variable by 1.

The decrement operator can be used in two ways:

* Pre `--x` first decrement then assign.
* Post `x--` first assign then decrement.

Both Pre- and post-work the same if you are using it as a single statement. But if you are using it as a part of a
bigger expression, then it will make a difference.

Example 1:

```c
int a = 5, b;
b = a-- + a--;
printf("%d %d", a, b);
// 3 10
```

Example 2:

```c
int a = 5, b;
b = --a + --a;
printf("%d %d", a, b);
// 3 8
```

#### Explanation of Example 1:

1. We declare two integer variables a and b. Initially, a is assigned the value of 5, while we haven't yet set any
   initial value for b.
2. The line b = a-- + a--; performs several operations at once. Firstly, it adds the current values of a (which is still
    5) with itself (again, currently 5). This results in y = 10.
3. Secondly, after adding these values together, it decrements a twice – first from its original value of 5 to 4, then
   again to 3.

Note that -- before a variable means decrementing it by one immediately after the operation. So when used within an
expression like here, it will be applied only once, not twice as you might expect based on the order of appearance.

Use pen and paper. make a table of values of a and b at each step.

| a     | b  |
|-------|----|
| ~~5~~ | 10 |
| ~~4~~ |    |
| 3     |    |

Example 3:

```c
x = 6;
y = x-- * --x * x-- * --x * x-- * x--;
```

| x     |
|-------|
| ~~6~~ |
| ~~5~~ |
| 4     |

y = $6^6$ (6 times we are multiplying 6 with itself)

x = 3 (x = 6 and there are 6 elements [ 6 decrements] )

## Associativity of Decrement Operator

```C
int a = 5, b;
b = a-- + a--;
printf("%d %d", a, b);
// 3 10
```

The decrement operator also has right-to-left associativity, which means that the rightmost operator will be evaluated
first.

Initially, the value of a is 5. The rightmost a-- operator is evaluated first, decrementing the value of a from 5 to 4.
Then, the leftmost a-- operator is evaluated, decrementing the value of a from 4 to 3. Finally, the sum of the
decremented values of a (3 and 4) is assigned to b, resulting in b being assigned the value 7.

The final value of a is 3, as it has been decremented twice. Therefore, the output of the code will be "3 10".

