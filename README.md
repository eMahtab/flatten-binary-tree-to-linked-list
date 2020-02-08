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

### ❗️ 💥 Caution : EmptyStackException
Calling stack.pop() or stack.peek() on an empty stack will result in a EmptyStackException. So always make sure you don't call those method on an empty stack. In above implementation when there is only one `TreeNode` in the stack and we pop it, now there is nothing in the satck, so calling `stack.peek()` will result in EmptyStackException. So we add the check of, if the satck is not empty, then only we call `stack.peek()`



# References :
https://www.youtube.com/watch?v=vssbwPkarPQ
