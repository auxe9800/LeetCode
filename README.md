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
