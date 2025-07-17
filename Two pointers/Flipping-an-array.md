# Problem:

- Platform: Leetcode 832
- Link: https://leetcode.com/problems/flipping-an-image/description
- Difficulty: Easy
- Tags: Array, Two Pointers, Bit Manipulation, Matrix, Simulation

## Problem Statement
Given an n x n binary matrix image, flip the image horizontally, then invert it, and return the resulting image.

To flip an image horizontally means that each row of the image is reversed.

For example, flipping [1,1,0] horizontally results in [0,1,1].
To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0.

For example, inverting [0,1,1] results in [1,0,0].

## Example

```
Input: image = [[1,1,0],[1,0,1],[0,0,0]]
Output: [[1,0,0],[0,1,0],[1,1,1]]
Explanation: First reverse each row: [[0,1,1],[1,0,1],[0,0,0]].
Then, invert the image: [[1,0,0],[0,1,0],[1,1,1]]
```

## Approach 
- create a new matrix vector
- for each row: first flip horizontally
    - reverse that row using two pointers
- then invert
    - convert 0 to 1 and 1 to 0
- push in new matrix

### Time complexity
- Time: `O(n*m)` 
- Space: `O(n*m)`

### Code (C++)
```c++
vector<vector<int>> flipAndInvertImage(vector<vector<int>>& image) {
	vector<vector<int>> final (0);
	for(int p=0 ; p<image.size() ; p++){
		vector<int>temp=image[p];
		int i=0;
		int j=temp.size()-1;
		while(i<=j){
			// swap
			int t=temp[i];
			temp[i]=temp[j];
			temp[j]=t;
			i++;
			j--;
		}
		for(int k=0 ; k<temp.size() ; k++){
			if(temp[k]==0){
				temp[k]=1;
			}else{
				temp[k]=0;
			}
		}
		final.push_back(temp);
	}
	return final;
}
```
