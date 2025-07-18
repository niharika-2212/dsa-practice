# Problem: Maximum Matching of Players With Trainers

- Platform: Leetcode 2410
- Link: https://leetcode.com/problems/maximum-matching-of-players-with-trainers/description/
- Difficulty: Easy
- Tags: Array, two pointers, greedy, sorting

## Problem Statement
You are given a 0-indexed integer array players, where players[i] represents the ability of the ith player. You are also given a 0-indexed integer array trainers, where trainers[j] represents the training capacity of the jth trainer.

The ith player can match with the jth trainer if the player's ability is less than or equal to the trainer's training capacity. Additionally, the ith player can be matched with at most one trainer, and the jth trainer can be matched with at most one player.

Return the maximum number of matchings between players and trainers that satisfy these conditions.


## Example

```
Input: players = [4,7,9], trainers = [8,2,5,8]
Output: 2
Explanation:
One of the ways we can form two matchings is as follows:
- players[0] can be matched with trainers[0] since 4 <= 8.
- players[1] can be matched with trainers[3] since 7 <= 8.
It can be proven that 2 is the maximum number of matchings that can be formed.
```

## Approach 
- sort both arrays
- place two pointers at start of both
- for each player if player capacity <= trainer, move forward both (player is assigned a trainer)
- else move trainer forward (same player can be assigned new trainer)

### Time complexity
- Time: `O(n log n + m log m)`
- Space: `O(1)`

### Code (C++)
```c++
int matchPlayersAndTrainers(vector<int>& players, vector<int>& trainers) {
    sort(players.begin(), players.end());
    sort(trainers.begin(), trainers.end());
    int count=0;
    int i=0, j=0;
    while(i<trainers.size() && j<players.size()){
        if(trainers[i]>=players[j]){
            count++;
            i++;
            j++;
        }else{
            i++;
        }
    }
    return count;
}
```
