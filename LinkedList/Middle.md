# Problem: Middle of the linked list

- Platform: Leetcode 876
- Link: https://leetcode.com/problems/middle-of-the-linked-list/description
- Difficulty: Easy
- Tags: linked list, two pointers

## Problem Statement
Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.

## Example

```
Input: head = [1,2,3,4,5]
Output: [3,4,5]
Explanation: The middle node of the list is node 3.
```

## Approach 
- count number of elements in list
- calculate middle
- go to the middle node
- return that node

### Time complexity
- Time: `O(n)` 
- Space: `O(1)`

### Code (C++)
```c++
ListNode* middleNode(ListNode* head) {
        int count=0;
        int mid = 0;
        ListNode* middle = new ListNode;
        ListNode* head1 = new ListNode;
        head1=head;
        while(head!=NULL){
            head=head->next;
            count++;
        }
        if(count%2!=0){
            mid = (count-1)/2;
        }else{
            mid = count/2;
        }
        for(int i=0 ; i<mid ; i++){
            if(head1!=NULL){
                head1=head1->next;
            }
        }
        middle = head1;
        return middle;
    }
```
