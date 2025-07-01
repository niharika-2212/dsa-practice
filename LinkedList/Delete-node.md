# Problem: Delete node in a linked list

- Platform: Leetcode 237
- Link: https://leetcode.com/problems/delete-node-in-a-linked-list/description
- Difficulty: medium
- Tags: Linked List

## Problem Statement
There is a singly-linked list head and we want to delete a node node in it.

You are given the node to be deleted node. You will not be given access to the first node of head.

All the values of the linked list are unique, and it is guaranteed that the given node node is not the last node in the linked list.

Delete the given node. Note that by deleting the node, we do not mean removing it from memory. We mean:

The value of the given node should not exist in the linked list.
The number of nodes in the linked list should decrease by one.
All the values before node should be in the same order.
All the values after node should be in the same order.


## Example

```
Input: head = [4,5,1,9], node = 5
Output: [4,1,9]
Explanation: You are given the second node with value 5, the linked list should become 4 -> 1 -> 9 after calling your function.
```

## Approach 
- copy value of node next to the node
- delete the next node
- so for `4->5->1->9` copy 1 in place of 5 and delete 1 list becomes `4->1->9`


### Time complexity
- Time: `O(1)` 
- Space: `O(1)`

### Code (C++)
```c++
void deleteNode(ListNode* node) {
  node->val = node->next->val;
  node->next = node->next->next;
}
```
