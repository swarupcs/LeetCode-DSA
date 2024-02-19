## 231. Power of Two


https://leetcode.com/problems/power-of-two/


```
Given an integer n, return true if it is a power of two. Otherwise, return false.

An integer n is a power of two, if there exists an integer x such that n == 2x.
```

#### Example 1:

```
Input: n = 1
Output: true
Explanation: 20 = 1

```

#### Example 2:
```
Input: n = 16
Output: true
Explanation: 24 = 16
```

#### Example 3:
```
Input: n = 3
Output: false
```

#### Constraints:
```
-231 <= n <= 231 - 1
```

## Solutions

### Intuition

```
We need to detect if the number is power of two. So, we can just divide n by 2 and check if we got any remainder until n equals 1. If it goes so far, 
we know it's power of two. If we get any remainders somewhere, it's not power of two.
```

### Approach
```
1. So, firstly, we check if n is smaller than 1, if smaller, return false. (If it's negative or 0, it can't be power of 2)
2. Use a while loop to keep dividing n by 2 until it becomes less than 2.
3. Inside the loop, check if n divided by 2 leaves a remainder and n is not equal to 1. If yes, return false. Because, power of two must not leave remainder when divided by 2, and we don't return false if n is 1 (1 doesn't follow this pattern, but is still power of 2, bro).
4. Update n by dividing it by 2.
5. If the loop completes without returning false, we can return true.
```

* **Java**

```
class Solution {
    public boolean isPowerOfTwo(int n) {
        if (n < 1) {
            return false;
        }

        while (n >= 2) {
            if ((n % 2 != 0 && n != 1)) {
                return false;
            }

            n = n / 2;
        }

        return true;
    }
}


```