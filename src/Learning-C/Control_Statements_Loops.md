# Loops

## While loop

## Do-While Loops

It is similar to the `while` loop but with one key difference: the `do-while` loop always executes its body at least once, even if the condition is initially false.

## Understanding how `while` and `do-while` loops can be simulated in place of each other by rearranging the code structure. :

### Example:

```C
int i = 0;
while (i < 10) {
    // Code to be executed
    i++;
}
```

This can be done using a Do-While loop as:

```C
int i = 0;
do {
    // Code to be executed
    i++;
} while (i < 10);
```

 The `While` loop checks the condition before executing the code, whereas, the `Do-While` loop executes the code first and then checks the condition. The examples above demonstrate how to rearrange the code to achieve the same functionality using either loop construct.