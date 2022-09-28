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
- Then to define when pointer i reach the closer end of the array by thinking (i+k)-1 and how far end pointer is away from the updated i. (illustrion may talks better)
<img width="937" alt="image" src="https://user-images.githubusercontent.com/92517160/192901928-9a3f96d7-202e-470b-8a0d-de4a1c0083e0.png">


#### Pseudocode (single pointer):
- Example original inked list: **Node1-> Node2-> Node3-> Node4-> Node5**
- Initialise a dummy head, and dummy should point to the head. **dummyHead->Node1-> Node2-> Node3-> Node4-> Node5**
- Initialise a pointer, currNode, starting position at dummy.
- When to stop move currNode? Consider the **size** of the list (number of nodes in the list)
-       A: size is even: currNode stops 2 nodes before the tail (That's the last pair of the Nodes): currNode.next.next = null;
-       B: size is odd: currNode stops 1 nodes before the tail(There is not enough node to pair): currNode.next = null; 
- In a while loop (Meet both A&&B loop will break) 
- To swap the first pair. 
**First**, Setup a temp to mark the Node1(currNode.next) and set up a temp1 to mark the Node3(currNode.next.next)
**Second**, make dummyHead point to Node2, then Node2 point to Node1, lastly make Node1 point to Node3. **dummyHead->Node2-> Node1-> Node3-> Node4-> Node5**
- In the loop, move the pointer(currNode to right 2 Nodes).
- Return dummyHead.next

#### Solution: Java

```
//LeetCode 24. Swap Nodes in Pairs
//Given a linked list, swap every two adjacent nodes and return its head.
// You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

// dummyNode -> Node1 -> Node2 -> Node3 -> Node4...
//dummyNode -> Node2 -> Node1 -> Node3 -> Node4
// algorithm is  : dummy point to 2, then 2 point to 1, then 1 point to 3; 

import com.leetcode.linkedlist.ListNode;

public class SwapPairs {
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


        // two pointer methods (using preNode and head as two pointers, preNode is dummyNode, head is Node1)
//        ListNode preNode = dummyHead;
//        while(preNode.next != null && preNode.next.next != null){
//            ListNode tempNode = head.next.next; // Here use only 1 tempNode to mark Node3;
//
//            preNode.next = head.next; // head.next is now Node2, so this is to preNode point to Node2; so dummy point to 2
//            head.next.next = head; //head.next now is Node2, so make Node2.next to head(which is Node1); so 2 point to 1
//            head.next = tempNode; // so 1 point to 3;
//
//            preNode = head;  // move pointer preNode to right 2 position
//            head = head.next; //move head to right 1 position; preNode and head is next to each other;

//        }

        return dummyHead.next;
    }
}
```


For more instructions head over to the [LeetCode](https://leetcode.com/).

