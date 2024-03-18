# Functions

Part of a program designed to perform a specific task. It is a self-contained block of code that encapsulates a specific task or related group of tasks.

Fucntions can be Predeined or Userdefined.

Reusability, modularity, and abstraction are the main advantages of using functions.

Disadvantages include  memory overhead and the potential for slower execution.

Function can never be defined inside definitionof another function

Function can return onlya  single value at a time

```C
#include <stdio.h>

// Function declaration
void calculate(int x, int *y, int *z);

int main() {
    int a = 10;
    int b, c;
    
    // Function call
    calculate(a, &b, &c); // here &b and &c are actual arguments. Also known as call by reference.
    
    // Output
    printf("a: %d square of a: %d cube of a: %d", a, b, c);
    
    return 0;
}

// Function definition
void calculate(int x, int *y, int *z) {
    // here int *y and int *z are pointers or addresses of b and c. This is also known as call as formal arguments.
    *y = pow(x, 2);
    *z = pow(x, 3);
}
```

Function execution can be understoodjk using the example of reading a book with a bookmark. When a person reads a book and uses a bookmark to attend to another matter, they can easily return to the exact point where they left off in the book. This process mirrors how functions in programming work, allowing for the temporary suspension of one task to perform another and then seamlessly returning to the initial task.


#### Prototyping

It is done to give the compiler an idea about the function name, return type and parameters.

IF functions are defined before calling then no need to prototype.

#### Function Calling

It is also called as function invocation. Whenever a function is called, the control of the program is transferred to the function definition. The function definition is executed and the control is transferred back to the calling function.

Before transferring the control to the function definition, the actual arguments are passed to the formal arguments. The formal arguments are the parameters of the function definition. The actual arguments are the parameters of the function call.

Next line address of main() is pushed onto the stack and all the variables used in main() are now dead. ie. they cant be accessed in calculate() and all the variables of calculate() are now alive.

Afgter executing the calculate() the control is transferred back to main() and the next line address of main() is popped from the stack and all the variables of calculate() are now dead and all the variables of main() are now alive.

#### Return Type
 
It is the type of value that the function returns. If the function does not return any value then the return type is void.

