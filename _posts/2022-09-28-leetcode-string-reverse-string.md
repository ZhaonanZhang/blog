---
layout: post
title: LeetCode 209 Minimum Size Subarray Sum (Java)
---

#### Problem : Medium

[LeetCode](https://leetcode.com/problems/minimum-size-subarray-sum/):
Given an array of positive integers nums and a positive integer target, return the minimal length of a contiguous subarray [numsl, numsl+1, ..., numsr-1, numsr] of which the sum is greater than or equal to target. If there is no such subarray, return 0 instead.
#### Thought

To solve this problem, first of all is to understand the given constraint: 
- All the integers in nums are **positive**.
- Return a **contiguous subarray**.
- Whenever it's about looking for a contiguous subarray with all non negtive arrays, sliding window method should **flag up**. 
- Sliding window is a special **two pointers methods**.
- I found a youtube video is **particularly useful** with great explanation and useful whiteboarding graphs: [TECH DOSE](https://www.youtube.com/watch?v=S6Xg-0uaODc)
- This is my first time trying to implement sliding window method. It's fun!!!
#### Steps:
-Update soon

#### Solution: Java

```
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int left = 0, right = 0, sum = 0;
        int shortest = Integer.MAX_VALUE; //set min to the max value then reduce it
        while(right< nums.length){
            sum += nums[right]; //add current element to sum by moving right pointer

            if(sum>= target){
                //check if current sum >= target
                // move left pointer to squeeze the window until sum < target (to find the first shortest window)
                while (sum >= target){
                    sum -= nums[left];
                    left ++;
                }
                //Below updated window would be (right -left +1) + 1 (the one before )
                shortest = Math.min(shortest, right-left+2);
            }
            right ++;
        }
        return shortest == Integer.MAX_VALUE ? 0: shortest;
       
    }
}

```


For more instructions head over to the [LeetCode](https://leetcode.com/problems/search-insert-position/).
