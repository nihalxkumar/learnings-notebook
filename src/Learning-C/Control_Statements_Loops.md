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

## For loop

The for loop is suitable for situations where the number of iterations is known beforehand and depends on a counter variable.

Any or all of the initialization, condition, and update statements can be omitted, but the semicolons must still be present.

```c
for (initialization; condition; update) {
    // code to be executed
}

```C
#include <stdio.h>

int main() {
    int n, i;
    for (int n = 1; n < 10; n += 3)
    {
        for(int i = 1; i < 11; i++)
        {
            printf("%d*%d=%d\t%d*%d=%d\t%d*%d=%d\n",
                n,i,n*i,
                (n+1),i,(n+1)*i,
                (n+2),i,(n+2)*i);
        }
        printf("\n");
    }
    return 0;
}
```

