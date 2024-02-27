# if statements

The `if` statement is used to execute a block of code if the condition is true. If the condition is false, another block of code can be executed using the `else` statement. The `else` statement is optional.

> Every control structure has bydefault scope of one statement [semi colon]. If you want to execute more than one statement, you need to use a block statement `{}`.

### Examples and Explanations:

#### Example 1: Scope

```c
int x = 5;
if (x == 4);
printf"x is equal to 5");
// output will be "x is equal to 5"
// because the if statement has a semicolon at the end and scope ended there.
```

#### Example 2: Scope of if Statement

```C
int x = 9;
if (x == 5)
printf("x is equal to 5");
printf("x is equal to 9");
// output will be "x is equal to 9"
// because scope of if statement is only one statement.
```

# if-else statements

The if-else statement allows execution of different code blocks based on whether a condition is true or false.

```C
int x = 5;
if (x == 4) {
    printf("x is equal to 4");
} else {
    printf("x is not equal to 4");
}
// Output: "x is not equal to 4"

```

```C
int x = 3;
if (x > 3) {
    printf("abc");
}
printf("def"); // Incorrect placement
else {
    printf("ghi");
}
```

#### misplaced else

The term 'misplaced else' refers to placing an else statement outside of its intended block (the one following the last if or elif) when writing nested conditionals. This leads to unexpected behavior because the else clause will be associated with the nearest preceding if or elif, which may not have been intended.

```C
float x = 0.7;
if (x == 0.7)
printf("abc");
else
printf("def");
```

Here, the issue lies in the comparison if (x == 0.7). The problem arises due to the way floating-point numbers are stored and represented in computer memory.

When the value 0.7 is assigned to the variable x, it is stored as a binary floating-point number with a limited precision. This binary representation may not be an exact match for the decimal value 0.7 due to the inherent limitations of representing real numbers in a finite amount of memory.

As a result, when comparing x with the literal 0.7, there may be a slight difference between the two values due to rounding errors or precision issues in floating-point arithmetic. This can lead to the comparison (x == 0.7) evaluating to false even though logically we might expect it to be true.

if both had the exact binary then there would be no issue. like in `float x = 0.5 if (x == 0.5) printf("abc"); else printf("def");` the output will be "abc"

# if-else-if

if-else-if statement allows you to test multiple conditions sequentially.

```C
int num = 10;

if (num > 0) {
    printf("Number is positive\n");
} else if (num < 0) {
    printf("Number is negative\n");
} else {
    printf("Number is zero\n");
}
```
