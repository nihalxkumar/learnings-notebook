1. Count the number of lines and loops for the same
2. Find relation between line number, number of characters and spaces in that line. Apply loop for the same.


```
1
12
123
1234
12345
```

<details>
<summary>Code</summary>

```C
for (l = 1, l <= 5, l++){
    for (ch = 1, ch <= l, ch++){
        printf("%d", ch);
    }
    printf("\n");
}
``` 

</details>

---

```
1
23
456
78910
```

<details>
<summary>Code</summary>

```C
int x = 1;
for (l = 1; l <= 4; l++){
    for (ch = 1, ch <= l, ch++){
        printf("%d", ch);
        x++;
    }
    printf("\n");
}
``` 

</details>

---
```
1
11
111
1111
111
11
1
```
<details>
<summary>Code</summary>

```C
for (l = 1; l <= 7; l++)
{
    if (l <= 4){
        for (ch = 1; ch <= l; ch++)
        printf("1");
    }else{
        for (ch = 7; ch >= l; ch--)
        printf("1");
    }
    printf("\n");
}
```

</details>

---
```
1111
 111
  11
   1
  11
 111
1111
```

<details>
<summary>Code</summary>

```C
for (l = 1; l <=7; l++)
{
    if (l<=4){
        for (s = 2; s <= l; s++){
            printf(" ");
        }
        for (ch = 4; ch >= l; ch--){
            printf("1");
        }
    } else {
        for (s = 6; s >= l; s--){
            printf(" ");
        }
        for (ch = 4; ch <= l; ch++){
            printf("1");
        }
    }
}
```

</details>

---

```
1     1
11   11
111 111
1111111
```


<details>
<summary> Code </summary>

```C
int ch, l, s, s1 = 1, l1= 1;

    for (l = 1; l<= 4; l++)
    {
        for (ch = 1; ch <= l; ch++){
            printf("1");
        }
        for (s = 5; s >= s1; s--){
            printf(" ");
        }
        s1 += 2;
        for (ch = 1; ch <= l1; ch++){
            printf("1");
        }
        if (l != 3){
            l1++;
        }
        printf("\n");
    }
```

or

```C
#include <stdio.h>

int main() {
    int rows = 4;
    int spaces = rows * 2 - 2;

    for (int i = 1; i <= rows; i++) {
        for (int j = 1; j <= i; j++) {
            printf("1");
        }
        for (int k = 1; k <= spaces; k++) {
            printf(" ");
        }
        spaces -= 2;
        for (int l = 1; l <= i; l++) {
            printf("1");
        }
        printf("\n");
    }
    return 0;
}
```

</details>

---

<!-- 
```
1111111
111 111
11   11
1     1
```

<details>
<summary>Code</summary>

```C    
int s1=-2, l1=1, l, ch, s;

for (l = 1; l <= 4; l++){
    for(ch = 4; ch >= l; ch--){
        printf("1");
    }
    for(s = 0; s <= s1; s++){
        printf(" ");
    }
    s1 += 2;
    for(ch = 3; ch <= l1; ch--){
        printf("1");
    }
    if (l != 1){
        l1++;
    }
    printf("\n");
}
```

</details> 

-->


```
abcdefgfedcba
abcdef fedcba
abcde   edcba
abcd     dcba
abc       cba
ab         ba
a           a
```

<details>
<summary>Code</summary>

```C  
  
#include <stdio.h>

int main(){
    int l, s, s1 = -2 ;
    char ch, ch1, end = 'g';

    for (l = 1; l <= end; ch++){
        for(ch = 'a'; l <= end; ch++;){
            printf("%c", ch);
        }
        for(s = 0; s <= s1; s++){
            printf(" ");
            s1 += 2;
        }
        
        if(l == 1){
            end--;
        }
        for(ch1 = ch-1; ch1 >= 'a'; ch1--;){
            printf("%c", ch1);

        }
        printf("\n");
    }
}
```

</details> 


