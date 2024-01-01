## 14. Longest Common Prefix


https://leetcode.com/problems/add-two-numbers/

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".



#### Example 1:
```
Input: strs = ["flower","flow","flight"]
Output: "fl"
```

#### Example 2:
```
Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

#### Constraints:
```
1 <= strs.length <= 200
0 <= strs[i].length <= 200
strs[i] consists of only lowercase English letters.
```

## Solutions


#### Horizontal Scanning Approach
```

The objective is to discover the longest common prefix by horizontally scanning each letter in the array of strings one at a time. You can get the LCP by doing the following:

LCP(S1...SN) = LCP(S1, S2, S3,...., SN)

Algorithm:

1. From S1 through SN, iterate through the string one at a time.
2. For each iteration till ith index, the LCP(S1…Si) can be obtained.
3. End the loop and return the empty string if the LCP is empty.
4. Otherwise, keep going, and you can get the LCP(S1...SN) after scanning N strings.
```


* **Java**

```
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if(strs.length == 0) {
            return "";
        }
        String commonPrefix = strs[0];
        for(int i=0; i<strs.length; i++) {
            while(strs[i].indexOf(commonPrefix) != 0) {
                commonPrefix = commonPrefix.substring(0,commonPrefix.length() - 1);
                if(commonPrefix.isEmpty()) {
                    return "";
                }
            }
        }
        return commonPrefix;
    }
}

```

```
Time Complexity: 
O(N) where N is the size of the array S[].

Space Complexity: 
O(1), as no extra space is used.
```