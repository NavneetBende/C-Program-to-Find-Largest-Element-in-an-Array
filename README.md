# C-Program-to-Find-Largest-Element-in-an-Array

Largest element in an array in C
Today, we will learn largest element in an array in C. We will do this by first taking the value of the first element in the variable max.

Then we will compare with remaining elements of the array and store the value if another larger number is found in this array. This will go on array_size-1 times and the program ends.

Largest element in an array in C
Methods discussed in this post
Method 1: Simple iterative solution
Method 2: Top-Down recursive approach
Method 3: Bottom-Up recursive approach
Method 1 Working:-
For a user-defined input num:-

Assign max = arr[0]
Linearly traverse through the whole array
Whenever you encounter a larger element (arr[i] > max)
Update max, max = arr[i]
Largest element in an array in C
Run
// C Program to find largest element in an array
#include<stdio.h>

int getLargest(int arr[], int len)
{
    // assign first array element as largest
    int max = arr[0];
    
    // linearly search for the largest element
    for(int i=1; i max)
            max = arr[i];
    }
    
    return max;
    
}
int main()
{
    int arr[] = {20, 5, 35, 40, 10, 50, 15};
    
    // get the length of the array
    int len = sizeof(arr)/sizeof(arr[0]);    
    
    printf("The Largest element is: %d", getLargest(arr, len));
}
// Time complexity: O(N)
// Space complexity: O(N)
Output
Largest: 50
Related Pages
Method 2 (Using Recursion)
This method requires you to know recursion in C. 

Call a function : getLargest(int arr[], int i, int len, int max)

With initial call up values as : getLargest(arr, 0, len, arr[0])
Initially passing max as arr[0]
Initially passing ‘i’ as 0
In each recursive call check if current array element is greater than max
If it is then assign max = arr[i]
Move to the next recursive call trying to do the same thing for the next array index
Stop when you’ve read all elements and reach the bounds of array and print max value
C Program (Method 2)
Run
// C Program to find largest element in an array
// using top down recursive approach
#include <stdio.h>


void getLargest(int arr[], int i, int len, int max)
{
    // base case, when last element was read in previous recursion 
    if(i >= len){
        printf("Largest: %d",max);
        return;
    }
    
    if(arr[i] > max)
        max = arr[i];
    
    getLargest(arr, i+1, len, max);
}
int main()
{
    int arr[] = {20, 5, 35, 40, 10, 50, 15};
    
    // get the length of the array
    int len = sizeof(arr)/sizeof(arr[0]);    
    
    getLargest(arr, 0, len, arr[0]);
    
    return 0;
}
// Time complexity: O(N)
// Space complexity: O(1)
// Auxilary space complexity : O(N) due to function call stack
Output
Largest: 50
Method 3 (Using Recursion)
This method requires you to know recursion in C. 

Call a function : maximum(int arr[], int i, int end)

With initial call up values as maximum(arr, 0, end)
Initially passing end as the index of last array element
Initially passing ‘i’ as 0
Recursively reach iteration where reading 2nd last element
Find larger between 2nd last and last array elements
And return the result to max value of the previous recursive iteration
In each of the remaining recursive callups find the largest b/w current array index element and current max value
Pass final max value from last recursive callup to main and print
C Program (Method 3)
Run
// C Program to find largest element in an array
// using bottom up recursive approach
#include <stdio.h>

int maximum(int arr[], int i, int end)
{
    int max;
    
    // when we reach 2nd last array element
    // return the larger b/w last & 2nd last elements
    if(i == end-1)
        return (arr[i] > arr[i + 1]) ? arr[i] : arr[i + 1];

    max = maximum(arr, i + 1, end);

    return (arr[i] > max) ? arr[i] : max;
}

int main()
{
    int arr[] = {25, 100, 35, 20, 10, 80};
    
    // storing the index of end array element 
    // end = 5 : arr[5] = 80 (the end element)
    int end = sizeof(arr)/sizeof(arr[0]) - 1;    

    int max;

    max = maximum(arr, 0, end);

    printf("Largest: %d\n", max);

    return 0;
}
// Time complexity: O(N)
// Space complexity: O(1)
// Auxilary space complexity : O(N) due to function call stack
Output
Largest: 100
How to find the 2nd largest?
We can also have a look on how. to find the 2nd largest item in array here below-

Method 1
Run
#include <stdio.h>
#include <limits.h>


int secLargest(int arr[], int n)
{
    // assigning first element as largest temporarily
    int largest = arr[0];
    
    // we find the largest element here
    for (int i=0; i < n; i++){ if(arr[i] > largest)
            largest = arr[i];
    }
    
    // temporarily assinging max value
    int sec_largest = INT_MIN;
    
    // finding second largest here
    for (int i=0; i < n; i++) 
{ 
if(arr[i] != largest && arr[i] > sec_largest)
            sec_largest = arr[i];
    }

    return sec_largest;
    
}
int main()
{
    int arr[] = {25, 40, 35, 20, 10, 80};
    
    // get the length of the array
    int len = sizeof(arr)/sizeof(arr[0]);    
    
    printf("The 2nd largest : %d",secLargest(arr, len));
}
// Time complexity: O(N)
// Space complexity: O(N)
Output
The 2nd largest : 40
Method 2
Run
#include <stdio.h>
#include <limits.h>


void get2ndLargest(int arr[], int n)
{
    int i, first, second;
 
    /* The array must have 2 or more items */
    if (n < 2)
    {
        printf("Array has lesser than 2 items");
        return;
    }
 
    first = second = INT_MIN;
    for (i = 0; i < n ; i++) 
    { 
        /* If the current array element is larger than the first 
        then update both first and second */ 
        if (arr[i] > first)
        {
            second = first;
            first = arr[i];
        }
 
        /* If arr[i] lies between first and second
        then update second */
        else if (arr[i] > second && arr[i] != first)
            second = arr[i];
    }
    if (second == INT_MAX)
        printf("We don't have 2nd largest item in array\n");
    else
        printf("The 2nd largest : %d",second);
}
 
int main()
{
    int arr[] = {30, 20, 60, 40, 10, 100};
    int len = sizeof(arr)/sizeof(arr[0]);

    get2ndLargest(arr, len);

    return 0;
}
// Time Complexity : O(N)
// Space Complexity : O(N)
Output
The 2nd largest : 40
