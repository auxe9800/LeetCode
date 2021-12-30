```python
class Solution:
    def solveSudoku(self, board: List[List[str]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """
        def is_valid(row, col, val, board):
            for i in range(len(board)):
                if val == board[i][col]:
                    return False
            for j in range(len(board)):
                if val == board[row][j]:
                    return False
            start_row = int(row/3)*3
            start_col = int(col/3)*3
            for i in range(start_row, start_row+3):
                for j in range(start_col, start_col+3):
                    if val == board[i][j]:
                        return False
            return True
        def backtracking(board):
            for i in range(len(board)):
                for j in range(len(board)):
                    if board[i][j] != ".":
                        continue
                    for k in range(1, 10):
                        if is_valid(i, j, str(k), board):
                            board[i][j] = str(k)
                            if backtracking(board):
                                return True
                            board[i][j] = "."
                    return False
            return True
        backtracking(board)
```
