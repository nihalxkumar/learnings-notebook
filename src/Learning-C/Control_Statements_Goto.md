jumping to a specific location in the program.

```C
int main() {
    int x = 5;
    if (x < 0) {
        goto error;
    }
    // Code to be executed when x is positive
    return 0;
error:
    printf("Error: x is negative\n");
    return -1;
}
```

```C
int complex_function(void) {
    if (initialize_1() != SUCCESS) { goto out1; }
    if (initialize_2() != SUCCESS) { goto out2; }
    if (initialize_3() != SUCCESS) { goto out3; }

    /* other statements */

    return SUCCESS;

  out3:
    deinitialize_3();
  out2:
    deinitialize_2();
  out1:
    deinitialize_1();
  return ERROR;
}
```

