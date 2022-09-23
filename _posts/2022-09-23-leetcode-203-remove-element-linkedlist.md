---
layout: post
title: LeetCode 203 Remove Linked List Elements (Java)
---

#### Problem : Easy

[LeetCode](https://leetcode.com/problems/remove-linked-list-elements/):
Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.

<img width="479" alt="image" src="https://user-images.githubusercontent.com/92517160/192067588-728b2c45-f50a-42e1-9678-1f39dc642b33.png">

#### Thought

- I have tried to implement this in C++ before but this i smy first time using Java to solve it.
- Rather than using pointer, Java ListNode has a filed Next as a **reference** to next value in the linked list.
- Useful youtube **link** [#5 Linked List Implementation in Java Part 1 | Data Structures ](https://www.youtube.com/watch?v=SMIq13-FZSE&t=824s)
- Another **useful link** in Chinese from Carl [手把手带你学会操作链表 | LeetCode：203.移除链表元素](https://www.bilibili.com/video/BV18B4y1s7R9/)
- I have tried to understand this data staructure by drawing on the paper with understanding of memory location useage. 
- Using dummy node can keep consistance of treversing to remove target elments from the list. In this case, head will stay the same, instaed dummy and currNode will keep traversing until the end of the list. 
- Hint for this challenge will be returning **dummy.next**;


#### Steps:
- 

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

