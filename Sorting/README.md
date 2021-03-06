## STL sort() and comparators
1. sorting an array in ascending order: ``` sort(arr,arr+n); ``` , where ``` n = sizeof(arr)/sizeof(arr[0]);```
2. sorting a vector in ascending order: ``` sort(arr.being(),arr.end()); ```
3. sorting in descending order: ``` sort(arr, arr+n, greater<int>()); ```
4. Using comparator:  The function comp returns true, when a should be found before b in the sorted array. <br>
-> For ascending : if a<b return 1 <br>
-> For descending: if a<b return -1
```
struct ob{
  int low;
  int high;
};

bool comparator_function( ob a, ob b ){
  return a.low < b.low;   //For ascending
  reutrn a.low > b.low;   // For descending
}

sort(arr,arr+n,comparator_function);
```


## Bubble Sort
With each subsequent iteration "k", kth largest element is being placed at its position. 
1. Naive approach -> 2 for loops -> takes O(n^2) everytime
2. Stop when the array is sorted -> make use of flags to check if there were any swaps during an iteration.
  - Worst Case: When the array is reverse sorted : O(n*n)
  - Average Case: O(n*n)
  - Best Case: O(n)
  -Auxillary space: O(1) ->inplace sorting
  
3. Recursive Bubble sort {[Recursive Bubble sort](https://www.geeksforgeeks.org/recursive-bubble-sort/)}
  - Base case => Only one element present in the array 
  - No advantage over the iterative approaches.
  ```
  void BubbleSortRecursive(vector<int> a,int n){
    if(n==1)
      return;
    for(int i=0;i<n-1;i++){
      if(a[i] > a[i+1])
        swap(a[i],a[i+1]);
    }
    return BubbleSortRecursive(a,n-1);
  }
  ```

## Quick sort
- Divide and conquer method
- Inplace, cache friendly sorting algorithm as it has good locality of reference when used for arrays.
1. Time taken by quicksort can be given by  T(n) = T(k) + T(n-k-1) + O(n) , where k is the number of elements smaller than the pivot
2. Worst case : When partition picks smallest or the largest number as pivot ->  T(n) = T(0) + T(n-1) + O(n)  -> O(N*N)
3. Best case: When partition always picks the middle element as pivot -> T(n) = 2T(n/2) + O(n) -> O(NlogN)
4. Average case : O(NlogN)
For more reference [Click here](https://www.geeksforgeeks.org/quick-sort/)
```
#include <iostream>
#include <bits/stdc++.h>
#include<vector>
#include<string>
using namespace std;

void swap(int* a, int* b){
    int temp = *a;
    *a = *b;
    *b = temp;
}

int partition(int a[],int low, int high){
    int index = low; // position for the pivot 
    for(int i=low;i<high;i++){
        if(a[i]<a[high]){
            swap(&a[i],&a[index]);
            index++;
        }
    }
    swap(&a[index],&a[high]);
    return index;
}


void quicksort(int a[],int low,int high){
    if(low<high){
    int index = partition(a,low,high);
    
    quicksort(a,low,index-1);
    quicksort(a,index+1,high);
}
}


void print(int arr[],int size){
     int i;  
    for (i = 0; i < size; i++)  
        cout << arr[i] << " ";  
    cout << endl; 
}
int main() {
   int arr[] = {9,6,4,8,6};  
    int n = sizeof(arr) / sizeof(arr[0]);  
    quicksort(arr, 0, n - 1);  
    cout << "Sorted array: \n";  
    print(arr, n);  
    return 0;  
}
```
