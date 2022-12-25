# Valid Substring
Given a string S consisting only of opening and closing parenthesis 'ie '('  and ')', find out the length of the longest valid(well-formed) parentheses substring.
NOTE: Length of the smallest valid substring ( ) is 2.

Example 1:
```
Input: S = "(()("
Output: 2
Explanation: The longest valid 
substring is "()". Length = 2.
```
Example 2:
```
Input: S = "()(())("
Output: 6
Explanation: The longest valid 
substring is "()(())". Length = 6.
```

## Your Task:  

You dont need to read input or print anything. Complete the function findMaxLen() which takes S as input parameter and returns the maxlength.


Expected Time Complexity:O(n)
Expected Auxiliary Space: O(1)   


## Constraints:
```
1 <= |S| <= 105
```
## Solution

```c++
int findMaxLen(string s) 
{
        // code here
    stack<int> st;
    st.push(-1);
    int res = 0;
    for(int i=0; i<s.length(); i++)
    {
        if(s[i]=='(') st.push(i);
        else 
        {
            st.pop();
            if(st.empty()) st.push(i);
            else res = max(res, i-st.top());
        }
    }
     return res;
}
```