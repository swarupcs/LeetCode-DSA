## 278. First Bad Version


https://leetcode.com/problems/first-bad-version/


```
You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API bool isBadVersion(version) which returns whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.
```

#### Example 1:

```
Input: n = 5, bad = 4
Output: 4
Explanation:
call isBadVersion(3) -> false
call isBadVersion(5) -> true
call isBadVersion(4) -> true
Then 4 is the first bad version.

```

#### Example 2:
```
Input: n = 1, bad = 1
Output: 1
```


#### Constraints:
```
1 <= bad <= n <= 231 - 1
```

## Solutions


```
Key Points :

1. Utilize binary search for efficient narrowing down of the version range.
2. Initialize low and high pointers to the start and end of the range.
3. Update ans whenever a bad version is found, then narrow the search to the left.
4. Iterate through the version range until low is greater than high.
5. Return the value of ans as the first bad version.

```

* **Java**

```
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); */

public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        return firstBad(n);
    }

    public int firstBad(int n) {
		int low = 1;
		int high = n;
		int ans = 0;
		while(low<=high) {
			int mid = low+(high - low)/2;
			if(isBadVersion(mid) == true) {
				ans = mid;
				high = mid - 1;
			} else {
				low = mid + 1;
			}
		}
		
		return ans;
	}
}


```