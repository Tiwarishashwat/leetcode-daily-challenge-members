```java
class Solution {
    public boolean checkValidString(String s) {
        int openCount = 0;
        int closeCount = 0;
        int length = s.length() - 1;
        
        for (int i = 0; i <= length; i++) {
            if (s.charAt(i) == '(' || s.charAt(i) == '*') {
                openCount++;
            } else { //)
                openCount--;
            }
            
            if (s.charAt(length - i) == ')' || s.charAt(length - i) == '*') {
                closeCount++;
            } else { //(
                closeCount--;
            }
            
            if (openCount < 0 || closeCount < 0) {
                return false;
            }
        }
        
        
        return true;
    }
}
```

```cpp

class Solution {
public:
    bool checkValidString(string s) {
        int openCount = 0;
        int closeCount = 0;
        int length = s.length() - 1;

        for (int i = 0; i <= length; i++) {
            if (s[i] == '(' || s[i] == '*') {
                openCount++;
            } else { // )
                openCount--;
            }

            if (s[length - i] == ')' || s[length - i] == '*') {
                closeCount++;
            } else { // (
                closeCount--;
            }

            if (openCount < 0 || closeCount < 0) {
                return false;
            }
        }

        return true;
    }
};

```

```python

class Solution:
    def checkValidString(self, s: str) -> bool:
        openCount = 0
        closeCount = 0
        length = len(s) - 1

        for i in range(length + 1):
            if s[i] == '(' or s[i] == '*':
                openCount += 1
            else:  # )
                openCount -= 1

            if s[length - i] == ')' or s[length - i] == '*':
                closeCount += 1
            else:  # (
                closeCount -= 1

            if openCount < 0 or closeCount < 0:
                return False

        return True
```
