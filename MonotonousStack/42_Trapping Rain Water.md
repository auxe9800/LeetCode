```python
class Solution:
    def trap(self, height: List[int]) -> int:
        maxLeft = [0] * len(height)
        maxRight = [0] * len(height)
        result = 0
        
        maxLeft[0] = height[0]
        for i in range(1, len(height)):
            maxLeft[i] = max(height[i], maxLeft[i-1])
            
        maxRight[len(height)-1] = height[len(height)-1]
        for i in range(len(height)-2, 0, -1):
            maxRight[i] = max(height[i], maxRight[i+1])
            
        for i in range(1, len(height)-1):
            temp = min(maxLeft[i], maxRight[i]) - height[i]
            if temp > 0:
                result += temp
                
        return result
```
