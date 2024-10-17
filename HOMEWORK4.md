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

