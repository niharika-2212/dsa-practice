# Problem: Number of students unable to eat lunch

- Platform: Leetcode 1700 
- Link: https://leetcode.com/problems/number-of-students-unable-to-eat-lunch/description
- Difficulty: Easy
- Tags: array, stack, queue

## Problem Statement
The school cafeteria offers circular and square sandwiches at lunch break, referred to by numbers 0 and 1 respectively. All students stand in a queue. Each student either prefers square or circular sandwiches.

The number of sandwiches in the cafeteria is equal to the number of students. The sandwiches are placed in a stack. At each step:

If the student at the front of the queue prefers the sandwich on the top of the stack, they will take it and leave the queue.
Otherwise, they will leave it and go to the queue's end.
This continues until none of the queue students want to take the top sandwich and are thus unable to eat.

You are given two integer arrays students and sandwiches where sandwiches[i] is the type of the i​​​​​​th sandwich in the stack (i = 0 is the top of the stack) and students[j] is the preference of the j​​​​​​th student in the initial queue (j = 0 is the front of the queue). Return the number of students that are unable to eat.

## Example
```
Input: students = [1,1,0,0], sandwiches = [0,1,0,1]
Output: 0 
Explanation:
- Front student leaves the top sandwich and returns to the end of the line making students = [1,0,0,1].
- Front student leaves the top sandwich and returns to the end of the line making students = [0,0,1,1].
- Front student takes the top sandwich and leaves the line making students = [0,1,1] and sandwiches = [1,0,1].
- Front student leaves the top sandwich and returns to the end of the line making students = [1,1,0].
- Front student takes the top sandwich and leaves the line making students = [1,0] and sandwiches = [0,1].
- Front student leaves the top sandwich and returns to the end of the line making students = [0,1].
- Front student takes the top sandwich and leaves the line making students = [1] and sandwiches = [1].
- Front student takes the top sandwich and leaves the line making students = [] and sandwiches = [].
Hence all students are able to eat.
```

## Approach 
- count number of 1s and 0s in students
- traverse in sandwiches
    - if 1 
        - count1 is not 0, reduce count (student eats)
        - count1 is 0, break - no more people can eat (people who wanted 1 are empty)
    - if 0
        - count0 is not 0, reduce count (student eats)
        - count0 is 0, break - no more people can eat (people who wanted 0 are empty)
- return remaining students(count0+count1)


### Time complexity
- Time: `O(students+sandwiches)` 
- Space: `O(1)`

### Code (C++)
```c++
int countStudents(vector<int>& students, vector<int>& sandwiches) {
    int count1=0, count0=0;
    for(int i=0 ; i<students.size() ; i++){
        if(students[i]==1){
            count1++;
        }else{
            count0++;
        }
    }
    for(int i=0 ; i<sandwiches.size() ; i++){
        if(sandwiches[i]==0 ){
            if(count0==0){
                break;
            }
            count0--;
        }else if(sandwiches[i]==1){
            if(count1==0){
                break;
            }
            count1--;
        }
        
    }
    return count0+count1;
}
```
