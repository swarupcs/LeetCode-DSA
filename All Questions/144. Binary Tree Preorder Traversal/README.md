## 136. Single Number


https://leetcode.com/problems/binary-tree-preorder-traversal/


```
Given the root of a binary tree, return the preorder traversal of its nodes' values.
```

#### Example 1:
![Alt text](image.png)
```
Input: root = [1,null,2,3]
Output: [1,2,3]

```

#### Example 2:
```
Input: root = []
Output: []
```

#### Example 3:
```
Input: root = [1]
Output: [1]
```

#### Constraints:
```
The number of nodes in the tree is in the range [0, 100].
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
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> ans = new ArrayList<>();
        preOrder(root, ans);
        return ans;


    }

    public static void preOrder(TreeNode root, List<Integer> ans) {
        if(root == null) {
            return;
        }

        ans.add(root.val);
        preOrder(root.left, ans);
        preOrder(root.right, ans);
    }
}
```