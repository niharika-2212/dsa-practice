# Problem: Merged two sorted list

- Platform: Leetcode 21
- Link: https://leetcode.com/problems/merge-two-sorted-lists/description/
- Difficulty: Easy
- Tags: Linked List, Recursion

## Problem Statement
You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.


## Example

```
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

## Approach 
- Use merge sort approach
- we already have two sorted list
- set two pointers for each list
- compare values at two pointers
- append the smaller value in new sorted list
- when either of the list ends, insert all elements of other list as it is

### Time complexity
- Time: `O(n+m)` 
- Space: `O(1)`

### Code (C++)
```c++
ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode* final = new ListNode;
        ListNode* head = new ListNode;
        head = final;
        while(list1!=NULL && list2!=NULL){
            if(list1->val < list2->val){
                final->next = list1;
                final=final->next;
                list1 = list1->next;
            }else{
                final->next=list2;
                final=final->next;
                list2 = list2->next;
            }
        }
        while(list1!=NULL){
            final->next=list1;
            final=final->next;
            list1 = list1->next;
        }
        while(list2!=NULL){
            final->next=list2;
            final=final->next;
            list2 = list2->next;
        }
        return head->next;
    }
```
