# If-else

The `if` statement is used to execute a block of code if the condition is true. If the condition is false, another block
of code can be executed using the `else` statement. The `else` statement is optional.

> Every control structure has bydefault scope of one statement [semi colon]. If you want to execute more than one
> statement, you need
> to use a block statement `{}`.

## Brain teasors:

```c
int x = 5;
if (x == 4);
printf"x is equal to 5");
// output will be "x is equal to 5"
// because the if statement has a semicolon at the end and scope ended there.
```

```C
int x = 9;
if (x = 5)
printf("x is equal to 5");
// output will be "x is equal to 5"
// because if(x = 5) is an assignment statement and the value of x is 5.
// non zero expression will be treated as true.
// should have used == for comparison.
```

```C
int x = 9;
if (x == 5)
printf("x is equal to 5");
printf("x is equal to 9");
// output will be "x is equal to 9"
// because scope of if statement is only one statement.
```

