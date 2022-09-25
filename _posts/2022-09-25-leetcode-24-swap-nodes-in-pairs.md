---
layout: post
title: LeetCode 24 Swap Nodes in Pairs (Java)
---

#### Problem : Medium

[LeetCode](https://leetcode.com/problems/swap-nodes-in-pairs/):
Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)


###### Image from Leetcode
<img width="467" alt="image" src="https://user-images.githubusercontent.com/92517160/192166352-4e42c12e-3c47-4fef-ba10-9505b34a1605.png">



#### Thought
- 1, There are two methods to solve this problem which is setting up single pointer or two pointers. Single pointer method is slightly easier to understand. Please see the comments in nodes which indicating both methods.
- 2, Consider first: Do I need a dummy head? Do I need a pointer(currNode)? How to find the Nodes I want to operate on?
- 3, REMEMBER: the pointer is always point to the previous node where the target Node is. In this case, I need to swap pairs, therefore, using two pointer is possible. 
- 4, So where(currNode) pointer should start or what's it initial position shoule be? Well, we are operating on the Head node and the Node after as a pair, so we'd better set up a Dummy head and the pointer should point to the Dummy Head too (as the reason been explained from previous thought).
- 5, Next, how do we swap ONE pair of nodes? Using a pen and paper to illustrate the process can be very useful.
- 6, After successfully swap a pair, how do we move the pointer to next pair? And how many position should it move? Should we use a loop?
- 7, Lastly, consider the retuen value. Go back t the question to make sure return the correct type. 
- 8, For this problem, swaping the Nodes but not updating the value of the Nodes, this is means just need to updating the linking pointers.
- 5, Useful youtube **link** [#5 Linked List Implementation in Java Part 1 Data Structures ](https://www.youtube.com/watch?v=SMIq13-FZSE&t=824s)
- Another **useful link** in Chinese from Carl [手把手带你学会操作链表](https://www.bilibili.com/video/BV1YT411g7br/?spm_id_from=333.788)
- I have tried to understand this data staructure by drawing on the paper with understanding of memory location usesage. 
- Using dummy node can keep consistance of treversing to remove target elments from the list. In this case, head will stay the same, instaed dummy and currNode will keep traversing until the end of the list. 
- Hint for this challenge will be returning **dummy.next**;


#### Steps:
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

//dummyNode -> Node1 -> Node2 -> Node3 -> Node4...
//dummyNode -> Node2 -> Node1 -> Node3 -> Node4
//algorithem is  : dummy point to 2, then 2 point to 1, then 1 point to 3;
class Solution {
    public ListNode swapPairs(ListNode head) {
        ListNode dummyHead = new ListNode(-1);
        dummyHead.next = head;
        // single pointer methods(using currNode as a pointer)
        ListNode currNode = dummyHead;
        while(currNode.next != null && currNode.next.next != null){
            ListNode temp = currNode.next; //temp point/to mark to Node1 (headNode)
            ListNode temp1 = currNode.next.next.next; // temp1 point to/to mark Node 3;

            currNode.next = temp.next; //currNode point to Node2; so dummy point to 2
            currNode.next.next = temp; //Node2(after position update, now at the head) point to temp(previous Node1), so 2 point to 1
            temp.next = temp1; // Node1(after position update) point to temp1(which is previous Node3);

            currNode = currNode.next.next; //move currNode right 2 nodes(position);
        }
        return dummyHead.next;
    }
}
```


For more instructions head over to the [LeetCode](https://leetcode.com/).

