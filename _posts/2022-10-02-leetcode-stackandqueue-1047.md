---
layout: post
title: LeetCode 1047. Remove All Adjacent Duplicates In String (Java)
---

#### Problem : Easy

[LeetCode](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/):
You are given a string s consisting of lowercase English letters. A duplicate removal consists of choosing two adjacent and equal letters and removing them.

We repeatedly make duplicate removals on s until we no longer can.

Return the final string after all such duplicate removals have been made. It can be proven that the answer is unique.

<img width="841" alt="image" src="https://user-images.githubusercontent.com/92517160/193479373-030dd277-c723-4f47-86a1-ca1bc143d73a.png">



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
