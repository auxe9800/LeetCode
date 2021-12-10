```python
class Solution:
    def constructMaximumBinaryTree(self, nums: List[int]) -> Optional[TreeNode]:
        if len(nums) == 0:
            return None
        
        node_val = max(nums)
        node_index = nums.index(node_val)
        
        left = self.constructMaximumBinaryTree(nums[:node_index])
        right = self.constructMaximumBinaryTree(nums[node_index+1:])
        
        node = TreeNode(node_val, left, right)
        return node
```
