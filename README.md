# consecutive-numbs
finds consecutive numbers in arrays
Project 2, IT Program Design
1. Write a program merge.c that include the following function:
void merge(int n, int a1[], int a2[], int a3[]);

that has a parameter as an integer array a1[] of length n and another parameter an integer
array a2[] of length n. The function merges the contents of the two integer arrays a1 and a2 to
a3. Thus, if a1[] contains the values -9, 16, 0, 2, and a2[] contains 1, 3, 5, 4, then make a3 equal
to -9, 1, 16, 3, 0, 5, 2, 4. Nothing is returned.
In the main function, ask the user to enter the length of the arrays, declare the arrays, read in
the values for the two arrays, and call the merge function to compute the third array. The main
function should display the result of the third array.
Enter the length of the array: 3
Enter the elements of the first array: 3 4 9
Enter the elements of the second array: 7 2 1
Output:
The output array is: 3 7 4 2 9 1
2. Write a program range.c that include the following functions.
int consecutive(int a[], int n);
int inRange(int a[], int n, int low, int high);
The consecutive function tests whether the integer array has three consecutive numbers
with the same value. The function returns 1 if there are three consecutive numbers with the
same value and return 0 if not. Assumes that the array has at least three elements;
The inRange function compares elements of the array with low and high, returns 1 if all the
elements of the array are in the range (inclusive) and returns 0 if there is element in the array
that are not in the range.
In the main function, ask the user to enter the length of the array, declare the array with the
length, read in the values for the array and low and high, and call the two functions. The main
function should display the result.
Sample run #1:
Enter the length of the array: 5
Enter the elements of the array: 3 4 4 4 9
Enter low and high: 2 9
Output:
There are three consecutive numbers with the same value in the
array.
All numbers are in the range.
Sample run #2:
Enter the length of the array: 5
Enter the elements of the array: 3 7 4 4 1
Enter low and high: 2 9
Output:
The array does not contain three consecutive numbers with the
same value.
There are elements in the array that are not in the range.
Before you submit
1. Compile both programs with –Wall. –Wall shows the warnings by the compiler. Be sure
it compiles on the student cluster with no errors and no warnings.
 gcc -Wall merge.c
gcc –Wall range.c
2. Be sure your Unix source file is read & write protected. Change Unix file permission on
Unix:
chmod 600 merge.c
chmod 600 range.c
3. Test the second program with the shell script try_sets and try_barcode on Unix:
chmod +x try_merge
./try_merge
chmod +x try_range
./try_range
4. Submit merge.c and range.c on Canvas.
Grading
Total points: 100 (50 point each problem)
1. A program that does not compile will result in a zero.
2. Runtime error and compilation warning 5%
3. Commenting and style 15%
4. Functionality 80%
 Functions are implemented as required.
Programming Style Guidelines
The major purpose of programming style guidelines is to make programs easy to read and
understand. Good programming style helps make it possible for a person knowledgeable in the
application area to quickly read a program and understand how it works.
1. Your program should begin with a comment that briefly summarizes what it does. This
comment should also include your name.
2. In most cases, a function should have a brief comment above its definition describing
what it does. Other than that, comments should be written only needed in order for a
reader to understand what is happening.
3. Variable names and function names should be sufficiently descriptive that a
knowledgeable reader can easily understand what the variable means and what the
function does. If this is not possible, comments should be added to make the meaning
clear.
4. Use consistent indentation to emphasize block structure.
5. Full line comments inside function bodies should conform to the indentation of the code
where they appear.
6. Macro definitions (#define) should be used for defining symbolic names for numeric
constants. For example: #define PI 3.141592
7. Use names of moderate length for variables. Most names should be between 2 and 12
letters long.
8. Use underscores to make compound names easier to read: tot_vol or total_volumn is
clearer than totalvolumn.


//merge.c stores inputs into 2 arrays and then add them in a third array using a function by Hassan Baraka 
#include <stdio.h>
 
//declare the function merge
void merge(int n, int a1[], int a2[],  int a3[]);
 
int main() {
  int a_1[100], a_2[100], length, element_a_1 = 0, element_a_2 = 0, a_3[200];

 // revieve length of the two arrays
  printf("Enter the length of the array: ");
  scanf("%d", &length);

 // recieve elements of array one
  printf("Enter the elements of the fisrt %d array: ", element_a_1);
  for (element_a_1 = 0; element_a_1 < length; element_a_1++) {
    scanf("%d", &a_1[element_a_1]);
  }
 
  // recieve elements of array 2
 
  printf("Enter the elements of the second %d array: ", element_a_2);
  for (element_a_2 = 0; element_a_2 < length; element_a_2++) {
    scanf("%d", &a_2[element_a_2]);
  }

// call function 
  merge(length, a_1, a_2, a_3);

// display merged array
printf("After merging the two arrays: \n");
for(element_a_1 = 0; element_a_1 < length*2; element_a_1++)
{
printf("%d\t", a_3[element_a_1]);
}
  return 0;
}
 
// function definition
void merge(int n, int a1[], int a2[], int a3[]) 
{

// merge the two arrays
int elm_a_1, arrays_length = n;
for(elm_a_1 = 0; elm_a_1 < arrays_length; elm_a_1++)
{
a3[elm_a_1] = a1[elm_a_1];
}

int merged_length = arrays_length+arrays_length;
int elm_a_3;
for(elm_a_1 = 0, elm_a_3 = arrays_length; elm_a_3 < merged_length && elm_a_1 < arrays_length; elm_a_1++, elm_a_3++)
{
a3[elm_a_3] =  a2[elm_a_1];
}

}


/*range.c recieve numbers from user & test if there is 3 consecutive numbers w/ the same value.
 * also see if all of the numbers in the range of two numbers that the user will provide later.*/

#include <stdio.h>

//declare functions
int consecutive (int a[], int n);
int inRange(int a[], int n, int low, int high);

int main(void)
{

//declare variables
	int array[100], range_array [2], length, element = 0, a = 0, b = 0, c = 0;

//recieve length of the array
printf("Enter %d array length: ", length);
scanf("%d", &length);

//input element of array

printf("Please enter elements %d of array: ", array[element]);
for(element = 0; element < length; element++)
{
scanf("%d", & array[element]);
}
//ask user to input range
printf("Enter %d low and high: ", range_array[2]);
for(element = 0; element < 2; element++)
{
scanf("%d", &range_array[2]);
}

//call consecutive function
consecutive(array, length);

//call inRange
inRange(array, length, range_array[0], range_array[1]);

//check if there is consecutive numbers

for(a = 0, b = a+1, c = b+1; a < length && b < length && c < length; a++, b++, c++)

if(((array[a] == array[b]) && (array[a] = array[c])))

printf("There are three consecutive numbers with the same value in the array.\n");

else
printf("The array does not contain three consecutive numbers with the same value.\n");

       
//check if elements are in range

for(a = 0; a < length; a++)
{
if(((range_array[0] <= array[a]) && (range_array[1] <= array[a])))
{
printf("All numbers are in range.\n");
}
else
printf("There are elements in array that are not in the range.\n");
}

return 0;
}

//define consecutive function
int consecutive(int a[], int n)
{
// test weather the array has three consecutive numbers
int i;
for(i = 0; i < n; i++)

if(((a[i] == a[i+1]) && (a[i] == a[i+2])))

return 1;


else

return 0;
return 0;
}
//define inRange function
int inRange(int a[], int n, int low, int high)
{ 
n = 2;
int range_array[2] = {[0] = low, [1] = high};
// check if elements in range
 int i;
for(i = 0; i < n; i++)
{

if((range_array[0] <= i && range_array[1] <= i))
{
return 1;
}

else

return 0;
}
return 0;

}
