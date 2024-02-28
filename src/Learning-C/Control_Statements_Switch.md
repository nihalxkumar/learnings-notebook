# Switch

The `switch` statement is used to execute a block of code based on the value of a  variable or an expression. It provides an alternative to using multiple `if-else` statements when there are multiple possible execution paths based on a single variable.

## Syntax:

The switch statement evaluates the expression and compares its value with the values specified in the case labels.

The default case is optional and is executed when none of the case labels match the value of the expression. default case can be written anywhere in the switch statement.

```C
#include <stdio.h>

int main() {
    int choice;
    
    printf("Enter a number between 1 and 3: ");
    scanf("%d", &choice);
    
    switch (choice) {
        case 1:
            printf("You entered one\n");
            break;
        case 2:
            printf("You entered two\n");
            break;
        case 3:
            printf("You entered three\n");
            break;
        default:
            printf("Invalid choice\n");
    }
    
    return 0;
}
```

> Unlike if-else statements, switch statements can only be used with integral types (char, int, enum). No variables. Each case label must be a constant expression (integer constants, character constants, or enumerated constants).