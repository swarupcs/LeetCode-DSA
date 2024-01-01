## 151. Reverse Words in a String


https://leetcode.com/problems/reverse-words-in-a-string/

Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in s will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

Note that s may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.


#### Example 1:
```
Input: s = "the sky is blue"
Output: "blue is sky the"
```

#### Example 2:
```
Input: s = "  hello world  "
Output: "world hello"
Explanation: Your reversed string should not contain leading or trailing spaces.
```

#### Example 3:
```
Input: s = "a good   example"
Output: "example good a"
Explanation: You need to reduce multiple spaces between two words to a single space in the reversed string.
```

#### Constraints:
```
1 <= s.length <= 104
s contains English letters (upper-case and lower-case), digits, and spaces ' '.
There is at least one word in s.
```

## Solutions

```
Algorithm :

A. Initialize Pointers and Strings:
    1. Initialize two pointers, left and right, to the start and end of the input string s, respectively.
    2. Initialize an empty string temp to store the characters of a word temporarily.
    3. Initialize an empty string ans to store the reversed order of non-empty words.

B. Iterate Through the String:
    1. Start a loop that continues until the left pointer is less than or equal to the right pointer.
    2. Inside the loop, get the character at the left pointer (ch = s.charAt(left)).

C. Process Characters:

    1. If the character is not a space (' '), append it to the temp string.
    2. If the character is a space and temp is not empty, it means the end of a word:
    3. If ans is not empty, append the current word (temp) followed by a space to ans.
    4. If ans is empty, set ans to the current word (temp).
    5. Reset the temp string to an empty state.

D. Continue Iterating:
    1. Increment the left pointer and repeat the process.

E. Handle the Last Word:
    1. After the loop, check if temp is not empty.
    2. If it's not empty, append it to ans with a space if ans is not empty.
    3. If it's empty, set ans to temp.

F. Return the Result:
    1. The final reversed order of non-empty words is stored in the ans string, which is then returned.
```
* **Java**

```
class Solution {
    public String reverseWords(String s) {
        int left = 0;
	int right = s.length() - 1;

	String temp = "";
	String ans = "";

	//Iterate the string and keep on adding to form a word
	//If empty space is encountered then add the current word to the result
	while (left <= right)
	{
		char ch = s.charAt(left);
		if (ch != ' ')
		{
			temp += ch;
		}
		else if(temp!="")
		{
			if (!ans.equals(""))
			{
				ans = temp + " " + ans;
			}
			else
			{
				ans = temp;
			}
			temp = "";
		}
		left++;
	}

	//If not empty string then add to the result(Last word is added)
	if (!temp.equals(""))
	{
		if (!ans.equals(""))
		{
			ans = temp + " " + ans;
		}
		else
		{
			ans = temp;
		}
	}

	return ans;
    }
}
```