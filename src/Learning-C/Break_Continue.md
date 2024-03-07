# Break

`Break` can come in switch or a body of loop. `Break` is used to exit the loop or switch statement.

```c
for (n=1;, n<=500; n+1)
{
    for (i = 2; i <= n/2; i++)

    {
    if (n%i == 0)
        break;
    }

    if (i == n/2 + 1)
    printf("%d\n", n);
}
```


# Continue

`Continue` can come only in body of a loop. `Continue` is used to skip the current iteration and continue with the next iteration of the loop by bringing the control at the begining of body of loop.

```c
for (i = 1; i <= 10; i++)
{
    if (i == 5)
        continue;
    if (i == 6)
        break;
    printf("%d\n", i);
}
```
