# Miscellaneous Operators

There are several additional shorthand operators available in C, each serving unique purposes. Some examples include:

## Comma operator:

It used as an operator[for expressions] and as a separator[for declarations]. It evaluates both operands
and returns the value of the second operand.

Evaluates both operands sequentially and returns the last operand's value. It is commonly used in loops
to update multiple variables simultaneously

```C
// Update x and y together
for (int x = 0, y = 10; x < 10; ++x, --y) {
    // Use updated x and y
}
```

note: The comma operator has the lowest precedence of all C operators.

## Pointer dereferencing (*):

Allows indirect access to memory locations stored in pointers.

```C
char str[] = "Hello World";
printf("%c", *(str + 5)); // Output: 'o'
```

## Type Casting

It refers to explicitly converting values from one data type to another during runtime.

This conversion can be done using the type cast operator ((type))

```C
int x = 3;
float y = (float)x; // Converting int to float
double z = (double)y; // Converting float to double
printf("%f\n%lf", y, z);
```
