```python
class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:
        n = len(heights)
        maxLeftIndex = [0] * n
        maxRightIndex = [0] * n
        result = 0
        
        maxLeftIndex[0] = -1
        for i in range(1, n):
            temp = i-1
            while temp >= 0 and heights[temp] >= heights[i]:
                temp = maxLeftIndex[temp]
            maxLeftIndex[i] = temp
        
        
        maxRightIndex[n-1] = n
        for i in range(n-2, -1, -1):
            temp = i+1
            
            while temp < n and heights[temp] >= heights[i]:
                temp = maxRightIndex[temp]
            maxRightIndex[i] = temp
            
        for i in range(n):
            area = heights[i] * (maxRightIndex[i] - maxLeftIndex[i] - 1)
            result = max(area, result)
            
        return result
```
