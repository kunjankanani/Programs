# Increasing Order Search Tree

Given the root of a binary search tree, rearrange the tree in in-order so that the leftmost node in the tree is now the root of the tree, and every node has no left child and only one right child.

 

Example 1:

![Alt text](https://assets.leetcode.com/uploads/2020/11/17/ex1.jpg)
```
Input: root = [5,3,6,2,4,null,8,1,null,null,null,7,9]

Output: [1,null,2,null,3,null,4,null,5,null,6,null,7,null,8,null,9]
```
Example 2:

![Alt text](https://assets.leetcode.com/uploads/2020/11/17/ex2.jpg)
```
Input: root = [5,1,7]

Output: [1,null,5,null,7]
 ```

Constraints:

- The number of nodes in the given tree will be in the range [1, 100].
- ```0 <= Node.val <= 1000```


## Solution
```c++
TreeNode* increasingBST(TreeNode* root) {
  // Base case: if the root is null, return null
  if (root == nullptr) return nullptr;

  // Recursively rearrange the left subtree
  TreeNode* left = increasingBST(root->left);

  // Set the left child of the root to null
  root->left = nullptr;

  // If the left subtree is not null, find the rightmost node in the left subtree
  // and set its right child to the root
  if (left != nullptr) {
    TreeNode* curr = left;
    while (curr->right != nullptr) {
      curr = curr->right;
    }
    curr->right = root;
  }

  // Recursively rearrange the right subtree
  root->right = increasingBST(root->right);

  // If the left subtree is not null, return the root of the left subtree as the new root
  // otherwise, return the root of the original tree as the new root
  return (left != nullptr) ? left : root;
}
```