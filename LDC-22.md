```java
class Solution {
    public String removeOuterParentheses(String s) {
        StringBuilder res = new StringBuilder("");
        int n = s.length();
        int depth=0;
        for(int i=0;i<n;i++){
            char ch = s.charAt(i);
            if(ch == '('){
                if(depth > 0){
                    res.append(ch);
                }
                depth++;
            }else{
                depth--;
                 if(depth > 0){
                    res.append(ch);
                }
            }
        }
        return res.toString();
    }
}
```
```cpp
class Solution {
public:
    string removeOuterParentheses(string s) {
        string res = "";
        int depth = 0;

        for (char ch : s) {

            if (ch == '(') {
                if (depth > 0) {
                    res += ch;
                }
                depth++;
            }
            else {
                depth--;

                if (depth > 0) {
                    res += ch;
                }
            }
        }

        return res;
    }
};
```
```python
class Solution:
    def removeOuterParentheses(self, s: str) -> str:
        res = ""
        depth = 0

        for ch in s:

            if ch == '(':
                if depth > 0:
                    res += ch

                depth += 1

            else:
                depth -= 1

                if depth > 0:
                    res += ch

        return res
```
