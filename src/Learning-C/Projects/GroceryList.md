# Grocery List Management System

```C
#include <stdio.h>

struct item 
{
    int ID;
    char name[50];
    float price;
    int quantity;
};

struct item* readGroceryList(int count) 
{
    struct item* gItems = (struct item*)malloc(sizeof(struct item) * count);
    for(int i = 0; i < count; i++) 
    {
        gItems[i].ID = i + 1;
        printf("Enter the details for item %d: \n", i + 1);
        printf("Name:");
        scanf("%s", gItems[i].name);
        printf("Price:");
        scanf("%f", &gItems[i].price);
        printf("Quantity:");
        scanf("%d", &gItems[i].quantity);
    }
    return gItems;
}

void printGroceryList(struct item* gItems, int count) 
{
    printf("\n");
    for(int i = 0; i < count; i++) 
    {
        printf("Item ID: %d, ", gItems[i].ID);
        printf("Name: %s, ", gItems[i].name);
        printf("Price: %f, ", gItems[i].price);
        printf("Quantity: %d\n", gItems[i].quantity);
    }
}

struct item findItem(int qVal, struct item* gItems, int count) 
{
    int index = -1;
    for(int i = 0; i < count; i++) 
    {
        if(gItems[i].quantity == qVal) 
        {
            index = i;
            return gItems[index];
        }
    }
    struct item emptyItem;
    emptyItem.ID = -1;
    return emptyItem;
}

struct item findMaxPriceItem(struct item* gItems, int count) 
{
    int maxIndex = -1;
    int maxPrice = -1;
    for(int i = 0; i < count; i++) 
    {
        if(gItems[i].price > maxPrice) 
        {
            maxPrice = gItems[i].price;
            maxIndex = i;
        }
    }
    return gItems[maxIndex];
}

int main() 
{
    int num_q;
    printf("Enter the number of unique grocery items in the store - ");
    scanf("%d", &num_q);
    struct item* gItems_main = readGroceryList(num_q);
   
    printGroceryList(gItems_main, num_q);

    int qVal;
    printf("\n Enter the quantity of the item you wish to find - ");
    scanf("%d", &qVal);
    struct item fItem = findItem(qVal, gItems_main, num_q);
    if(fItem.ID == -1) {
        printf("Item not found!\n");
    } else {
        printf("The item found with quantity %d is:\n", qVal);
        printf("ID: %d, Name = %s, Price = %f\n", fItem.ID, fItem.name, fItem.price);
    }

    struct item maxItem = findMaxPriceItem(gItems_main, num_q);
    printf("\nThe item with maximum price is: \n");
    printf("Item ID: %d, ", maxItem.ID);
    printf("Name: %s, ", maxItem.name);
    printf("Price: %f, ", maxItem.price);
    printf("Quantity: %d\n", maxItem.quantity);
}
```
