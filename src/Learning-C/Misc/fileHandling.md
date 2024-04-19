# Files

Applications require information to be read from or written to a memory device

  - All files are administered by the Operating System(OS) which allocates and deallocates disk blocks.
  
  - The OS also controls the transfer of data between programs and the files they access 

The most convenient way to handle such large scales of data is to read/write data from/to files. 

## Handling Files in C programs

A file has to be opened before data can be read from or written to it.

When the file is opened, the OS associates a **stream** with the file

A common **buffer** and a file **postion indication** are maintained in the memory for a function to know how much of the file has already been read.

The stream is disconnected when the files is closed.

### Opening a File

```C
FILE *file_pointer_name;
file_pointer_name = fopen("filename", "mode");
```

mode can be one of the following:

- r: Open a file for reading. The file must exist.
- w: Create an empty file for writing. If a file with the same name already exists, its content is erased and the file is considered as a new empty file.
- a: Append to a file. Writing operations append data at the end of the file. The file is created if it does not exist.
- r+ or w+: Open a file for update both reading and writing. The file must exist.
- a+: Supports both reading and writing but  but writing is only supported if it is appended at the end of the file.
- rb: Open a file for reading in binary mode.
- wb: Create an empty file for writing in binary mode.
- ab: Append to a file in binary mode.
- rb+ or wb+: Open a file for update both reading and writing in binary mode.

### Closing a File

Although it is not required to close a file. However, it is a good practice to do so for various reasons:

Operating systems have a limit on the number of files that a program can open.

Multiple programs might be trying to access the same file, and they cannot do so until the current program closes the file stream.

```C
fclose(file_pointer_name);
```

### Reading and Writing to a File

The standard library offers a number of functions for performing read and write on the files

1. character oriented functions (`fgetc` and `fputc`)
2. line oriented functions (`fgets and `fputs`)
3. formatted functions (`fscanf` and `fprintf`)


- `fgetc`: 
  - It fetches the next character that has not yet been read from the file.
  - `fgetc(FILE *stream);`
  - It could be used as follows: `int c = fgetc(fp);`
  - If there are no more characters to be read from the file, fgetc returns EOF. 

~~~admonish note title = "EOF (End Of File)"
EOF is an integer defined in stdio.h, having a value of -1. So, if we wanted to read all characters from a file, it could be done inside a while loop, as follows:

```C
while((c = fgetc(fp)) != EOF) {
    // Process the current character in c here.
}
```

This loop will automatically terminate on EOF.
~~~

- `fputc`:
  - It outputs a character to the current file. 
  - `fputc(int c, FILE *stream);`
  - Note that although the syntax specifies int, the output is a character, so we need to enter the ASCII code. For example, `fputc(70, fp);` outputs ‘F’, because the ASCII code of ‘F’ is 70.

- `fgets`:
  - `fgets(char *s, int size, FILE *stream);`
  - This is a line-oriented function. fgets reads at most size - 1 characters from the file stream and saves the characters in s. After that, `\0`, the string-terminating character, is automatically appended to s.
  - Note that if a newline is encountered before size - 1 characters, then fgets automatically stops reading. So, fgets will read size - 1 characters or one entire line, whichever is smaller. Example usage: `char buf[10];` `fgets(buf, 10, fp);`

- `fputs`:
  - `fputs(const char* s, FILE *stream);`
  - The fputs function writes the string of characters in `s` to the file stream.

- `fscanf` and `fprintf`:
  - These function exactly like scanf and printf, except we need to specify the file stream as the first argument. 
  - `fscanf(FILE *stream, ….)` (the rest is the same as normal scanf/printf).

    ```C
    fscanf(fp1, “%s%d%d”, name, &marks1, &marks1);
    fprintf(fp2, “%s %d %d %d”, name, marks1, marks2, marks1 + marks2);
    ```


### Example

```C
#include <stdio.h>

int main() {
    FILE* fp = open("file.txt", "w+");
    char buf[] = "A1234 abcd";
    fputs(buf, fp); // Writes "A1234 abcd" to fp.
    rewind(fp); // Go back to position 0 of fp.
    int c = fgetc(fp); // c = 'A';
    fputc(c, stdout); // Prints A to standard output (explained later).
    int x;
    fscanf(fp, "%d", &x); // x = 1234
    fprintf(stdout, " %d", x); // Prints 1234
    fclose(fp);
}
```

## Special Files

- `stdin`: Standard input file. It is a file that is automatically opened when a program starts. It is used to read input from the keyboard.
- `stdout`: Standard output file. It is a file that is automatically opened when a program starts. It is used to write output to the screen. It is associated with the terminal. 
- `stderr`: Standard error file. It is mainly used for debugging purposes. The default output of stderr is also in the terminal, the same as stdout.

`fscanf()` and `fprintf()` can achieve all of the functionality of `scanf()` and `printf()`, simply by using the special files, stdin and stdout.

`fscanf()` can read from file streams, but `scanf()` cannot.

### Error Handling

The functions that open files return NULL if they fail to open the file. 

```C
FILE *fp = fopen("file.txt", "r");
if (fp == NULL) {
    printf("Error opening file\n");
    return 1;
}
```






