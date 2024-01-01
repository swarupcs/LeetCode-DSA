## 1752. Check if Array Is Sorted and Rotated



https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/

Given an array nums, return true if the array was originally sorted in non-decreasing order, then rotated some number of positions (including zero). Otherwise, return false.

There may be duplicates in the original array.

Note: An array A rotated by x positions results in an array B of the same length such that A[i] == B[(i+x) % A.length], where % is the modulo operation.


#### Example 1:
```
Input: nums = [3,4,5,1,2]
Output: true
Explanation: [1,2,3,4,5] is the original sorted array.
You can rotate the array by x = 3 positions to begin on the the element of value 3: [3,4,5,1,2].
```

#### Example 2:
```
Input: nums = [2,1,3,4]
Output: false
Explanation: There is no sorted array once rotated that can make nums.
```

#### Example 2:
```
Input: nums = [1,2,3]
Output: true
Explanation: [1,2,3] is the original sorted array.
You can rotate the array by x = 0 positions (i.e. no rotation) to make nums.
```

#### Constraints:
```
1 <= nums.length <= 100
1 <= nums[i] <= 100
```

## Solutions


### Approach
https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/solutions/3781162/optimal-solution-with-explanation/
```

The function check takes a reference to a vector of integers called nums as its input and returns a boolean value indicating whether the array meets the specified conditions.

The variable n is assigned the size of the nums array, representing the number of elements in the array.

The boolean variable rotated is initialized as false. It will be used to keep track of whether the array has been rotated or not.

A loop is used to iterate through each element of the nums array. The loop variable i represents the current index.

Inside the loop, the condition nums[i] > nums[(i+1)%n] is checked. This condition compares the current element with the next element in a circular manner, considering the modulo operation (i+1)%n. If this condition is true, it means that the array is not sorted in non-decreasing order.

If the array is not sorted in non-decreasing order and rotated is already true, it means that we have already detected a rotation earlier, so we can immediately return false as the array does not meet the required conditions.

If the array is not sorted in non-decreasing order and rotated is false, it means that we have detected the first instance of a rotation. We update rotated to true to indicate that a rotation has been found.

If the current element is equal to the next element (nums[i] == nums[(i+1)%n]), it means there are duplicate elements in the array. We can safely ignore them and continue to the next iteration of the loop.

After the loop ends, if we have not encountered a second rotation (i.e., rotated is still true), it means that the array was originally sorted in non-decreasing order and then rotated some number of positions. We return true.

If the loop completes and no rotations were found (i.e., rotated is still false), it means that the array is already sorted in non-decreasing order without any rotations. We also return true in this case.

```

* **Java**

```
class Solution {
    public boolean check(int[] nums) {
        int n = nums.length;
        boolean rotated = false;
        
        for (int i = 0; i < n; i++) {
            if (nums[i] > nums[(i + 1) % n]) {
                if (rotated) {
                    return false;
                }
                rotated = true;
            } else if (nums[i] == nums[(i + 1) % n]) {
                continue;
            }
        }
        
        return true;
    }
}
```