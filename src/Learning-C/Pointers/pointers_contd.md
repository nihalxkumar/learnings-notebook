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
Resources to refer to:

- [Syntax Explained](https://cdecl.org/)
- [Syntax Visualized](https://www.dcode.fr/c-declaration-explained)
- [Binary representations of floating point formats](https://float.exposed)
- [oceanO's Article on pointers](https://medium.com/@jalal92/just-dereference-the-link-for-the-code-in-the-video-cdfc0c2d9547)



<!-- if float needs 4 bytes float **p will result in p+2 -->