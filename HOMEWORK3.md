## Sorting
### 1. Radix Sort Implementation in C++

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int getMax(const vector<int>& arr) {
    int max_val = arr[0];
    for (int num : arr) {
        if (num > max_val) {
            max_val = num;
        }
    }
    return max_val;
}

void countingSort(vector<int>& arr, int exp) {
    int n = arr.size();
    vector<int> output(n);
    int count[10] = {0};

    for (int i = 0; i < n; i++) {
        count[(arr[i] / exp) % 10]++;
    }

    for (int i = 1; i < 10; i++) {
        count[i] += count[i - 1];
    }

    for (int i = n - 1; i >= 0; i--) {
        output[count[(arr[i] / exp) % 10] - 1] = arr[i];
        count[(arr[i] / exp) % 10]--;
    }

    for (int i = 0; i < n; i++) {
        arr[i] = output[i];
    }
}

void radixSort(vector<int>& arr) {
    int max_val = getMax(arr);
    for (int exp = 1; max_val / exp > 0; exp *= 10) {
        countingSort(arr, exp);
    }
}

int main() {
    vector<int> arr = {170, 45, 75, 90, 802, 24, 2, 66};
    radixSort(arr);
    for (int num : arr) {
        cout << num << " ";
    }
    return 0;
}

### 2. Bucket Sort Implementation in C++


 ```cpp

#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

void bucketSort(vector<float>& arr) {
    int n = arr.size();
    vector<vector<float>> buckets(n);

    for (int i = 0; i < n; i++) {
        int idx = n * arr[i];
        buckets[idx].push_back(arr[i]);
    }

    for (int i = 0; i < n; i++) {
        sort(buckets[i].begin(), buckets[i].end());
    }

    int index = 0;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < buckets[i].size(); j++) {
            arr[index++] = buckets[i][j];
        }
    }
}

int main() {
    vector<float> arr = {0.897, 0.565, 0.656, 0.1234, 0.665, 0.3434};
    bucketSort(arr);
    for (float num : arr) {
        cout << num << " ";
    }
    return 0;
}


### 3. Cycle Sort Implementation in C++

```cpp

#include <iostream>
#include <vector>
using namespace std;

void cycleSort(vector<int>& arr) {
    int n = arr.size();
    for (int cycle_start = 0; cycle_start < n - 1; cycle_start++) {
        int item = arr[cycle_start];
        int pos = cycle_start;

        for (int i = cycle_start + 1; i < n; i++) {
            if (arr[i] < item) {
                pos++;
            }
        }

        if (pos == cycle_start) continue;

        while (item == arr[pos]) pos++;
        swap(item, arr[pos]);

        while (pos != cycle_start) {
            pos = cycle_start;
            for (int i = cycle_start + 1; i < n; i++) {
                if (arr[i] < item) {
                    pos++;
                }
            }
            while (item == arr[pos]) pos++;
            swap(item, arr[pos]);
        }
    }
}

int main() {
    vector<int> arr = {1, 8, 3, 9, 10, 10, 2, 4};
    cycleSort(arr);
    for (int num : arr) {
        cout << num << " ";
    }
    return 0;
}

### 4.Wiggle Sort (LeetCode)

```cpp

#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

void wiggleSort(vector<int>& nums) {
    for (int i = 0; i < nums.size() - 1; i++) {
        if ((i % 2 == 0 && nums[i] > nums[i + 1]) ||
            (i % 2 == 1 && nums[i] < nums[i + 1])) {
            swap(nums[i], nums[i + 1]);
        }
    }
}

int main() {
    vector<int> nums = {3, 5, 2, 1, 6, 4};
    wiggleSort(nums);
    for (int num : nums) {
        cout << num << " ";
    }
    return 0;
}

### 5. Dutch National Flag Problem (LeetCode)

#include <iostream>
#include <vector>
using namespace std;

void sortColors(vector<int>& nums) {
    int low = 0, mid = 0, high = nums.size() - 1;
    while (mid <= high) {
        switch (nums[mid]) {
            case 0:
                swap(nums[low++], nums[mid++]);
                break;
            case 1:
                mid++;
                break;
            case 2:
                swap(nums[mid], nums[high--]);
                break;
        }
    }
}

int main() {
    vector<int> nums = {2, 0, 2, 1, 1, 0};
    sortColors(nums);
    for (int num : nums) {
        cout << num << " ";
    }
    return 0;
}






