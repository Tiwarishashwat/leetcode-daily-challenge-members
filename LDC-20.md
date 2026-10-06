```java
class Solution {
    public int minAddToMakeValid(String s) {
        int open = 0, close=0;
        for(int i=0;i<s.length();i++){
            char ch = s.charAt(i);
            if(ch == '('){
                open++;
            } else {
                if(open>0) {
                    open--;
                } else {
                    close++;
                }
            }
        }
        return (open+close); 
    }
}


```

```cpp
class Solution {
public:
    int minAddToMakeValid(string s) {
        int open = 0, close = 0;

        for (char ch : s) {
            if (ch == '(') {
                open++;
            } else {
                if (open > 0) {
                    open--;
                } else {
                    close++;
                }
            }
        }

        return open + close;
    }
};
```

```python
class Solution:
    def minAddToMakeValid(self, s: str) -> int:
        open = 0
        close = 0

        for ch in s:
            if ch == '(':
                open += 1
            else:
                if open > 0:
                    open -= 1
                else:
                    close += 1

        return open + close
```
