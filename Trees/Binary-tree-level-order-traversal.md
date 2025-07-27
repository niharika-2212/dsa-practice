# Problem: Binary Tree Level Order Traversal

- Platform: Leetcode 102
- Link: https://leetcode.com/problems/binary-tree-level-order-traversal/description
- Difficulty: Easy
- Tags: tree, BFS, binary tree

## Problem Statement
Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

## Example
```
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[9,20],[15,7]]
```

## Approach
- create a queue
- insert root in queue
- initial level is 0
- for each level calculate queue size -> that will be level size
- pop the front node and store it
- push in result vector for that level
- push in queue if current node is not empty for left and right
- repeat till queue becomes empty


### Time complexity
- Time: `O(n)` 
- Space: `O(h)`

### Code (C++)
```c++
vector<vector<int>> levelOrder(TreeNode* node) {
    vector<vector<int>>res;
    if(node==NULL){
        return {};
    }
    queue<TreeNode*> q;
    q.push(node);
    int currlevel=0;
    while(!q.empty()){
        int levelsize = q.size();
        res.push_back({});
        for(int i=0 ; i<levelsize ; i++){
            TreeNode* curr = q.front();
            q.pop();
            res[currlevel].push_back(curr->val);
            if(curr->left!=NULL){
                q.push(curr->left);
            }
            if(curr->right!=NULL){
                q.push(curr->right);
            }
        }
        currlevel++;
    }
    return res;
}
```
