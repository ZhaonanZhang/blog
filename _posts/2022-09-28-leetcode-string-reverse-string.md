---
layout: post
title: LeetCode 344 Reverse String (Java)
---

#### Problem : Easy

[LeetCode](https://leetcode.com/problems/reverse-string/):
Write a function that reverses a string. The input string is given as an array of characters s.
You must do this by modifying the input array in-place with O(1) extra memory.

<img width="575" alt="image" src="https://user-images.githubusercontent.com/92517160/192897669-17027a3e-8b98-4c1c-8b57-d1e1fba1e8d7.png">


#### Thought

- This an easy problem if using two pointers (indexing);
- One pointer from the start of the string ( left) , One from the end of the string (right) , both traversing to the middle and swapping the char along the way.
- The key point will be when do we stop swapping the front element with the back element. Either using while loop, condition will be while **(left <right)**, here doesn't have to consider left == right because when they meet, there is no need to swap. Or using for loop, condition will be **(int i< length/2-1)**. 


#### Solution: Java

```
class Solution {
    public void reverseString(char[] s) {
        int l = 0;
        int r = s.length-1;
        for(int i=0; i<s.length/2 ; i++){
            char temp = s[l];
            s[l] = s[r];
            s[r] = temp;
            l++;
            r--;
        }
    }
}

```


For more instructions head over to the [LeetCode](https://leetcode.com/problems/search-insert-position/).
