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
#include <iostream>
#include <vector>
#include <unordered_map>
using namespace std;

int subarraysWithAtMostKUnique(vector<int>& arr, int k) {
    int start = 0, count = 0;
    unordered_map<int, int> freq;
    
    for (int end = 0; end < arr.size(); end++) {
        freq[arr[end]]++;
        
        while (freq.size() > k) {
            freq[arr[start]]--;
            if (freq[arr[start]] == 0)
                freq.erase(arr[start]);
            start++;
        }
        count += (end - start + 1);
    }
    return count;
}

### 4.Find Number of Subarrays Where max(SA) - min(SA) <= k

#include <iostream>
#include <vector>
#include <deque>
using namespace std;

int countSubarraysWithDiffLessThanK(vector<int>& arr, int k) {
    int start = 0, count = 0;
    deque<int> minDeque, maxDeque;
    
    for (int end = 0; end < arr.size(); end++) {
        while (!minDeque.empty() && arr[minDeque.back()] >= arr[end])
            minDeque.pop_back();
        while (!maxDeque.empty() && arr[maxDeque.back()] <= arr[end])
            maxDeque.pop_back();
        
        minDeque.push_back(end);
        maxDeque.push_back(end);
        
        while (arr[maxDeque.front()] - arr[minDeque.front()] > k) {
            start++;
            if (minDeque.front() < start) minDeque.pop_front();
            if (maxDeque.front() < start) maxDeque.pop_front();
        }
        count += (end - start + 1);
    }
    return count;
}

### 5.First Negative Number in Every Window of Size K

#include <iostream>
#include <vector>
#include <deque>
using namespace std;

vector<int> firstNegativeInEveryWindow(vector<int>& arr, int k) {
    deque<int> dq;
    vector<int> result;
    
    for (int i = 0; i < arr.size(); i++) {
        if (arr[i] < 0)
            dq.push_back(i);
        
        if (i >= k - 1) {
            if (!dq.empty() && dq.front() < i - k + 1)
                dq.pop_front();
            result.push_back(dq.empty() ? 0 : arr[dq.front()]);
        }
    }
    return result;
}

### 6.Variable Window Problems

### (i) Largest/Smallest Subarray Where sum <= S or sum >= S

#include <iostream>
#include <vector>
using namespace std;

int largestSubarrayWithSumLessThanOrEqualToS(vector<int>& arr, int S) {
    int start = 0, sum = 0, maxLength = 0;

    for (int end = 0; end < arr.size(); end++) {
        sum += arr[end];
        
        while (sum > S) {
            sum -= arr[start];
            start++;
        }
        maxLength = max(maxLength, end - start + 1);
    }
    return maxLength;
}

### (ii) Largest Subarray with K Distinct Characters

#include <iostream>
#include <vector>
#include <unordered_map>
using namespace std;

int largestSubarrayWithKDistinct(vector<int>& arr, int K) {
    unordered_map<int, int> freq;
    int start = 0, maxLength = 0;

    for (int end = 0; end < arr.size(); end++) {
        freq[arr[end]]++;
        
        while (freq.size() > K) {
            freq[arr[start]]--;
            if (freq[arr[start]] == 0)
                freq.erase(arr[start]);
            start++;
        }
        maxLength = max(maxLength, end - start + 1);
    }
    return maxLength;
}

### (iii) Length of Largest Subarray with No Repeating Characters

#include <iostream>
#include <unordered_map>
using namespace std;

int longestSubarrayWithNoRepeatingChars(string s) {
    unordered_map<char, int> lastSeen;
    int start = 0, maxLength = 0;

    for (int end = 0; end < s.size(); end++) {
        if (lastSeen.find(s[end]) != lastSeen.end())
            start = max(start, lastSeen[s[end]] + 1);
        
        lastSeen[s[end]] = end;
        maxLength = max(maxLength, end - start + 1);
    }
    return maxLength;
}

### (iv) Minimum Window Substring

#include <iostream>
#include <string>
#include <unordered_map>
using namespace std;

string minWindowSubstring(string s, string t) {
    unordered_map<char, int> freqT;
    for (char c : t) freqT[c]++;
    
    unordered_map<char, int> window;
    int start = 0, minLength = INT_MAX, matchCount = 0, minStart = 0;
    
    for (int end = 0; end < s.size(); end++) {
        char c = s[end];
        if (freqT.find(c) != freqT.end()) {
            window[c]++;
            if (window[c] == freqT[c]) matchCount++;
        }
        
        while (matchCount == freqT.size()) {
            if (end - start + 1 < minLength) {
                minLength = end - start + 1;
                minStart = start;
            }
            if (freqT.find(s[start]) != freqT.end()) {
                window[s[start]]--;
                if (window[s[start]] < freqT[s[start]]) matchCount--;
            }
            start++;
        }
    }
    
    return minLength == INT_MAX ? "" : s.substr(minStart, minLength);
}

### 7.Practice Kadane's Algorithm and Moore's Voting Algorithm

### Kadane’s Algorithm:

#include <iostream>
#include <vector>
using namespace std;

int kadaneAlgorithm(vector<int>& arr) {
    int maxSoFar = arr[0], currentMax = arr[0];
    
    for (int i = 1; i < arr.size(); i++) {
        currentMax = max(arr[i], currentMax + arr[i]);
        maxSoFar = max(maxSoFar, currentMax);
    }
    return maxSoFar;
}

### Moore’s Voting Algorithm:

#include <iostream>
#include <vector>
using namespace std;

int mooreVotingAlgorithm(vector<int>& arr) {
    int candidate = -1, count = 0;

    for (int num : arr) {
        if (count == 0) {
            candidate = num;
            count = 1;
        } else if (num == candidate) {
            count++;
        } else {
            count--;
        }
    }

    // Verify the candidate
    count = 0;
    for (int num : arr) {
        if (num == candidate) count++;
    }

    return (count > arr.size() / 2) ? candidate : -1;
}
