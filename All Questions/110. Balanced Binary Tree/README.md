## 110. Balanced Binary Tree


https://leetcode.com/problems/balanced-binary-tree/


```
Given a binary tree, determine if it is height-balanced.

Height-Balanced : A height-balanced binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.

```

#### Example 1:
![Alt text](image.png)
```
Input: root = [3,9,20,null,null,15,7]
Output: true
```

#### Example 2:
![Alt text](image-1.png)
```
Input: root = [1,2,2,3,3,null,null,4,4]
Output: false
```

#### Example 3:
```
Input: root = []
Output: true
```

#### Constraints:
```
The number of nodes in the tree is in the range [0, 5000].
-104 <= Node.val <= 104
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
    public boolean isBalanced(TreeNode root) {
        //If the height function not return -1, then it is a balanced binary tree
        return height(root) != -1;
    }

    int height(TreeNode root) {
        // Base case
        if(root == null) {
            return 0;
        }

        // Height of left subtree
        int leftHeight = height(root.left);
        // If the left subtree is unbalanced, return -1
        if(leftHeight == -1) {
            return -1;
        }
        // Height of right subtree
        int rightHeight = height(root.right);
        // If the right subtree is unbalanced, return -1
        if(rightHeight == -1) {
            return -1;
        }

        // If the difference between leftHeight and rightHeight is greater than 1, return -1
        if(Math.abs(leftHeight - rightHeight) > 1) {
            return -1;
        }

        // Otherwise return the height of the tree
        return Math.max(leftHeight, rightHeight) + 1;
    }
}


```