# Binary Tree Inorder Traversal

Given the root of a binary tree, return the inorder traversal of its nodes' values.

 

Example 1:

![Add](https://assets.leetcode.com/uploads/2020/09/15/inorder_1.jpg)
```
Input: root = [1,null,2,3]
Output: [1,3,2]
```
Example 2:
```
Input: root = []
Output: []
```
Example 3:
```
Input: root = [1]
Output: [1]
```

Constraints:

- The number of nodes in the tree is in the range [0, 100].
- -100 <= Node.val <= 100
 

**Follow up:** Recursive solution is trivial, could you do it iteratively?

## Solution

```c++
vector<int> inorderTraversal(TreeNode* root) 
    {
        vector<int> res;  
        inorder(root, res);
        return res;
    }

    void inorder(TreeNode* root, vector<int>& res)
     {
        if (root == NULL) return;  
        inorder(root->left, res); 
        res.push_back(root->val); 
        inorder(root->right, res); 
     }
```