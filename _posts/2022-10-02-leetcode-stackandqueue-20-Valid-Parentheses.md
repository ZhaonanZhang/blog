---
layout: post
title: 20. Valid Parentheses (Java)
---

#### Problem : Easy

[LeetCode](https://leetcode.com/problems/valid-parentheses/):
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.

<img width="841" alt="image" src="https://user-images.githubusercontent.com/92517160/193479373-030dd277-c723-4f47-86a1-ca1bc143d73a.png">



#### Thought

Try the four steps for this problem:
- **Simulation**: Simulate the running of the problem on a paper.

- **Rules**: Try to summarize the general rules and characteristics of the topic.
Through the above simulation, the following three characteristics can be concluded:
1. ( and ), [ and ], { and } are in one-to-one correspondence, and it is invalid if they cannot be paired
2. For valid parentheses, its partial sub-expressions are still valid parentheses, such as { [ ( ) ]} , if the partial sub-expressions are invalid, then the whole is invalid
3. If some sub-expressions establish a pairing relationship and are valid parentheses, they will not affect the whole after they are eliminated.
4. Strings of odd length are always invalid.


- **Match**: Find data structures and algorithms that match these characteristics.
The whole process is divided into two steps, one is pairing and the other is elimination.

Pairing process, ( and ), [ and ], { and }.

The process of elimination is carried out from the inside to the outside. First, it is judged whether some sub-expressions (inside) can be eliminated, and then whether the whole expression (outside) can be eliminated. However, the process of traversal is carried out from outside to inside, and the state needs to be saved. , the characteristics of the first-in-last-out stack meet the requirements.

- **Boundaries**: Consider special cases.
The length of the string is odd.



#### Solution: Java

```
class Solution {
    public boolean isValid(String s) {
            Stack<Character> stack = new Stack<Character>();
            for (char c : s.toCharArray()) {
                if (c == '(')
                    stack.push(')');
                else if (c == '{')
                    stack.push('}');
                else if (c == '[')
                    stack.push(']');
                else if (stack.isEmpty() || stack.pop() != c)
                    return false;
            }
            return stack.isEmpty();       
    }
}

```


For more instructions head over to the [LeetCode](https://leetcode.com/).
