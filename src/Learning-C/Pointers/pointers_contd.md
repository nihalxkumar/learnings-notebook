# Pointers

Misc

### Distinguishing Between Void Pointers and Char Pointers

| Void Pointers                                                               | Character Pointers                                                    |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Truly generic. Can point to any data type                                   | Points to characters or bytes (given a byte is just an unsigned char) |
| Cannot be dereferenced directly since the data type it points to is unknown | Can be dereferenced directly                                          |
| Requires type casting before dereferencing                                  | Used for byte-level operations.                                       |


### Pass by Value and Pass by Reference

#### Pass by value

| Advantages                                                           | Disadvantages                                                                                                     |
| -------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Easy to understand - you can just pass copies, nothing to deference. | Performance overhead - A big object like a struct to be copied will be time and memory intensive.                 |
| Safe - Original data won't be modified by the called function        | Short reach(Lack of direct access) - Called functions can only modify local copies. This can be a good thing too. |

#### Pass by reference

| Advantages                                                                                                                   | Disadvantages                                                                        |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Efficiency  - You just pass an address, it can point to a gigantic structure, not a problem.                                 | Can be complex to understand - You have to dereference the pointer to get the value. |
| Direct access - can modify data outside the called function. This trick allows us to return multiple values from a function. |                                                                                      |
### Associativity

pointers have unary operators therfore associativity is right to left

```C
int *p;
int x = 5.2;
p = &x;
printf("%d", *(int*)p);
```

here if we had 

```C
printf("%f", (int*)*p);
```

It would result in a compilation error because of associativity rule.

Another case of associativity:

```C
printf("%u", (int*)p++);
```

This will result in an error because the compiler will try to add 1 to the pointer first and then typecast it to an integer pointer. To avoid this, we can use parentheses to enforce the correct order of operations:

```C
printf("%u", ((int*)p)++);
```

This will add 1 to the pointer p first and then typecast the result to an integer pointer.



> *(arr + 1) = arr[1]
> 
> int *a[5] mean “a” is an array of 5 integer pointers.

~~~admonish note
```c
#include <stdio.h>

int main() {
    int *ptr[3], i , iA[]={5,10,15}, iB[]={1,2,3}, iC[]={2,4,6};
    ptr[0]=iA; ptr[1]=iB; ptr[2]=iC;
    for(i=0; i<3 ; i++){
        printf("iA[%d]: address=%p data=%d", i, ptr[0]+i, *(ptr[0]+i));
        printf("iB[%d]: address=%p data=%d", i, ptr[0]+i, *(ptr[0]+i));
        printf("iC[%d]: address=%p data=%d", i, ptr[0]+i, *(ptr[0]+i));
    }

    return 0;
}
```
~~~


-----

Resources to refer to:

- [Syntax Explained](https://cdecl.org/)
- [Syntax Visualized](https://www.dcode.fr/c-declaration-explained)
- [Binary representations of floating point formats](https://float.exposed)
- [oceanO's Article on pointers](https://medium.com/@jalal92/just-dereference-the-link-for-the-code-in-the-video-cdfc0c2d9547)
