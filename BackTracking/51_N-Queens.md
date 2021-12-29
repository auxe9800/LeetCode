```python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        chessboard = []
        path = []
        
        def is_valid(path, row, col):
            for i in range(row):
                if path[i][col] == "Q":
                    return False
                
            i = row -1
            j = col -1
            while i>=0 and j>=0:
                if path[i][j] == 'Q':
                    return False
                i -= 1
                j -= 1
                
            i = row - 1
            j = col + 1
            while i>=0 and j <= n -1:
                if path[i][j] == "Q":
                    return False
                i -= 1
                j += 1
                
            return True
            
        def backtracking(n, row):
            nonlocal chessboard
            nonlocal path
            
            if n == row:
                for i in range(len(path)):
                    path[i] = "".join(path[i])
                chessboard.append(path.copy())
                return
            
            temp = ["."] * n
            for col in range(0, n):
                temp[col] = "Q"
                path.append(temp.copy())
                if is_valid(path, row, col):
                    backtracking(n, row+1)
                path.pop()
                temp[col] = "."
                    
        backtracking(n, 0)
        return chessboard
```
