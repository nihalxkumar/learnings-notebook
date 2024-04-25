# Increment

The increment operator `++` increases the value of the variable by 1.

The increment operator can be used in two ways:

* Pre-increment `++x`: first increment then assign.
* Post-increment `x++`: first assign then increment.

Both Pre- and post-work the same if used as a single statement. 

However, when used as part of a larger expression, they exhibit different behaviors.

### Example 1:

```C
int a = 5, b;
b = a++ + a++;
printf("%d %d", a, b);
// 7 10
```

### Example 2:

```C
int a = 5, b;
b = ++a + ++a;
printf("%d %d", a, b);
// 7 13
 ```

#### Explanation of Example 1:

1. We declare two integer variables a and b. Initially, a is assigned the value of 5, while we haven't yet set any
   initial value for b.

2. The line b = a++ + a++; performs several operations at once. Firstly, it adds the current values of a (which is still
    5) with itself (again, currently 5). This results in y = 10.
3. Secondly, after adding these values together, it increments a twice – first from its original value of 5 to 6, then
   again to 7.

Note that ++ before a variable means incrementing it by one immediately after the operation. So when used within an
expression like here, it will be applied only once, not twice as you might expect based on the order of appearance.

Use pen and paper. make a table of values of a and b at each step.

| a     | b   |
| ----- | --- |
| ~~5~~ | 10  |
| ~~6~~ |     |
| 7     |     |

### Example 3:

```C
x = 1;
y = x++ * ++x * x++ * ++x * x++ * x++;
```

| x     |
| ----- |
| ~~1~~ |
| ~~2~~ |
| 3     |

y = $3^6$ (6 times we are mulitplying 3 with itself)

x = 7 (x = 1 and there are 6 elemts [ 6 increments]

---

```C
int x ;
x = 5++

//error: lvalue required as increment operand  
//Build failed

// To correct the code we can either use a variable instead of a constant for incrementing
// or assign the result of the increment operation to another variable.
```

int x; declares an integer variable named x, and x = 5++; attempts to increment the value of 5, which is not allowed in
C.

The ++ operator is a unary operator that increments the value of a variable by 1, but it cannot be applied to a constant
like 5.

```admonish note title = "L-value error"
An expression that can appear on the left side of an assignment operator (=).

It represents an object that occupies some identifiable location in memory. An L-value error occurs when you try to assign a value to something that is not a valid storage location, such as a constant or an expression that does not
represent a memory location. 

In the given code, 5 is a constant and cannot be assigned a new value, leading to an L-value error.
```

## Associativity of increment operator

```c
int x = 5;
int y = x++ + ++x;
printf("%d %d", x, y);
// 7 12
```

The increment operator has right-to-left associativity, which means that if multiple increment operators are used in the
same expression, the rightmost one will be evaluated first.

In the given code, `x++` is evaluated first, incrementing the value of x from 5 to 6. Then, `++x` is evaluated, incrementing
the value of x from 6 to 7. Finally, the sum of the incremented values of x (7 and 7) is assigned to y, resulting in y
being assigned the value 14. The final value of x is 7.

