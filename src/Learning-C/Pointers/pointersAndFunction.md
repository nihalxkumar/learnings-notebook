# Pointers and Functions

```C
#include <stdio.h>

// Formal arguments: int *a, int *b
void swap (int *a, int *b){
    int t;
    t = *a;
    *a = *b;
    *b = t;
}

int main() {
    int x = 5, y = 2;
    // Actual arguments: &x, &y
    swap(&x, &y);
    printf("%d %d", x, y);
    return 0;
}
```

```admonish info title="Call by Value and Call by Reference"

In `main()`, the values of `x` and `y` are 5 and 2, respectively.
When swap(`&x`, `&y`) is called, the addresses of `x` and `y` (let's say they are `0x1234` and `0x5678` respectively) are passed as the actual arguments.
Inside the swap function, the formal parameters `a` and `b` are assigned the copies of the addresses `0x1234` and `0x5678`.
Within the swap function, the values pointed to by `a` and `b` (which are the values of `x` and `y`) are swapped, so now `*a` is 2 and `*b` is 5.
After the swap function returns, the values of `x` and `y` in `main()` have been swapped, so `x` is now 2 and `y` is now 5.

The key point here is that the swap function receives copies of the addresses, not the actual variables `x` and `y`. This is an example of **call by value**, where the function operates on the copies of the arguments, not the original variables.

Value of actual arguement is copied into formal arguements and any change done to the formal arguements will not reflect in the actual arguements.

If we had used call by reference, the swap function would have had direct access to the original variables `x` and `y`, and the swap would have been performed on the original values, not copies.
```

```C
#include <stdio.h>

void mystery(int *ptra, int *ptrb) {
    int *temp;
    temp = ptrb;
    ptrb = ptra;
    ptra = temp;
}

int main() {
    int a = 2016, b = 0, c = 4, d = 42;
    mystery(&a, &b);
    if (a < c)
        mystery(&c, &a);
    mystery(&a, &d);
    printf("%d", a);
    return 0;
}
```

```C
#include <stdio.h>

int f(int x, int *py, int **ppz) {
    int y, z;
    **ppz += 1;
    z = **ppz;
    *py += 2;
    y = *py;
    x += 3;
    return x + y + z;
}

int main() {
    int c, *b, **a;
    c = 4;
    b = &c;
    a = &b;
    printf("%d", f(c, b, a));
    return 0;
}
```

```C
#include <stdio.h>

void f(int *p, int *q)
{
  p = q;
 *p = 2;
}
int i = 0, j = 1;
int main()
{
  f(&i, &j);
  printf("%d %d \n", i, j);
  getchar();
  return 0;
}
```