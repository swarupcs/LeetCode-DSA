## 104. Maximum Depth of Binary Tree

https://leetcode.com/problems/maximum-depth-of-binary-tree/


```
Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.
```

#### Example 1:
![Alt text](image.png)
```
Input: root = [3,9,20,null,null,15,7]
Output: 3
```

#### Example 2:
```
Input: root = [1,null,2]
Output: 2
```


#### Constraints:
```
The number of nodes in the tree is in the range [0, 104].
-100 <= Node.val <= 100
```

## Solutions


* **Java**

```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null) {
            return 0;
        }
        int leftHeight = maxDepth(root.left);
        int rightHeight = maxDepth(root.right);

        return (1 + Math.max(leftHeight, rightHeight));
    }
}


```