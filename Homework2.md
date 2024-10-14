1. In-place vs. Out-of-place Sorting Algorithms
In-place Sorting Algorithms

Bubble Sort: In-place, Stable
Insertion Sort: In-place, Stable
Selection Sort: In-place, Unstable
Quick Sort: In-place, Unstable
Out-of-place Sorting Algorithms

Merge Sort: Out-of-place, Stable
Heap Sort: In-place, Unstable
Radix Sort: Out-of-place, Stable

2.Iterative Merge Sort in C++:
#include <iostream>
#include <vector>
using namespace std;

void merge(vector<int>& arr, int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;

    vector<int> L(n1), R(n2);
    for (int i = 0; i < n1; i++)
        L[i] = arr[left + i];
    for (int i = 0; i < n2; i++)
        R[i] = arr[mid + 1 + i];

    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k++] = L[i++];
        } else {
            arr[k++] = R[j++];
        }
    }
    while (i < n1) {
        arr[k++] = L[i++];
    }
    while (j < n2) {
        arr[k++] = R[j++];
    }
}

void iterativeMergeSort(vector<int>& arr, int n) {
    for (int curr_size = 1; curr_size < n; curr_size *= 2) {
        for (int left_start = 0; left_start < n - 1; left_start += 2 * curr_size) {
            int mid = min(left_start + curr_size - 1, n - 1);
            int right_end = min(left_start + 2 * curr_size - 1, n - 1);
            merge(arr, left_start, mid, right_end);
        }
    }
}

int main() {
    vector<int> arr = {12, 11, 13, 5, 6, 7};
    int n = arr.size();

    iterativeMergeSort(arr, n);

    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}

3.Code to Merge Two Sorted Lists in C++

#include <iostream>
#include <vector>
using namespace std;

vector<int> mergeSortedLists(const vector<int>& list1, const vector<int>& list2) {
    vector<int> merged;
    int i = 0, j = 0;

    while (i < list1.size() && j < list2.size()) {
        if (list1[i] <= list2[j]) {
            merged.push_back(list1[i]);
            i++;
        } else {
            merged.push_back(list2[j]);
            j++;
        }
    }

    while (i < list1.size()) {
        merged.push_back(list1[i]);
        i++;
    }

    while (j < list2.size()) {
        merged.push_back(list2[j]);
        j++;
    }

    return merged;
}

int main() {
    vector<int> list1 = {1, 3, 5, 7};
    vector<int> list2 = {2, 4, 6, 8};

    vector<int> result = mergeSortedLists(list1, list2);

    for (int num : result) {
        cout << num << " ";
    }

    return 0;
}
