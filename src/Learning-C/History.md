## History of Languages

### Low Level languages

#### Machine Language or Binary Language
- Consists of 0s and 1s.
- Computers can only understand binary.
    - Unambiguous, simple, and easy to build.
    - Difficult for humans to read and understand.
    - Not suitable for representing complex data structures.
    - Machine-dependent due to differences in code architecture.


#### Assembly Language
- Uses mnemonics like `ADD`, `SUB`, `MUL`.
- Operands are represented in binaries.
- Language translators (Assemblers) were built to make computers understand mnemonics.
- Assembly language is translated into machine language by an assembler.


## High Level languages

- Resemble English.
- Examples: BASIC, COBOL, FORTRAN, etc.
- Can’t be understood by computers directly, hence language translators are needed.
  - Compiler
  - Interpreter

| Feature            | Compiler                                                                                    | Interpreter                                                                        |
|--------------------|---------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| Processing         | Converts the entire source code into object code before execution                           | Translates and executes source code line by line                                   |
| Execution Speed    | Compiled code runs faster                                                                   | Interpreted code runs slower                                                       |
| Error Handling     | Displays all errors after compilation                                                       | Displays errors of each line one by one                                            |
| Memory Requirement | Requires more memory                                                                        | Requires less memory                                                               |
| Portability        | Cannot be easily ported as it is bound to a specific target machine                         | Works well in web environments and can be easily ported                            |
| Debugging          | Difficult to debug as the program cannot be changed without getting back to the source code | Easier to debug as programs written in an interpreted language are easier to debug |


High-Level Languages -> Character User Interface

### Fourth Generation languages

- Aimed to have minimum input and maximum output.
- Examples: Visual Basic (VB), SQL, etc.
- Time is saved because of shorter input, but it takes more memory, 
making it less efficient than High-Level Languages.

### Fifth Generation Languages

- Designed for AI.
- Examples: LISP, PROLOG.
