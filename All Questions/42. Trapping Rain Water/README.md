## 42. Trapping Rain Water


https://leetcode.com/problems/trapping-rain-water/


```
Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.
```

![alt text](image.png)
#### Example 1:

```
Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.

```

#### Example 2:
```
Input: height = [4,2,0,3,2,5]
Output: 9
```


#### Constraints:
```
n == height.length
1 <= n <= 2 * 104
0 <= height[i] <= 105
```

## Solutions

```
Key Points:
1. calculate the Left max Array, which stores the maximum height encountered from the left side for each position in the elevation map(the concept is called prefix max).
2. Next calculate the Right max array, which stores the maximum height encountered from the right side for each position in the elevation map(the concept is called suffix max).
3. Finally we iterate through each position, calculating the trapped water at that position using the formula min(left[i], right[i]) - arr[i].
4. The trapped water at each position is added to the sum.
The total trapped water is returned as the result.
```

* **Java**

```
class Solution {
    public int trap(int[] height) {
        return Maximum_Water(height);
    }

    public static int Maximum_Water(int[] arr) {
		int n = arr.length;
		// left max
		int[] left = new int[n];
		left[0] = arr[0];
		for (int i = 1; i < n; i++) {
			left[i] = Math.max(left[i - 1], arr[i]);
		}
		
		//right max
		int[] right = new int[n];
		right[n-1] = arr[n-1];
		for(int i = n-2; i>=0; i--) {
			right[i] = Math.max(right[i+1], arr[i]);
		}
		
		// Calculate the ans
		int sum = 0;
		for(int i=0; i<right.length; i++) {
			sum = sum + Math.min(left[i],right[i]) - arr[i];
		}
		return sum;

	}
}


```