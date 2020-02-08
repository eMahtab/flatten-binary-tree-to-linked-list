# Flatten a Binary Tree to Linked List
## https://leetcode.com/problems/flatten-binary-tree-to-linked-list

Given a binary tree, flatten it to a linked list in-place.
```
For example, given the following tree:

    1
   / \
  2   5
 / \   \
3   4   6

The flattened tree should look like:

1
 \
  2
   \
    3
     \
      4
       \
        5
         \
          6
```

# Implementation :

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public void flatten(TreeNode root) {
        if(root == null)
            return;
        Stack<TreeNode> stack = new Stack<>();
        stack.push(root);
        while(!stack.isEmpty()){
            TreeNode current = stack.pop();
            if(current.right != null)
                stack.push(current.right);
            if(current.left != null)
                stack.push(current.left);
            
            if(!stack.isEmpty())
               current.right = stack.peek();
            current.left = null;
        } 
    }
    
}
```
# References :
https://www.youtube.com/watch?v=vssbwPkarPQ
