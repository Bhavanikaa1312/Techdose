## Binary Search
###1.Lower and upper bound

```cpp
#include <iostream>
#include <vector>
#include <algorithm> 

using namespace std;

int main() {
    vector<int> arr;  
    int value;        

    int lower = lower_bound(arr.begin(), arr.end(), value) - arr.begin();
    cout << "Lower bound of " << value << " is at index: " << lower << endl;

    int upper = upper_bound(arr.begin(), arr.end(), value) - arr.begin();
    cout << "Upper bound of " << value << " is at index: " << upper << endl;

    return 0;
}


###2.Capacity to ship packages within D days:

```cpp
class Solution {
public:
int findDays(vector<int>& weights,int cap ){
    int load=0;
    int days=1;
    for(int i=0;i<weights.size();i++){
        if(weights[i]+load > cap){
            days+=1;
            load = weights[i];
        }
        else{
            load += weights[i];
        }
    }
    return days;
}
    int shipWithinDays(vector<int>& weights, int days) {
        int low = *max_element(weights.begin(),weights.end());
        int high = accumulate(weights.begin(),weights.end(),0);
        while(low<=high){
            int mid=(low+high)/2;
            int numOfDays = findDays(weights,mid);
            if(numOfDays <= days){
                high = mid-1;
            }
            else{
                low = mid+1;
            }
        }
        return low;
    }
};

###3.Aggressive cows:

class Solution {
public:
int findDays(vector<int>& weights,int cap ){
    int load=0;
    int days=1;
    for(int i=0;i<weights.size();i++){
        if(weights[i]+load > cap){
            days+=1;
            load = weights[i];
        }
        else{
            load += weights[i];
        }
    }
    return days;
}
    int shipWithinDays(vector<int>& weights, int days) {
        int low = *max_element(weights.begin(),weights.end());
        int high = accumulate(weights.begin(),weights.end(),0);
        while(low<=high){
            int mid=(low+high)/2;
            int numOfDays = findDays(weights,mid);
            if(numOfDays <= days){
                high = mid-1;
            }
            else{
                low = mid+1;
            }
        }
        return low;
    }
};


### 4.Painters Partition Problem

int countStudent(vector<int>&nums,int maxpages){
    int student =1;
    long long pagesStudent = 0;
    for(int i=0;i<nums.size();i++){
        if(pagesStudent + nums[i] <= maxpages){
            pagesStudent += nums[i];
        }
        else{
            student += 1;
            pagesStudent = nums[i];
        }
    }
    return student;
}
    int splitArray(vector<int>& nums, int k) {
        int m = nums.size();
        if(k>m) return -1;
        int low= *max_element(nums.begin(),nums.end());
        int high = accumulate(nums.begin(),nums.end(),0);
        while(low<=high){
            int mid = (low+high)/2;
            int student = countStudent(nums,mid);
            if(student > k){
                low = mid+1;
            }
            else{
                high = mid-1;
            }
        }        
        return low;
    }

    int findLargestMinDistance(vector<int> &boards, int k) {
        return splitArray(boards,k);
    }
    
    ### 5.Quick Select - Kth Smallest Element (Row, Column, Row-Column)
    #include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int partition(vector<int>& arr, int low, int high) {
    int pivot = arr[high];
    int i = low;

    for (int j = low; j < high; j++) {
        if (arr[j] <= pivot) {
            swap(arr[i], arr[j]);
            i++;
        }
    }
    swap(arr[i], arr[high]);
    return i;
}

int quickSelect(vector<int>& arr, int low, int high, int k) {
    if (low <= high) {
        int pivotIndex = partition(arr, low, high);

        if (pivotIndex == k) {
            return arr[pivotIndex];
        } else if (pivotIndex > k) {
            return quickSelect(arr, low, pivotIndex - 1, k);
        } else {
            return quickSelect(arr, pivotIndex + 1, high, k);
        }
    }
    return -1;
}

int findKthSmallest(vector<vector<int>>& matrix, int k) {
    vector<int> merged;
    for (const auto& row : matrix) {
        merged.insert(merged.end(), row.begin(), row.end());
    }
    return quickSelect(merged, 0, merged.size() - 1, k - 1);
}

### 6. Garden-worker Problem
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

bool isFeasible(vector<int>& tasks, int workers, int mid) {
    int workerCount = 1, sum = 0;

    for (int task : tasks) {
        if (sum + task > mid) {
            workerCount++;
            sum = task;
            if (workerCount > workers) return false;
        } else {
            sum += task;
        }
    }
    return true;
}

int findMinimumTime(vector<int>& tasks, int workers) {
    int low = *max_element(tasks.begin(), tasks.end());
    int high = accumulate(tasks.begin(), tasks.end(), 0);
    int result = high;

    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (isFeasible(tasks, workers, mid)) {
            result = mid;
            high = mid - 1;
        } else {
            low = mid + 1;
        }
    }
    return result;
}

### 7.Implement Best Meeting Point Problem

#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int minTotalDistance(vector<vector<int>>& grid) {
    vector<int> rows, cols;
    for (int i = 0; i < grid.size(); i++) {
        for (int j = 0; j < grid[0].size(); j++) {
            if (grid[i][j] == 1) {
                rows.push_back(i);
                cols.push_back(j);
            }
        }
    }
    
    sort(rows.begin(), rows.end());
    sort(cols.begin(), cols.end());
    
    int rowMedian = rows[rows.size() / 2];
    int colMedian = cols[cols.size() / 2];
    int totalDistance = 0;
    for (int r : rows) totalDistance += abs(r - rowMedian);
    for (int c : cols) totalDistance += abs(c - colMedian);
    
    return totalDistance;
}

