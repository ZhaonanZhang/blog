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

- Stack is a perfect data structure for this problem.
- It's to elimanate the the pair(same) charactors in orders.
- Pairing process may concider using stack or queue.


#### Solution: Java

```
class Solution {
    public String removeDuplicates(String s) {
        Deque<Character> deque = new ArrayDeque<>();
        char[] ch = s.toCharArray();
        //check all char in ch, push if deque is empty or deque has no such a char
        for(char c: ch) {
            if (deque.isEmpty() || deque.peek() != c) {
                deque.push(c);
            } else {
                deque.pop(); //if another same char found, pop the first char out too because they are the pair should not exist in result.
            }
        }
        String s1 = "";
        while (!deque.isEmpty()) {
            s1 = deque.pop() + s1;
        }
        return s1;
    }       
}

```


For more instructions head over to the [LeetCode](https://leetcode.com/problems/).
