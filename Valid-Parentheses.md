# Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.
 

Example 1:
```
Input: s = "()"
Output: true
```

Example 2:
```
Input: s = "()[]{}"
Output: true
```

Example 3:
```
Input: s = "(]"
Output: false
```

## Constraints:

1 <= s.length <= 10^4

s consists of parentheses only '()[]{}'.

## Solution

To solve this problem in C++, you can use a stack to keep track of the open brackets as you iterate through the string.

Here is some pseudocode for how you could approach this problem:

```c++
bool isValid(string s) {
    stack<char> st;

    for (char c : s) {
        if (c == '(' || c == '{' || c == '[') {
            // If we encounter an open bracket, push it onto the stack
            st.push(c);
        } else {
            // If we encounter a close bracket, check if it is the correct type
            if (st.empty()) {
                // If the stack is empty, there is no corresponding open bracket
                return false;
            }
            if ((c == ')' && st.top() != '(') ||
                (c == '}' && st.top() != '{') ||
                (c == ']' && st.top() != '[')) {
                // If the top of the stack is not the corresponding open bracket, the string is not valid
                return false;
            }
            // If the close bracket is the correct type, pop the open bracket off the stack
            st.pop();
        }
    }

    // If the stack is not empty at the end, there are unbalanced brackets
    return st.empty();
}
```

This algorithm has a time complexity of O(n), where n is the length of the input string. It has a space complexity of O(n), since the stack could potentially hold all of the open brackets in the worst case.

