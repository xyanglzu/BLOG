---
 title: Leecode-543.Diameter of Binary Tree
toc: true
date: 2018-09-11 16:08:49
tags: 树
categories: Leecode
---

# 题目

[Leecode 543 Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/description/)

给定一棵二叉树，你需要计算它的直径长度。一棵二叉树的直径长度是任意两个结点路径长度中的最大值。这条路径可能穿过根结点。

**示例 :**
给定二叉树

```
          1
         / \
        2   3
       / \     
      4   5   
```

返回 **3**, 它的长度是路径 [4,2,1,3] 或者 [5,2,1,3]。

**注意：**两结点之间的路径长度是以它们之间边的数目表示。

# 代码

*最长的直径只可能是父亲结点的左子树结点数+右子树结点数，depth方法返回的是树的最大结点树*

```python
class Solution(object):
    def diameterOfBinaryTree(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        self.best = 0

        def depth(root):
            if not root:
                return 0
            left_l = depth(root.left)
            right_l = depth(root.right)
            self.best = max(self.best, left_l + right_l)
            return max(left_l, right_l) + 1

        depth(root)
        return self.best
```

