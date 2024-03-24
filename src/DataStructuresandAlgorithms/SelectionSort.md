# Selection Sort

simple sorting algorithm that works by repeatedly selecting the minimum element from the unsorted portion of the array and swapping it with the first element of the unsorted portion. 

```c
#include <stdio.h>
void selectionSort(int arr[], int n) {
    int i, j, min;
    for (i = 0; i < n-1; i++) {
        min = i; // minimum element in unsorted array

        for (j = i+1; j < n; j++) {
            if (arr[j] < arr[min]) {
                min = j;
            }
        }

        // swap the minimum element with the first element of the unsorted array
        if (min != i) {
            int temp = arr[i];
            arr[i] = arr[min];
            arr[min] = temp;
        }
    }
}


