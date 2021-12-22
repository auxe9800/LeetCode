```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        digits_dict = {}
        digits_dict["2"] = "abc"
        digits_dict["3"] = "def"
        digits_dict["4"] = "ghi"
        digits_dict["5"] = "jkl"
        digits_dict["6"] = "mno"
        digits_dict["7"] = "pqrs"
        digits_dict["8"] = "tuv"
        digits_dict["9"] = "wxyz"
        res = []
        string = ""
        
        if len(digits) == 0:
            return res
        
        def backtracking(digits, index):
            nonlocal res
            nonlocal string
            
            if len(string) == len(digits):
                res.append(string)
                return
            
            number = digits[index]
            for i in range(len(digits_dict[number])):
                string += digits_dict[number][i]
                backtracking(digits, index+1)
                string = string[:-1]
        
        backtracking(digits, 0)
        return res
```
