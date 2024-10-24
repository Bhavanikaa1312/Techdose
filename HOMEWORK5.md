### Array

### 1.Merge 2 Sorted Arrays Without Using Extra Space

#include <iostream>
#include <algorithm>
using namespace std;

void mergeSortedArrays(int arr1[], int n, int arr2[], int m) {
    int i = n - 1, j = 0;
    while (i >= 0 && j < m) {
        if (arr1[i] > arr2[j]) {
            swap(arr1[i], arr2[j]);
            i--;
            j++;
        } else {
            break;
        }
    }
    sort(arr1, arr1 + n);  // Sort the first array
    sort(arr2, arr2 + m);  // Sort the second array
}

### 2.Check Whether the Given Array Is in Sorted Order

#include <iostream>
using namespace std;

bool isSorted(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        if (arr[i] < arr[i - 1]) {
            return false;
        }
    }
    return true;
}

### 3.Count No. of Subarrays With At Most K Unique Characters


