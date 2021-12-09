```python
class Solution:
    def buildTree(self, inorder: List[int], postorder: List[int]) -> Optional[TreeNode]:
        return self.traversal(inorder, postorder)
    def traversal(self, inorder, postorder):
        if len(postorder) == 0:
            return None
        
        post = postorder[-1]
        index_in = inorder.index(post)
        
        left = self.traversal(inorder[:index_in], postorder[:index_in])
        right = self.traversal(inorder[index_in+1:], postorder[index_in:-1])
        
        
        node = TreeNode(post, left, right)
        
        return node
```
