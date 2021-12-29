```python
class Solution:
    def findItinerary(self, tickets: List[List[str]]) -> List[str]:
        path = ["JFK"]
        ticket_dict = defaultdict(list)
        
        for item in tickets:
            ticket_dict[item[0]].append(item[1])
            
        def backtracking(start_point):
            nonlocal path
            nonlocal ticket_dict
            
            if len(path) == len(tickets) + 1:
                return True
            
            ticket_dict[start_point].sort()
            for _ in ticket_dict[start_point]:
                end_point = ticket_dict[start_point].pop(0)
                path.append(end_point)
                if backtracking(end_point):
                    return True
                path.pop()
                ticket_dict[start_point].append(end_point)
                
        backtracking("JFK")
        return path
```
