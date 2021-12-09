```python
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        return self.traversal(preorder, inorder)
    def traversal(self, preorder, inorder):
        if len(preorder) == 0:
            return None
        
        pre = preorder[0]
        in_index = inorder.index(pre)
        root = TreeNode(val=pre)
        
        if len(preorder) == 1:
            return root
        
        left = self.traversal(preorder[1:in_index+1], inorder[:in_index])
        right = self.traversal(preorder[in_index+1:], inorder[in_index+1:])
        
        root = TreeNode(val=pre, left=left, right=right)
        
        return root
```
