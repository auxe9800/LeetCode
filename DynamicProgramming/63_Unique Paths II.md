```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        if obstacleGrid[len(obstacleGrid)-1][len(obstacleGrid[0])-1] == 1:
            return 0
        dp = [[0]*len(obstacleGrid[0]) for i in range(len(obstacleGrid))]
        dp[0][0] = 1
        for i in range(len(obstacleGrid)):
            for j in range(len(obstacleGrid[i])):
                if i == 0:
                    if j != 0:
                        if obstacleGrid[i][j-1] == 0:
                            dp[i][j] += dp[i][j-1]
                elif j == 0:
                    if i != 0:
                        if obstacleGrid[i-1][j] == 0:
                            dp[i][j] += dp[i-1][j]
                else:
                    if obstacleGrid[i][j-1] == 0:
                        dp[i][j] += dp[i][j-1]
                    if obstacleGrid[i-1][j] == 0:
                        dp[i][j] += dp[i-1][j]
        return dp[len(obstacleGrid)-1][len(obstacleGrid[0])-1]
```
