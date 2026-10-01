```java
class Solution {
    public boolean isValid(String s) {
        int n = s.length();
        if(n%2!=0){
            return false;
        }
        Stack<Character> stack = new Stack<>();
        for(int i=0;i<n;i++){
            char ch = s.charAt(i);
            if(ch == '(' || ch == '[' || ch == '{'){
                stack.push(ch);
            } else {
                if(stack.isEmpty()){
                    return false;
                }
                char top = stack.peek();
                if(ch == ')' && top != '('){
                    return false;
                } else  if(ch == ']' && top != '['){
                    return false;
                } else  if(ch == '}' && top != '{'){
                    return false;
                } else {
                    stack.pop();
                }
            }
        }
        return (stack.size()==0);
    }
}
```

```cpp
class Solution {
public:
    bool isValid(string s) {
        int n = s.length();

        if (n % 2 != 0) {
            return false;
        }

        stack<char> st;

        for (int i = 0; i < n; i++) {
            char ch = s[i];

            if (ch == '(' || ch == '[' || ch == '{') {
                st.push(ch);
            } else {
                if (st.empty()) {
                    return false;
                }

                char top = st.top();

                if (ch == ')' && top != '(') {
                    return false;
                } 
                else if (ch == ']' && top != '[') {
                    return false;
                } 
                else if (ch == '}' && top != '{') {
                    return false;
                } 
                else {
                    st.pop();
                }
            }
        }

        return st.empty();
    }
};
```

```python
class Solution:
    def isValid(self, s: str) -> bool:
        n = len(s)

        if n % 2 != 0:
            return False

        stack = []

        for i in range(n):
            ch = s[i]

            if ch == '(' or ch == '[' or ch == '{':
                stack.append(ch)
            else:
                if not stack:
                    return False

                top = stack[-1]

                if ch == ')' and top != '(':
                    return False
                elif ch == ']' and top != '[':
                    return False
                elif ch == '}' and top != '{':
                    return False
                else:
                    stack.pop()

        return len(stack) == 0
```
