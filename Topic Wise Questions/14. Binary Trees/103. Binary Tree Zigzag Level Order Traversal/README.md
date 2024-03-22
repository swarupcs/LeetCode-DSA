## 103. Binary Tree Zigzag Level Order Traversal


https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/


```
Given the root of a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).
```

#### Example 1:
![Alt text](image.png)
```
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[20,9],[15,7]]

```

#### Example 2:
```
Input: root = [1]
Output: [[1]]
```

#### Example 3:
```
Input: root = []
Output: []
```

#### Constraints:
```
The number of nodes in the tree is in the range [0, 2000].
-100 <= Node.val <= 100
```

## Solutions


* **Java**

## https://www.youtube.com/watch?v=y3lJY5ofLro

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
Steps: 
1. Create a list, that used for resultant output
2. If root is null, then we return empty list
3. Create a queue for level order traversal.
4. Initially we add root into the queue.
5. Initialize a flag variable , which is initialize by false, as in the first level we traverse left to right
6. Repeat following steps until queue is not empty
    a) Calculate the size of the queue (which is the number of nodes in current level)
    b) Create a list and a stack
    c) Repeat the following steps for the queue size times(current level)
        i) Add element based on the flag.
        ii) Enqueue the left and right children of the current node if the exist
    d) After processing each level, switch the value of flag
    e) Pop all elements from the stack and add them to the level
    f) Add the level list to the final result "zigzag"
7. Return the final result containing zigzag level order traversal.

 */
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> zigzag = new ArrayList<>();
        if (root == null){
            return zigzag;
        } 
            
        //Queue is used for level order traversal
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        boolean flag = false;

        while (!queue.isEmpty()) {

            int size = queue.size();
            List<Integer> level = new ArrayList<>();
            Stack<Integer> reverseStack = new Stack<>();
            for (int i = 0; i < size; i++) {
                TreeNode node = queue.poll();

                // Check flag
                if (flag){
                    reverseStack.add(node.val);
                }
                else {
                    level.add(node.val);
                }

                if (node.left != null) {
                    queue.add(node.left);
                } 
                if (node.right != null) {
                    queue.add(node.right);
                }    
            }
            flag = !flag;

            // Pop all elements from stack
            while (!reverseStack.isEmpty()) {
                level.add(reverseStack.pop());

            }

            zigzag.add(level);
        }

        return zigzag;
    }
}


```