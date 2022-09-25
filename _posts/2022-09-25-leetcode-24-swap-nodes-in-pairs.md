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
- 1, There are **two methods** to solve this problem which is setting up **single pointer or two pointers**. Single pointer method is slightly easier to understand. Please see the comments in nodes which indicating both methods.
- 2, Consider first: Do I need a dummy head? Do I need a pointer(currNode)? How to find the Nodes I want to operate on?
- 3, **REMEMBER: the pointer is always point to the previous node where the target Node is.** In this case, we need to swap Nodes pairs, therefore, using two pointer is possible. 
- 4, So where(currNode) pointer should start or what's it initial position shoule be? Well, we are operating on the Head node and the Node after as a pair, so we'd better set up a Dummy head and **the pointer(currNode) should point to the Dummy Head too** (as the reason been explained from previous thought).
- 5, Next, how do we swap ONE pair of nodes? Using a pen and paper to illustrate the process can be very useful.
- 6, After successfully swap a pair, how do we move the pointer to next pair? And how many position should it move? Should we use a loop?
- 7, Lastly, consider the retuen value. Go back to the question to make sure the correct type has been returned. 
- 8, For this problem, swaping the Nodes but not updating the value of the Nodes. This means we just need to updating the linking pointers.

- **useful link** in Chinese from Carl [帮你把链表细节学清楚 两两交换链表中的节点](https://www.bilibili.com/video/BV1YT411g7br/?spm_id_from=333.788)


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

