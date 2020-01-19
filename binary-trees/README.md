# Binary Trees

## Overview
* A tree is a _directed acyclic graph_ which has `N` nodes and `N-1` edges.
* A binary tree is a tree data structure in which each node has _at most_ two children.

## Tree Traversal
Four methods:
* Pre-order traversal
* In-order traversal
* Post-order traversal

### Pre-order Traversal
1. Root
2. Left
3. Right

![pre-order traversal](./pre-order.png)

### In-order Traversal
1. Left
2. Root
3. Right 

![in-order traversal](./in-order.png)
**Note:** For _binary search trees_ (a special kind of binary tree), we can retrieve all data in sorted order using in-order traversal.

### Post-order Traversal
1. Left
2. Right
3. Root

![post-order traversal](./post-order.png)
Post-order traversal is used when deleting nodes in a tree. And this makes sense. You want to delete both child nodes before deleting the parent node.

## Practice
**1. Given a binary tree, return the _preorder_ traversal of its nodes' values.**
  **Example:**
  ```
  Input: [1, null, 2, 3]
     1
      \
       2
      /
     3

  Output: [1, 2, 3]
  ```

  **Recursive Solution**:
  ```python
  class TreeNode:
       def __init__(self, x):
           self.val = x
           self.left = None
           self.right = None

  def preorderTraversal(root: TreeNode) -> List[int]:
      values = [];
      
      if root:
          values.append(root.val)
          values = values + preorderTraversal(root.left)
          values = values + preorderTraversal(root.right)
      
      return values
  ```

  **Iterative Solution**:
  ```python
  def preorderTraversal(root):
      """
      :type root: TreeNode
      :rtype: List[int]
      """
      result = []
      stack = []
      cur = root
      while cur or stack:
          while cur:
              stack.append(cur)
              result.append(cur.val)
              cur = cur.left
          cur = stack.pop()
          cur = cur.right
      return result
  ```

**2. Given a binary tree, return the inorder traversal of its nodes' values.**
  **Example:**
  ```
  Input: [1, null, 2, 3]
     1
      \
       2
      /
     3

  Output: [1, 3, 2]
  ```

  **Recursive Solution**
  ```python
  def inorderTraversal(root: TreeNode) -> List[int]:
    if not root: return []
    res = []
    
    if root.left:
        res = res + inorderTraversal(root.left)
    
    res.append(root.val)
    
    if root.right:
        res = res + inorderTraversal(root.right)
        
    return res
  ```

  **Iterative Solution**
  ```python
  def inorderTraversal(root: TreeNode) -> List[int]:
    current = []
    stack = []

    while current or stack
