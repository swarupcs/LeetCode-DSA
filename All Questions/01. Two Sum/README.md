## 01.Two Sum

https://leetcode.com/problems/two-sum/description/

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.



#### Example 1:
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

#### Example 2:
```
Input: nums = [3,2,4], target = 6
Output: [1,2]

```
#### Example 3:
```
Input: nums = [3,3], target = 6
Output: [0,1]
 ```

#### Constraints:
```
2 <= nums.length <= 104
-109 <= nums[i] <= 109
-109 <= target <= 109
Only one valid answer exists.
```

# Solutions

* **Java**

```
import java.util.*;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        //Array to store result
        int[] result = new int[2];
        //This map will store the difference and the corresponding index
        Map<Integer, Integer> map = new HashMap<>();
        //Traverse the entire array
        for(int i =0; i<nums.length; i++) {
            //if we seen the current element before then we have already encountered the other number of pair
            if(map.containsKey(nums[i])) {
                //index of the current element
                result[0] = i;
                //index of the other element of the pair
                result[1] = map.get(nums[i]);
            }
            //if we have not seen the current before, it means we have not yet encountered any number of the pair
             else {
                // Save the difference of the target and the current element
                // with the index of the current element
                map.put(target - nums[i], i);
            }
           
        }
         return result;
    }
}

```