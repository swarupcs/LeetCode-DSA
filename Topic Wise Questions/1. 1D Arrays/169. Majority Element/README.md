## 169. Majority Element


https://leetcode.com/problems/majority-element/


```
Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.
```

#### Example 1:

```
Input: nums = [3,2,3]
Output: 3

```

#### Example 2:
```
Input: nums = [2,2,1,1,1,2,2]
Output: 2
```


#### Constraints:
```
n == nums.length
1 <= n <= 5 * 104
-109 <= nums[i] <= 109
```

## Solutions

### Key Points:

```
1. Initialize Variables:
a) Set element and count to 0.
2. Moore's Voting Algorithm:
a) Iterate through nums.
b) If count is 0, update element to the current element.
c) If the current element is element, increment count; otherwise, decrement count.
3. Check for Majority Element:
a) Count occurrences of element in nums.
b) If its count exceeds half the array length, return element; otherwise, return -1.

```


* **Java**

```

public class Solution {
    public int majorityElement(int[] nums) {
        int n = nums.length;
        int element = 0;
        int count = 0;
        // Applying the Moore's Voting Algorithm
        for(int i=0; i<n; i++) {
            if(count == 0) {
                element = nums[i];
                count = 1;
            } else if(element == nums[i]) {
                count++;
            } else {
                count--;
            }
        }

        // Checking if the stored element is the majority element
        int countElement = 0;
        for(int i=0; i<n; i++) {
           if(nums[i] == element) {
            countElement++;
           }
        }
        if(countElement > (n/2)) {
            return element;
        }
        return -1;
    }   
}

```