## 101. Symmetric Tree


https://leetcode.com/problems/symmetric-tree/


```
Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).
```

#### Example 1:
![Alt text](image.png)
```
Input: root = [1,2,2,3,4,4,3]
Output: true

```

#### Example 2:
![Alt text](image-1.png)
```
Input: root = [1,2,2,null,3,null,3]
Output: false
```


#### Constraints:
```
The number of nodes in the tree is in the range [1, 1000].
-100 <= Node.val <= 100
```

## Solutions


* **Java**

```
Steps:

1. We take two variables root1 and root2 initially both pointing to the root.
2. Then we use any tree traversal to traverse the nodes. 
    We will simultaneously change root1 and root2 in this traversal function.
3. For the base case, if both are pointing to NULL, we return true, 
    whereas if only one points to NULL and other to a node, we return false.
3. If both points to a node, we first compare their value, 
    if it is the same we check for the lower levels of the tree.
4. We recursively call the function to check the root1’s left child with root2’s right child; 
    then we again recursively check the root1’s right child with root2’s left child.
5. When all three conditions ( node values of left and right and two recursive calls) return true, 
    we return true from our function else we return false.
```


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
    public boolean isSymmetric(TreeNode root) {
        if(root == null) {
            return true;
        }
        return isSymmetricUtil(root.left, root.right);
    }

    public boolean isSymmetricUtil(TreeNode root1, TreeNode root2) {
        if(root1 == null || root2 == null) {
            return root1 == root2;
        }

        return (root1.val == root2.val) && isSymmetricUtil(root1.left, root2.right) && isSymmetricUtil(root1.right, root2.left);
    }
}


```