```java
class Solution {
    public String reverseParentheses(String s) {
        Stack<Integer> stack = new Stack<>();
        int n = s.length();
        int map[] = new int[n];
        for(int i=0;i<n;i++){
            if(s.charAt(i) == '('){
                stack.push(i);
            }else if(s.charAt(i) == ')'){
                map[i] = stack.peek();
                map[stack.peek()] = i;
                stack.pop();
            }
        }
        int i=0;
        StringBuilder result = new StringBuilder();
        int dir=1;
        while(i<n){
            if(s.charAt(i) == '(' || s.charAt(i) == ')'){
                dir=dir*-1;
                i = map[i];
            }else{
                result.append(s.charAt(i));
            }
            i+=dir;
        }
        return result.toString();
    }
}
```

```cpp
class Solution {
public:
    string reverseParentheses(string s) {
        stack<int> st;
        int n = s.length();

        vector<int> mp(n);

        // Store matching parentheses
        for (int i = 0; i < n; i++) {
            if (s[i] == '(') {
                st.push(i);
            } 
            else if (s[i] == ')') {
                mp[i] = st.top();
                mp[st.top()] = i;
                st.pop();
            }
        }

        int i = 0;
        string result = "";
        int dir = 1;

        while (i < n) {
            if (s[i] == '(' || s[i] == ')') {
                dir = dir * -1;
                i = mp[i];
            } 
            else {
                result += s[i];
            }

            i += dir;
        }

        return result;
    }
};
```

```python
class Solution:
    def reverseParentheses(self, s: str) -> str:
        stack = []
        n = len(s)

        # Store matching parentheses
        mp = [0] * n

        for i in range(n):
            if s[i] == '(':
                stack.append(i)
            elif s[i] == ')':
                mp[i] = stack[-1]
                mp[stack[-1]] = i
                stack.pop()

        i = 0
        result = []
        direction = 1

        while i < n:
            if s[i] == '(' or s[i] == ')':
                direction *= -1
                i = mp[i]
            else:
                result.append(s[i])

            i += direction

        return ''.join(result)
```
