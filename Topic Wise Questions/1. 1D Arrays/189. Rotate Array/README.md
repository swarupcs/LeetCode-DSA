## 136. Single Number


https://leetcode.com/problems/rotate-array/


```
Given an integer array nums, rotate the array to the right by k steps, where k is non-negative.
```


#### Example 1:

```
Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]

```

#### Example 2:
```
Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```



#### Constraints:
```
1 <= nums.length <= 105
-231 <= nums[i] <= 231 - 1
0 <= k <= 105
```

## Solutions

```
Key Points:
1. Let n is length of the array.
2. For Rotate Array problem first use reversal algorihm(using two pointers approach) for 0 to (n - k-1). 
3. Again use reversal algorithm for (n-k) to (n-1).
4. And for last time use reversal algorithm for 0 to (n-1).
```
* **Java**

```
class Solution {
    public void rotate(int[] nums, int k) {
        RotateArray(nums,k);
    }

    public static void RotateArray(int[] arr, int k) {
		int n = arr.length;
		k = k % n;
		Reverse(arr, 0, n-k-1);	// Reverse first part	
		Reverse(arr, n-k, n-1);	//Reverse second part	
		Reverse(arr, 0, n-1);	//Reverse whole array
		
	}
	
	public static void Reverse(int[] arr, int i, int j) {
		while(i<j) {
			int temp = arr[i];
			arr[i] = arr[j];
			arr[j] = temp;
			i++;
			j--;
		}
	}
}


```