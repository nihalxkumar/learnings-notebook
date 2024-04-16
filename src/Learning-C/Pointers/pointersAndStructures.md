# Pointers and Structures

```c
struct stud{
    int roll;
    char dept_code[25];
    float cgpa;
} class, *ptr;

struct book{
    char Name[20];
    float price;
    char ISB[30];
}; struct book b, *br;
```

~~~admonish success title = "Allowed"

```c
ptr = &class;
```

```c
br = &b;
```

~~~

```admonish danger title = "Not Allowed"
ptr = &b;

br = &class;
```

Once `ptr` points to a structure variable, the members can be accessed through a dot operator or an arrow operator.

```c
(*ptr).roll
(*ptr).dept_code
(*ptr).cgpa
```

```c
ptr->roll
ptr->dept_code
ptr->cgpa
```

Order of precendence  
  1. `()`
  2. `[]`
  3. `->`
  4. `.`

```admonish

- `ptr->roll` is equivalent to (`*ptr).roll`

- `*ptr.roll` is invalid

- `*p->x` is same as *`(p->x)`

- `*p[n]` is same as `*(p+[n])`

- `*p->x++` is same as `*((p->x)++)`

- `++*p[n]` is same as `++(*(p[n]))`

- `++*p->y` is same as `++(*(p->y))` and `++(*((*p).y))`
```

> structure variables are passed by value just like primitive datatypes(intger, char, float, etc.) The only difference is that the structure name is used instead of the data type name. 
> arrays are generally passed by reference.


