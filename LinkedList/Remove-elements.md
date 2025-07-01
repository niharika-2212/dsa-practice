# Problem: Remove Linked List Elements

- Platform: Leetcode 203
- Link: https://leetcode.com/problems/remove-linked-list-elements/description
- Difficulty: Easy
- Tags: Linked List, recursion

## Problem Statement
Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.

## Example

```
Input: head = [1,2,6,3,4,5,6], val = 6
Output: [1,2,3,4,5]
```

## Approach 
- store prev value from the start
- iterate over list
- if value is to be removed
- delete that node 

### Time complexity
- Time: `O(n)` 
- Space: `O(1)`

### Code (C++)
```c++
ListNode* removeElements(ListNode* head, int val) {
  ListNode* dummy = (struct ListNode*)malloc(sizeof(struct ListNode));;
  dummy->next=head;
  ListNode* temp = dummy;
  while(temp->next!=NULL){
    if(temp->next->val==val){
      temp->next = temp->next->next;
    }
    else{
      temp = temp->next;
    }
  }
  return dummy->next;
}
```
