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

---

### Logic building theoretical knowledge

#### Example 1:

```C
#include <stdio.h>

char x = 'a'
switch (x) {
// 97
case 'a':
// 97 OR
case 'e':
case 'i':
case 'o':
case 'u':
printf("vowel");
break;
default:
printf("not vowel");
}
// the expression became 97 OR which will result shortcuiting in TRUE -> 1 -> case 1 -> 97 compared to 1 -> Not Vowel
```

#### Example 2: Using switch to print grade of a student based on marks:

61-70 -> D

71-80 -> C

81-90 -> B

91-100 -> A

```C
if(x%10 == 0)
x --;
switch(marks/10)
{
    case 6:
    printf("D");
    break;
    case 7:
    printf("C");
    break;
    case 8:
    printf("B");
    break;
    case 9:
    printf("A");
    break;
    default:
    printf("invalid");
}
```


#### Example 3: 

You can not put `case 'a'` and `case  '97'` together. It will result in a duplicate case error. 

---


| Else if ladder | Switch                  |
| -------------- | ----------------------- |
| no break       | break required          |
| any condition  | only equality condition |
| any data type  | only character constant |