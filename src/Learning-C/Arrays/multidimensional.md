# Multidimensional Arrays

Multidimensional arrays are arrays of arrays. They are useful to implement other data structures, such as matrices.

### Declaration

```c
datatype array_name[number_of_rows][number_of_columns];
```

For example:

```c
int x[2][3];
```

In this declaration, a 2D array of 2 rows and 3 columns named x is created. The index x[0][0] refers to the first element, and x[1][2] refers to the last element.

## 2D Arrays

absctraction of 1D array. every element is an 1D array itself

`int x[3][4] = {{1,2,3,4},{5,6,7,8},{9,10,11,12}};`

it can also be said that we have defined 3 one dimensional arrays.

```
|  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10 | 11 | 12 |

|----0th element--------|------1st element------|----2nd element-----|
```

### Valid Unvalid Declarations

1. `int x[2][3] = {{1,2,3},{4,5,6}};` 

     - Valid

2. `int x[][3] = {{1,2,3},{4,5,6}};` 

     - Valid. 
     - This syntax is often used when the compiler can infer the first dimension from the number of initializers provided. In this case, since two inner arrays are provided, the compiler infers that the first dimension should be 2. Therefore, it's equivalent to the first declaration.

3. `int x[2][] = {{1,2,3},{4,5,6}};` 

      - Not Valid. 
      - In C, when you omit the size of one dimension, you must specify it for the outermost dimension.  compiler needs to know the size of each dimension in order to allocate memory properly. To understand why this is an issue, consider the initializer list {{1,2,3},{4,5,6}}. The compiler can infer that the first dimension of x should be 2 because there are two sets of curly braces. However, it cannot determine the size of the second dimension from the initializer list alone. In C/C++, arrays are stored contiguously in memory, so the compiler needs to know the size of each dimension to calculate the memory offsets correctly. When you omit the size of the second dimension, the compiler doesn't have enough information to calculate these offsets, resulting in a compilation error.


4. `int x[][] = {{1,2,3},{4,5,6}};`
     - Not Valid.   


#### Program to Find the Transpose of a Matrix

```C
#include <stdio.h>
int main() {
  int a[10][10], transpose[10][10], r, c;
  printf("Enter rows and columns: ");
  scanf("%d %d", &r, &c);

  // asssigning elements to the matrix
  printf("\nEnter matrix elements:\n");
  for (int i = 0; i < r; ++i)
  for (int j = 0; j < c; ++j) {
    printf("Enter element a%d%d: ", i + 1, j + 1);
    scanf("%d", &a[i][j]);
  }

  // printing the matrix a[][]
  printf("\nEntered matrix: \n");
  for (int i = 0; i < r; ++i)
  for (int j = 0; j < c; ++j) {
    printf("%d  ", a[i][j]);
    if (j == c - 1)
    printf("\n");
  }

  // computing the transpose
  for (int i = 0; i < r; ++i)
  for (int j = 0; j < c; ++j) {
    transpose[j][i] = a[i][j];
  }

  // printing the transpose
  printf("\nTranspose of the matrix:\n");
  for (int i = 0; i < c; ++i)
  for (int j = 0; j < r; ++j) {
    printf("%d  ", transpose[i][j]);
    if (j == r - 1)
    printf("\n");
  }
  return 0;
}
```

#### Program to add two matrices

```C
#include <stdio.h>
int main() {
  int r, c, a[100][100], b[100][100], sum[100][100], i, j;
  printf("Enter the number of rows (between 1 and 100): ");
  scanf("%d", &r);
  printf("Enter the number of columns (between 1 and 100): ");
  scanf("%d", &c);

  printf("\nEnter elements of 1st matrix:\n");
  for (i = 0; i < r; ++i)
    for (j = 0; j < c; ++j) {
      printf("Enter element a%d%d: ", i + 1, j + 1);
      scanf("%d", &a[i][j]);
    }

  printf("Enter elements of 2nd matrix:\n");
  for (i = 0; i < r; ++i)
    for (j = 0; j < c; ++j) {
      printf("Enter element b%d%d: ", i + 1, j + 1);
      scanf("%d", &b[i][j]);
    }

  // adding two matrices
  for (i = 0; i < r; ++i)
    for (j = 0; j < c; ++j) {
      sum[i][j] = a[i][j] + b[i][j];
    }

  // printing the result
  printf("\nSum of two matrices: \n");
  for (i = 0; i < r; ++i)
    for (j = 0; j < c; ++j) {
      printf("%d   ", sum[i][j]);
      if (j == c - 1) {
        printf("\n\n");
      }
    }

  return 0;
}
```

#### Multiple Matrices

```C
#include <stdio.h>

// function to get matrix elements entered by the user
void getMatrixElements(int matrix[][10], int row, int column) {

   printf("\nEnter elements: \n");

   for (int i = 0; i < row; ++i) {
      for (int j = 0; j < column; ++j) {
         printf("Enter a%d%d: ", i + 1, j + 1);
         scanf("%d", &matrix[i][j]);
      }
   }
}

// function to multiply two matrices
void multiplyMatrices(int first[][10],
                      int second[][10],
                      int result[][10],
                      int r1, int c1, int r2, int c2) {

   // Initializing elements of matrix mult to 0.
   for (int i = 0; i < r1; ++i) {
      for (int j = 0; j < c2; ++j) {
         result[i][j] = 0;
      }
   }

   // Multiplying first and second matrices and storing it in result
   for (int i = 0; i < r1; ++i) {
      for (int j = 0; j < c2; ++j) {
         for (int k = 0; k < c1; ++k) {
            result[i][j] += first[i][k] * second[k][j];
         }
      }
   }
}

// function to display the matrix
void display(int result[][10], int row, int column) {

   printf("\nOutput Matrix:\n");
   for (int i = 0; i < row; ++i) {
      for (int j = 0; j < column; ++j) {
         printf("%d  ", result[i][j]);
         if (j == column - 1)
            printf("\n");
      }
   }
}

int main() {
   int first[10][10], second[10][10], result[10][10], r1, c1, r2, c2;
   printf("Enter rows and column for the first matrix: ");
   scanf("%d %d", &r1, &c1);
   printf("Enter rows and column for the second matrix: ");
   scanf("%d %d", &r2, &c2);

   // Taking input until
   // 1st matrix columns is not equal to 2nd matrix row
   while (c1 != r2) {
      printf("Error! Enter rows and columns again.\n");
      printf("Enter rows and columns for the first matrix: ");
      scanf("%d%d", &r1, &c1);
      printf("Enter rows and columns for the second matrix: ");
      scanf("%d%d", &r2, &c2);
   }

   // get elements of the first matrix
   getMatrixElements(first, r1, c1);

   // get elements of the second matrix
   getMatrixElements(second, r2, c2);

   // multiply two matrices.
   multiplyMatrices(first, second, result, r1, c1, r2, c2);

   // display the result
   display(result, r1, c2);

   return 0;
}
```