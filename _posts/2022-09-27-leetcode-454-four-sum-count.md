
---
layout: post
title: LeetCode 454 Four Sum Count (Java)
---

#### Problem : Medium

[LeetCode](https://leetcode.com/problems/4sum-ii/):
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
- if a is an element from nums1, b is an element from nums2, b is an element from nums3, d is an element from nums4;
- Set up a new HashMap, key will be sum of a+b, and value will be the times they exists ;
- Loop through nums1 and nums2, to moniter the key and value and save them in the HashMap;
- Calculate the sum of c+d, and search through the map to see if 0-(c+d) exists, and count along.



#### Solution: Java

```

class Solution {
    public int fourSumCount(int[] nums1, int[] nums2, int[] nums3, int[] nums4) {
        int result = 0;
        Map<Integer, Integer> firstMap = new HashMap();

        for(int i : nums1){
            for(int j: nums2){
                int temp1= i+j;
                if(firstMap.containsKey(temp1)){
                    firstMap.put(temp1, firstMap.get(temp1) +1 );
                }
                else{
                    firstMap.put(temp1, 1);
                }

            }
        }

        for(int k: nums3){
            for(int l: nums4){
                int temp2 = k+l;
                if(firstMap.containsKey(0-temp2)){
                    result= result+ firstMap.get(0-temp2);
                }
            }
        }

        return result;
    }
}
```


For more instructions head over to the [LeetCode](https://leetcode.com/).

