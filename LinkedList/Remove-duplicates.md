# Problem: Remove duplicates from sorted list

- Platform: Leetcode 83
- Link: https://leetcode.com/problems/remove-duplicates-from-sorted-list/description
- Difficulty: Easy
- Tags: Linked List

## Problem Statement
Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.

## Example

```
Input: head = [1,1,2,3,3]
Output: [1,2,3]
```

## Approach 
- iterate over linked list
- check if prev val equals current value
- if yes skip else insert in new list


### Time complexity
- Time: `O(n)` 
- Space: `O(1)`

### Code (C++)
```c++
ListNode* deleteDuplicates(ListNode* head) {
        ListNode * final=new ListNode;
        ListNode * head1=new ListNode;
        ListNode * prev=new ListNode;
        prev = head;
        if(head!=NULL){
            head=head->next;
        }
        head1=final;
        while(head!=NULL){
            if(prev->val!=head->val){
                final->next=prev;
                final=final->next;
                prev = head;
                head=head->next;
            }else{
                prev = head;
                head=head->next;
            }
        }
        final->next = prev;
        final=final->next;
        return head1->next;
    }
```
