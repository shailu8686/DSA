# DSA
#include <stdio.h>
int main()
{
 int *p, n, ele, ch, i, pos; // p is pointer to create a dynamic array
 printf("Enter number of elements to create an Array:\t");
 scanf("%d", &n);
 p = malloc(n * sizeof(int)); // use malloc to create a Dynamic array
 printf("Dynamic Array Created.\n");
 printf("Enter %d elements\n ", n);
 for (i = 0; i < n; i++) // Read n the elements to array
 {
 scanf("%d", &p[i]);
 }
 while (1)
 {
 printf("\n 1.Insert\n 2.delete\n 3.display \n 4.Exit\n Enter your
choice:\t");
 scanf("%d", &ch);
 switch (ch)
 {
 case 1:
 printf("\n Enter element & Pos(0 to %d) to insert:\t", n - 1);
 scanf("%d%d", &ele, &pos);
 realloc(p, (n+1) * sizeof(int)); // increase the size of array by 1
 n = n + 1; // update new size
 for (i = n - 1; i >= pos; i--) // Start moving all the elements to the
next positions
 {
 p[i] = p[i - 1];
 }
 p[pos] = ele; // insert the new element at specied position
 break;
 case 2:
 printf("Enter Position(0 to %d) to delete:\t", n - 1);
 scanf("%d", &pos);
 for (i = pos + 1; i < n; i++) // delete the position element by moving
next element of pos to prevvious pos
 {
 p[i - 1] = p[i];
 }
 n = n - 1; // Update the count total elements
 break;
 case 3:
 printf("\n Array Elements Are:\n");
 for (i = 0; i < n; i++)

 {
 printf("%d\t", p[i]);
 }
 break;
 case 4:
 exit(0);
 }
 }
 return 0;
} 

SPARSE MATRIX
#include <stdio.h>
#include <stdlib.h>
#define MAX 100
struct term {
 int row;
 int col;
 int value;
};
struct term sparse[MAX],trans[MAX];
int size; // Total num of values..
void create();
void transpose();
void display(int values,struct term matrix[]);
int main() {
 int choice;
 while(1) {
 printf("\nMenu:\n");
 printf("1. Create Sparse Matrix\n");
 printf("2. Transpose of Sparse Matrix\n");
 // printf(". Display Sparse Matrix\n");
 printf("3. Exit\n");
 printf("Enter your choice: ");
 scanf("%d", &choice);
 switch (choice) {
 case 1:
 create();
 break;
 case 2:
 transpose();
 break;
 case 3:
 exit(0);
 }
 }
 return 0;
}
void create() {
 int matrix[10][10];
 int i,rows,cols,values; // Starting index from 1 since 0 is used for
matrix dimensions
 printf("\nEnter number of Rows,Columns and number of Values :");
 scanf("%d%d%d",&rows,&cols,&values);
 sparse[0].row = rows;
 sparse[0].col = cols;
 sparse[0].value = values; // Initially no non-zero elements
 for(i=1;i<=values;i++)
 {
 printf("\n Enter row,col and value:");
 scanf("%d%d%d",&sparse[i].row,&sparse[i].col,&sparse[i].value);
 }
 display(values,sparse);
}
void transpose() {
 int i,values;
 // trans[0].row = sparse[0].col;
 // trans[0].col = sparse[0].row;
 // trans[0].value = sparse[0].value;
 values=sparse[0].value;
 for(i=0;i<=sparse[0].value;i++)
 {
 trans[i].row=sparse[i].col;
 trans[i].col=sparse[i].row;
 trans[i].value=sparse[i].value;

 }
 display(values,trans);
}
void display(int values,struct term a[]) {
 int i;
 printf("\n\t Row\tColumn\tValue\n");
 for (i = 0; i <= values; i++) {
 printf("a[%d]: %d\t%d\t%d\n",i, a[i].row, a[i].col, a[i].value);
 }
} 
