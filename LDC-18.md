```java
public class Solution {
    public int longestValidParentheses(String s) {
        int ans = 0;
        Stack<Integer> stack = new Stack<>();
        stack.push(-1);
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '(') {
                stack.push(i);
            } else {
                stack.pop(); //( , ), -1
                if (stack.empty()) {
                    stack.push(i);
                }
                ans = Math.max(ans, i - stack.peek());
            }
        }
        return ans;
    }
}
```
```cpp

class Solution {
public:
    int longestValidParentheses(string s) {
        int ans = 0;
        stack<int> st;
        st.push(-1);

        for (int i = 0; i < s.length(); i++) {
            if (s[i] == '(') {
                st.push(i);
            } else {
                st.pop();

                if (st.empty()) {
                    st.push(i);
                }

                ans = max(ans, i - st.top());
            }
        }

        return ans;
    }
};
```
```python

class Solution:
    def longestValidParentheses(self, s: str) -> int:
        ans = 0
        stack = [-1]

        for i in range(len(s)):
            if s[i] == '(':
                stack.append(i)
            else:
                stack.pop()

                if not stack:
                    stack.append(i)

                ans = max(ans, i - stack[-1])

        return ans
```
