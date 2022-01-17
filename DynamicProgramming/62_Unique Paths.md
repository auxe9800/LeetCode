```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        grid = [[0]*m for i in range(n)]
        grid[0][0] = 1
        
        for i in range(n):
            for j in range(m):
                if i == 0:
                    if j != 0:
                        grid[i][j] = grid[i][j-1]
                elif j == 0:
                    if i != 0:
                        grid[i][j] = grid[i-1][j]
                else:
                    grid[i][j] = grid[i][j-1] + grid[i-1][j]
                
        return grid[n-1][m-1]
```
