# Problem: Palindrome Linked List

- Platform: Leetcode 234
- Link: https://leetcode.com/problems/palindrome-linked-list/description
- Difficulty: Easy
- Tags: Linked List, two pointers, stack, recursion

## Problem Statement
Given the head of a singly linked list, return true if it is a palindrome or false otherwise.


## Example

```
Input: head = [1,2,2,1]
Output: true
```

## Approach 1
- reverse linked list in new list
- compare each value of both list, if equal return true, else false

### Time complexity
- Time: `O(n)` 
- Space: `O(1)`

### Code (C++)
```c++
bool isPalindrome(ListNode* head) {
        ListNode* head1 = NULL;
        ListNode* head2 = head;
        while(head!=NULL){
            ListNode* new_node = new ListNode;
            new_node->val = head->val;
            new_node->next = head1;
            head1 = new_node;
            head=head->next;
        }
        while(head2!=NULL){
            if(head2->val!=head1->val){
                return false;
            }
            head2=head2->next;
            head1=head1->next;
        }
        return true;
    }
```
