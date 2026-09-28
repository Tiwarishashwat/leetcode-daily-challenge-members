```java
class Solution {
    public int maxDepth(String s) {
        int result=0;
        int opCount=0;
        int n=s.length();
        for(int i=0;i<n;i++){
            char ch = s.charAt(i);
            if(ch == '('){
                opCount++;
            }else if(ch == ')'){
                result = Math.max(result, opCount);
                opCount--;
            }
        }
        return result;
    }
}
```

```cpp
class Solution {
public:
    int maxDepth(string s) {
        int result = 0;
        int opCount = 0;
        int n = s.length();

        for (int i = 0; i < n; i++) {
            char ch = s[i];

            if (ch == '(') {
                opCount++;
            } 
            else if (ch == ')') {
                result = max(result, opCount);
                opCount--;
            }
        }

        return result;
    }
};
```

```python
class Solution:
    def maxDepth(self, s: str) -> int:
        result = 0
        opCount = 0
        n = len(s)

        for i in range(n):
            ch = s[i]

            if ch == '(':
                opCount += 1
            elif ch == ')':
                result = max(result, opCount)
                opCount -= 1

        return result
```
