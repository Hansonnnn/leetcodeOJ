## Problem
Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as:

>a binary tree in which the depth of the two subtrees of every node never differ by more than 1.


**Example 1:**

Given the following tree `[3,9,20,null,null,15,7]`:

```
    3
   / \
  9  20
    /  \
   15   7
```
return ture.

**Example 2:**
Given the following tree `[1,2,2,3,3,null,null,4,4]`:
```
       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
```

## Solution
```python
class Solution(object):
    def isBalanced(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        if not root: return True
        left = self.get_height(root.left)
        right = self.get_height(root.right)
        if abs(left - right) > 1:
            return False
        return self.isBalanced(root.left) and self.isBalanced(root.right)
        pass

    def get_height(self, root):
        if root is None: return 0
        left = self.get_height(root.left)
        right = self.get_height(root.right)
        return max(left, right) + 1
```
link: https://leetcode.com/problems/balanced-binary-tree/

关于BST树的基本介绍及操作可以参照[BST](https://github.com/Hansonnnn/leetcodeOJ/blob/master/algorithms/BST.md)
