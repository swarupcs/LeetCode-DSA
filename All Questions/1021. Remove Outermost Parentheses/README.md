## 1021. Remove Outermost Parentheses



https://leetcode.com/problems/remove-outermost-parentheses/

A valid parentheses string is either empty "", "(" + A + ")", or A + B, where A and B are valid parentheses strings, and + represents string concatenation.

For example, "", "()", "(())()", and "(()(()))" are all valid parentheses strings.
A valid parentheses string s is primitive if it is nonempty, and there does not exist a way to split it into s = A + B, with A and B nonempty valid parentheses strings.

Given a valid parentheses string s, consider its primitive decomposition: s = P1 + P2 + ... + Pk, where Pi are primitive valid parentheses strings.

Return s after removing the outermost parentheses of every primitive string in the primitive decomposition of s.


#### Example 1:
```
Input: s = "(()())(())"
Output: "()()()"
Explanation: 
The input string is "(()())(())", with primitive decomposition "(()())" + "(())".
After removing outer parentheses of each part, this is "()()" + "()" = "()()()".
```

#### Example 2:
```
Input: s = "(()())(())(()(()))"
Output: "()()()()(())"
Explanation: 
The input string is "(()())(())(()(()))", with primitive decomposition "(()())" + "(())" + "(()(()))".
After removing outer parentheses of each part, this is "()()" + "()" + "()(())" = "()()()()(())".
```

#### Example 2:
```
Input: s = "()()"
Output: ""
Explanation: 
The input string is "()()", with primitive decomposition "()" + "()".
After removing outer parentheses of each part, this is "" + "" = "".
```

#### Constraints:
```
1 <= s.length <= 105
s[i] is either '(' or ')'.
s is a valid parentheses string.
```

## Approach
```
The Optimal approach to remove the outermost parentheses from a string can be achieved using a simple algorithm that keeps track of the number of opening and closing parentheses encountered. Here is an optimal approach:

1. Initialize two variables, open_count and close_count, to zero
2. Initialize an empty string called result.
3. Loop through each character c in the input string s.
4. If c is an opening parenthesis, increment open_count.
6. If c is a closing parenthesis, increment close_count.
7. If open_count and close_count are equal and greater than zero, this means that we have encountered a complete pair of opening and closing parentheses, so we can add the substring between them to the result string.
8. Reset open_count and close_count to zero.
9. Return the result string.
```

## Solutions

* **Java**

```
class Solution {
    public String removeOuterParentheses(String s) {
        int openCount = 0;
        int closeCount = 0;
        String result = "";
        int start = 0;
 
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if (c == '(') {
                openCount++;
            } else if (c == ')') {
                closeCount++;
            }
 
            if (openCount == closeCount) {
                result += s.substring(start+1, i);
                start = i+1;
            }
        }
 
        return result;
    }
}
```