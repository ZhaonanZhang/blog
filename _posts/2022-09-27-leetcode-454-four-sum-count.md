
---
layout: post
title: LeetCode 454. 4Sum II (Java)
---

#### Problem : Medium

[LeetCode]https://leetcode.com/problems/4sum-ii/):
Given four integer arrays nums1, nums2, nums3, and nums4 all of length n, return the number of tuples (i, j, k, l) such that:

0 <= i, j, k, l < n
nums1[i] + nums2[j] + nums3[k] + nums4[l] == 0


###### Image from Leetcode
<img width="614" alt="image" src="https://user-images.githubusercontent.com/92517160/192650829-8493d145-f041-4c45-85d3-e6e6c6b382e9.png">



#### Thought

- Knowing what data structure to use in problems is a very important skill.
- This is a typical Hash challenge. When do we consider a hash? Answer would be when we need to check if an element has appeared in a list or if it exists in a list. 
- To pay attention in this problem is four arrays are having same length n, and it accepts repetitive results. 
- We can use simple math knowlege to break down this problem from 4 individual numbers sum to 2 two numsbers sum. For example, if we want A+B+C+D == 0, then we can work out sum1= A+B then sum2 = C+D, then evaluate if sum1 + sum2 ==0.


#### pseudocode:
- Check if the head node exsits, if not return head;
- Initialise a new node: dummy node
- Dummy will point to the head
- Initialise another node as **currNode = dummy**
- Using while loop (Condition is currNode.next != null) to loop until find the target value
- When loop finishes(when currNode point to null), return **dummy.next**

#### Solution: Java

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */

class Solution {
    public ListNode removeElements(ListNode head, int val) {

        if(head == null){
            return head;
        }

        ListNode dummy = new ListNode();
        dummy.next = head;
        ListNode currNode = dummy;

        while (currNode.next != null ){
            if(currNode.next.val == val) {
                currNode.next = currNode.next.next;

            }
            else{
                currNode = currNode.next;
            }
        }
        return dummy.next;    
    }
}
```


For more instructions head over to the [LeetCode](https://leetcode.com/).

