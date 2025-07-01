# Problem: Reverse linked list

- Platform: Leetcode 206
- Link: https://leetcode.com/problems/reverse-linked-list/description
- Difficulty: Easy
- Tags: Linked list, recursion

## Problem Statement
Given the head of a singly linked list, reverse the list, and return the reversed list.


## Example

```
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

## Approach 
- Iterate over list
- insert elements at head(front) of new list
- return the new list


### Time complexity
- Time: `O(n)` 
- Space: `O(1)`

### Code (C++)
```c++
ListNode* reverseList(ListNode* head) {
        ListNode* prev = NULL;
        ListNode* next_node = NULL;
        while(head!=NULL){
            next_node=head->next;
            head->next = prev;
            prev = head;
            head = next_node;
        }
        head=prev;
        return head;
    }
```
