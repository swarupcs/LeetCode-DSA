## 238. Product of Array Except Self


https://leetcode.com/problems/product-of-array-except-self/


```
Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.
```

#### Example 1:

```
Input: nums = [1,2,3,4]
Output: [24,12,8,6]

```

#### Example 2:
```
Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
```


#### Constraints:
```
2 <= nums.length <= 105
-30 <= nums[i] <= 30
The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.
```

##### Follow up:
```
 Can you solve the problem in O(1) extra space complexity? (The output array does not count as extra space for space complexity analysis.)
```

## Solutions
```
Key Points:

1. We use left array that stores the product of elements(except itself) to the left of each position in the input array arr.
2. The right array stores the product of elements(except itself) to the right of each position in the input array arr.
3. Finally calculates the product of elements by multiplying the corresponding values from the left and right arrays.
4. The resulting array is the answer to the problem.
```

* **Java**

```
class Solution {
    public int[] productExceptSelf(int[] nums) {
        return product(nums);
    }

    public static int[] product(int[] arr) {
		int n = arr.length;
		int[] left = new int[n];
		left[0] = 1;
		for (int i = 1; i < n; i++) {
			left[i] = left[i - 1] * arr[i - 1];
		}

		int[] right = new int[n];
		right[n - 1] = 1;
		for (int i = n - 2; i >= 0; i--) {
			right[i] = right[i + 1] * arr[i + 1];
		}
		
		for(int i=0; i<n; i++) {
			left[i] = left[i] * right[i];
		}
		
		return left;

	}
}


```