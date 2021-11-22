# LeetCode
## Stack and Queue
1. Implement Queue using Stacks (232)
```python
class MyQueue(object):

    def __init__(self):
        self.first_stack = list()
        self.second_stack = list()

    def push(self, x):
        """
        :type x: int
        :rtype: None
        """
        self.first_stack.append(x)
        

    def pop(self):
        """
        :rtype: int
        """
        if len(self.second_stack) == 0:
            for _ in range(len(self.first_stack)):
                self.second_stack.append(self.first_stack.pop())
        return self.second_stack.pop()

    def peek(self):
        """
        :rtype: int
        """
        if len(self.second_stack) == 0:
            for _ in range(len(self.first_stack)):
                self.second_stack.append(self.first_stack.pop())
        return self.second_stack[-1]
        

    def empty(self):
        """
        :rtype: bool
        """
        return len(self.first_stack) == 0 and len(self.second_stack) == 0
```
2. Implement Stack using Queues (225)
```python
class MyStack(object):

    def __init__(self):
        self.queue_one = list()
        self.queue_two = list()
        self.is_queue_one = True

    def push(self, x):
        """
        :type x: int
        :rtype: None
        """
        if self.is_queue_one:
            self.queue_two.insert(0, x)
        else:
            self.queue_one.insert(0, x)

    def pop(self):
        """
        :rtype: int
        """
        if self.is_queue_one:
            for _ in range(len(self.queue_two) - 1):
                self.queue_one.insert(0, self.queue_two.pop())
            self.is_queue_one = False
            return self.queue_two.pop()
        else:
            for _ in range(len(self.queue_one) - 1):
                self.queue_two.insert(0, self.queue_one.pop())
            self.is_queue_one = True
            return self.queue_one.pop()
        

    def top(self):
        """
        :rtype: int
        """
        if self.is_queue_one:
            for _ in range(len(self.queue_two) - 1):
                self.queue_one.insert(0, self.queue_two.pop())
            return self.queue_two[-1]
        else:
            for _ in range(len(self.queue_one) - 1):
                self.queue_two.insert(0, self.queue_one.pop())
            return self.queue_one[-1]
        

    def empty(self):
        """
        :rtype: bool
        """
        return not (self.queue_one or self.queue_two)
```
3. Valid Parentheses (20)
```python
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        my_dict = {}
        my_dict['('] = ')'
        my_dict['{'] = '}'
        my_dict['['] = ']'
        my_stack = []
        for b in s:
            if my_stack:
                if my_stack[-1] in my_dict and my_dict[my_stack[-1]] == b:
                    my_stack.pop()
                    continue
            my_stack.append(b)
        return not my_stack
```
4. Remove All Adjacent Duplicates In String (1047)
```python
class Solution(object):
    def removeDuplicates(self, s):
        """
        :type s: str
        :rtype: str
        """
        my_stack = []
        
        for i in range(len(s)):
            if my_stack and my_stack[-1] == s[i]:
                my_stack.pop()
            else:
                my_stack.append(s[i])
                
        return ''.join(my_stack)
```
5. Evaluate Reverse Polish Notation (150)
```python
class Solution(object):
    def evalRPN(self, tokens):
        """
        :type tokens: List[str]
        :rtype: int
        """
        my_stack = []
        
        for i in range(len(tokens)):
            if tokens[i] not in ["+", "-", "*", "/", ]:
                my_stack.append(int(tokens[i]))
            elif tokens[i] == "+":
                second = my_stack.pop()
                first = my_stack.pop()
                my_stack.append(first + second)
            elif tokens[i] == "-":
                second = my_stack.pop()
                first = my_stack.pop()
                my_stack.append(first - second)
            elif tokens[i] == "*":
                second = my_stack.pop()
                first = my_stack.pop()
                my_stack.append(first * second)
            elif tokens[i] == "/":
                second = my_stack.pop()
                first = my_stack.pop()
                res = int(first / second)
                my_stack.append(res)
        return my_stack.pop()
```
