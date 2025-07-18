# Problem: Minimum Average of Smallest and Largest Elements

- Platform: Leetcode 3194
- Link: https://leetcode.com/problems/minimum-average-of-smallest-and-largest-elements/description
- Difficulty: Easy
- Tags: Array, two pointer, sorting

## Problem Statement
You have an array of floating point numbers `averages` which is initially empty. You are given an array `nums` of n integers where n is even.

You repeat the following procedure `n / 2` times:

Remove the smallest element, `minElement`, and the largest element `maxElement`, from nums.
Add `(minElement + maxElement) / 2` to `averages`.
Return the minimum element in `averages`.


## Example

```
Input: nums = [7,8,3,4,15,13,4,1]
Output: 5.5
Explanation:
step	nums	                averages
0	    [7,8,3,4,15,13,4,1]	    []
1	    [7,8,3,4,13,4]	        [8]
2	    [7,8,4,4]	            [8,8]
3	    [7,4]	                [8,8,6]
4	    []	                    [8,8,6,5.5]
The smallest element of averages, 5.5, is returned.
```

## Approach 1
- make two functions for calculating max and min index in array
- iterate n/2 times
    - find `max` and `min` in array
    - calculate average of these and store in `averages`
    - delete `max` and `min` elements
- at end return `min` in `averages` 


### Time complexity
- Time: `O(n**2)` 
- Space: `O(n)`

### Code (C++)
```c++
class Solution {
public:
    int minElement(vector<int>& nums){
        int min=nums[0],index=0;
        for(int i=0 ; i<nums.size() ; i++){
            if(min>nums[i]){
                min=nums[i];
                index=i;
            }
        }
        return index;
    }
    int maxElement(vector<int>& nums){
        int max=nums[0],index=0;
        for(int i=0 ; i<nums.size() ; i++){
            if(max<nums[i]){
                max=nums[i];
                index=i;
            }
        }
        return index;
    }
    double minimumAverage(vector<int>& nums) {
        vector<double>averages(0);
        int n=nums.size()/2;
        for(int i=0 ; i<n ; i++){
            int minindex=minElement(nums);
            int e1 = nums[minindex];
            nums.erase(nums.begin() + minindex);
            int maxindex=maxElement(nums);
            int e2 = nums[maxindex];
            nums.erase(nums.begin() + maxindex);
            double sum=e1+e2;
            double avg = sum/2;
            averages.push_back(avg);
            
        }
        double min=averages[0];
        for(int i=0 ;i<averages.size() ; i++){
            if(min>averages[i]){
                min=averages[i];
            }
        }
        return min;
    }
};
```

## Approach 2
- sort the array,
- iterate for n/2, so the min element is at i and max at n-i-1
- calculate average and insert in array
- move forward

### Time complexity
- Time: `O(n)` 
- Space: `O(1)`

### Code (C++)
```c++
double minimumAverage(vector<int>& nums) {
    vector<double>averages(0);
    int n=nums.size();
    sort(nums.begin(), nums.end());
    for(int i=0 ; i<n/2 ; i++){
                int sum=(nums[i] + nums[n - i - 1]);
            double avg = sum / 2;
            averages.push_back(avg);
            cout << avg << endl;
    }
    double min=averages[0];
    for(int i=0 ;i<averages.size() ; i++){
        if(min>averages[i]){
            min=averages[i];
        }
    }
    return min;
}
```
