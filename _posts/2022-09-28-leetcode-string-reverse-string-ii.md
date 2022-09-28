---
layout: post
title: 541 Reverse String II (Java)
---

#### Problem : Easy

[LeetCode](https://leetcode.com/problems/reverse-string-ii//):
Given a string s and an integer k, reverse the first k characters for every 2k characters counting from the start of the string.
If there are fewer than k characters left, reverse all of them. If there are less than 2k but greater than or equal to k characters, then reverse the first k characters and leave the other as original.

 
###### Image from Leetcode
<img width="561" alt="image" src="https://user-images.githubusercontent.com/92517160/192899272-8f04d31a-7e50-4dd1-8f53-34ebf8bd3e0d.png">


#### Thought
- Java String is immutable so convert given Sting to a charArray will be a good solution.
- When loop through this charArray, beacuse we need to swap the first k elements of the 2k substring, so define how int i increase in the loop is the key for best performance. It doesn't always have to be i++;
- Then to define when pointer i reach the closer end of the array by thinking (start+k)-1 and how far end pointer is away from the updated i. (illustrion may talk better)
<img width="937" alt="image" src="https://user-images.githubusercontent.com/92517160/192901928-9a3f96d7-202e-470b-8a0d-de4a1c0083e0.png">



#### Solution: Java

```
//题目的意思其实概括为 每隔2k个反转前k个，尾数不够k个时候全部反转

class Solution {
    public String reverseStr(String s, int k) {
        char[] sArray = s.toCharArray();
        for (int i = 0; i < sArray.length; i += 2 * k) {
            int start = i;
            //这里是判断尾数够不够k个来取决end指针的位置
            int end = Math.min(sArray.length - 1, start + k - 1);
            while (start < end) {
                char temp = sArray[start];
                sArray[start] = sArray[end];
                sArray[end] = temp;
                start++;
                end--;
            }
        }
        return new String(sArray);
    }      
}
```


For more instructions head over to the [LeetCode](https://leetcode.com/).

