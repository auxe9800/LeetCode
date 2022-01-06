```python
class Solution:
    def lemonadeChange(self, bills: List[int]) -> bool:
        five = 0
        ten = 0
        twenty = 0
        
        for b in bills:
            if b == 5:
                five += 1
            elif b == 10:
                ten += 1
                if five < 1:
                    return False
                five -= 1
            else:
                twenty += 1
                if ten < 1:
                    if five < 3:
                        return False
                    five -= 3
                else:
                    ten -= 1
                    if five < 1:
                        return False
                    five -= 1            
        return True
```
