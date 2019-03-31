##### Problem

Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

1.Open brackets must be closed by the same type of brackets.

2.Open brackets must be closed in the correct order.
Note that an empty string is also considered valid.

###### Example1:
```
Input: "()"
Output: true
```

###### Example2:
```
Input: "()[]{}"
Output: true
```

###### Example3:
```
Input: "()[]{}"
Output: true
```
###### Example4:
```
Input: "([)]"
Output: false
```
###### Example4:
```
Input: "{[]}"
Output: true
```
##### Solution 
```
class Solution:
    def isValid(self, str1):
        stack = []
        mapping = {")": "(", "}": "{", "]": "["}
        for s in str1:
            if s in mapping:
                top_elements = stack.pop() if stack else '_'
                if mapping[s] != top_elements:
                    return False
            else:
                stack.append(s)
        return not stack
        
```
##### Problem 2
 there are another similar problem.Just about:

Given a string containing just the characters '(', ')' and '*', determine if the input string is valid.

Note

character '*' can be anything with character '(' or ')',and it also can be just itself.You can regard it as a joker.


###### Example1
```
Input: "(*)"
Output: true
```
###### Example2
```
Input: "((*)"
Output: true
```
###### Example3
```
Input: "(*)))"
Output: False
```
###### Example4
```
Input: ")*)"
Output: False
```

##### Solution

```
    def _isValid(self, str1):
        stack = []
        mapping = {')': '(', '*': '*'}
        for i, s in enumerate(str1):
            if s in mapping:
                top_element = stack.pop() if stack else '_'
                if top_element != mapping[s]:
                    if s == '*' and str1[i+1] not in mapping:
                        return False
                pass
            else:
                stack.append(s)
        return not stack
