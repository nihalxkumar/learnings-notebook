# Logical
Logical operators are used to combine two or more conditions to determine the logic between values

- NOT Operator (`!`)

  - The **Not Operator** is represented by an exclamation mark (!). It reverses the logical state of its operand. It converts true to false and false to true.
  - In this example, the condition x > 5 evaluates to false, but the ! operator reverses it, so the message will be printed.
    ```c
    int x = 5;
    if (!(x > 5)) {
        printf("x is not greater than 5\n");
    }
    ```
- AND Operator (`&&`)

  - The AND Operator is represented by double ampersands (&&). It returns true only if both operands are true. For instance:
  - In this case, both x > 5 and y < 10 are true, so the message will be printed.
    ```c
    int x = 6, y = 8;
    if (x > 5 && y < 10) {
        printf("Both conditions are true\n");
    }
    ```

- OR Operator (`||`)
    - The OR Operator is represented by double pipes (||). It returns true if at least one of the operands is true.
    - In this example, x > 5 is false, but y < 10 is true, so the message will still be printed.
    ```C
    int x = 3, y = 12;
    if (x > 5 || y < 10) {
        printf("At least one condition is true\n");
    }
    ```

```admonish note title = "Short-curcuiting"
Short-circuiting refers to a feature of logical operators in programming languages that prevents unnecessary computation when the result of an expression becomes determinable based on earlier parts of the expression. 

Specifically, for the `OR` operator (`||`), short-circuiting means that once a true value is found among the operands, the entire expression returns true without evaluating subsequent operands. 

Conversely, for the `AND` operator (`&&`), short-circuiting means that once a false value is found among the operands, the entire expression returns false without evaluating subsequent operands
```

> Any non-zero value in case of C is considered as True
> 
> Order of precedence:
> 
> NOT > AND > OR