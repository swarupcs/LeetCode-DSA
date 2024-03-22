## 102. Binary Tree Level Order Traversal


https://leetcode.com/problems/binary-tree-level-order-traversal/


```
Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).
```

#### Example 1:
![Alt text](image.png)
```
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[9,20],[15,7]]
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
-1000 <= Node.val <= 1000
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

/*
Approach : Using queue

1. Create a queue;
2. Create a List named ans;
3. If root is null, then return ans;
4. Add root element into queue; (queue.offer(root);)
5. Calculate the size of the queue at that moment; (int levelNum = queue.size();)
6. Create a List named subList to add the current queue elements;
7. Traverse the queue for the queueSize times;
    a. If left child of queue.peek() is not null, then add the queue.peek() element into queue
    b. If right child of queue.peek() is not null, then add the queue.peek() element into queue
    c. Add queue.poll() element into subList.
8. Add the subList into ans List.
9. Repeat step 5,6,7,8,9 until the queue becomes empty;
 */
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<TreeNode>();
        List<List<Integer>> ans = new LinkedList<List<Integer>>();
        if(root == null) {
            return ans;
        }
        //Add root element into queue; 
        queue.offer(root);
        while(!queue.isEmpty()) {
            int levelNum = queue.size();
            List<Integer> subList = new LinkedList<Integer>();
            for(int i=0; i<levelNum; i++) {
                //If left child of queue.peek() is not null, then add the queue.peek() element into queue
                if(queue.peek().left != null) {
                    queue.offer(queue.peek().left);
                }
                //If right child of queue.peek() is not null, then add the queue.peek() element into queue
                if(queue.peek().right != null) {
                    queue.offer(queue.peek().right);
                }
                //Add the subList into ans List.
                subList.add(queue.poll().val);
            }
            ans.add(subList);
  
        }
        return ans;
    }
}


```