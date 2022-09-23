---
layout: post
title: LeetCode 203 Remove Linked List Elements (Java)
---

#### Problem : Easy

[LeetCode](https://leetcode.com/problems/remove-linked-list-elements/):
Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.

<img width="479" alt="image" src="https://user-images.githubusercontent.com/92517160/192067588-728b2c45-f50a-42e1-9678-1f39dc642b33.png">

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

