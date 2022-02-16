```python
class Solution:
    def nextGreaterElements(self, nums: List[int]) -> List[int]:
        n = len(nums)
        nums *= 2
        ans = [-1] * len(nums)
        stack = [0]

        for i in range(1, len(nums)):
            if nums[i] <= nums[stack[-1]]:
                stack.append(i)
            else:
                while stack and nums[i] > nums[stack[-1]]:
                    ans[stack.pop()] = nums[i]

                stack.append(i)
                
        return ans[:n]
```
