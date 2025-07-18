# Problem: Container with most water

- Platform: Leetcode 11
- Link: https://leetcode.com/problems/container-with-most-water/description
- Difficulty: Easy
- Tags: Two pointers, greedy

## Problem Statement
You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.


## Example
![alt text](container.png)
```
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.
```

## Approach 1
- using loops
- calculate volume for each pair in array
- if volume more than prev, store the new volume

### Time complexity
- Time: `O(n**2)` 
- Space: `O(1)`

### Code (C++)
```c++
int maxArea(vector<int>& height) {
    int water=0;
    for(int i=0 ; i<height.size() ; i++){
        int count=0;
        for(int j=i ; j<height.size() ; j++){
            if(height[i]>height[j]){
                int area=count*height[j];
                if(water<area){
                    water=area;
                }
                count++;    
            }
            else{
                int area=count*height[i];
                if(water<area){
                    water=area;
                }
                count++;    
            }
        }
       }
    return water;
}
```

## Approach 2
- using two pointers
- pointer at both ends
- calculate volume, if more than prev, store new volume
- then move forward the pointer with less height

### Time complexity
- Time: `O(n)` 
- Space: `O(1)`

### Code (C++)
```c++
int maxArea(vector<int>& height) {
    int i=0,j=height.size()-1;
    int vol=0;
    while(i<=j){
        if(height[i]<height[j]){
            int temp=(j-i)*height[i];
            if(temp>vol){
                vol=temp;
            }
            i++;
        }else{
            int temp = (j-i)*height[j];
            if(temp>vol){
                vol=temp;
            }
            j--;
        }
    }
    return vol;
}
```



