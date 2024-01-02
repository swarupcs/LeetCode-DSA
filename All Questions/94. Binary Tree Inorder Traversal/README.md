## 94. Binary Tree Inorder Traversal


https://leetcode.com/problems/binary-tree-inorder-traversal/


```
Given the root of a binary tree, return the inorder traversal of its nodes' values.
```

#### Example 1:
![Alt text](image.png)
```
Input: root = [1,null,2,3]
Output: [1,3,2]
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

### Approach 1 : Recursive

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
    public List<Integer> inorderTraversal(TreeNode root) {
       List<Integer> ans = new ArrayList<>();
       inOrder(root, ans);
       return ans; 
    }

    public static void inOrder(TreeNode root, List<Integer> ans) {
        if(root == null) {
            return;
        }

        inOrder(root.left, ans);
        ans.add(root.val);
        inOrder(root.right, ans);  
    }
}

```
### Approach 2 : Iterative
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

/*
Iterative Approach:

1. Create an ArrayList named inorder;
2. Create an TreeNode type Stack named stack;
3. Initialize node as root;
4. If node is not null then,
    a. push the node into stack; (stack.push(node);)
    b. node moves to it's 'left child; (node = node.left;)
5. Else 
    a. If stack is empty then
        break from the loop;
    b. Otherwise 
        i) pop the top element from stack and store into node; (node = stack.pop();)
        ii) add the node value into inorder List; (inorder.add(node.val);)
        iii) move node to it's right child;
6. Repeat step 4 and 5; (while(true))
7. Return inorder
*/
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> inorder = new ArrayList<Integer>();
        Stack<TreeNode> stack = new Stack<TreeNode>();
        TreeNode node = root;
        while(true) {
            if(node != null) {
                stack.push(node);
                node = node.left;
            } else {
                if(stack.isEmpty()) {
                    break;
                }
                node = stack.pop();
                inorder.add(node.val);
                node = node.right;
            }
        }
        return inorder;
    }
}
```