```java
class Solution {
    public int minInsertions(String s) {
        int closingRequired = 0;
        int insertions = 0;
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if (ch == '(') {
                if (closingRequired % 2 != 0) { //one closing was needed but open came
                    insertions++;  // Insert ')' to complete the previous pair
                    closingRequired--; //  // One pending ')' requirement is satisfied
                }
                closingRequired += 2; // Current '(' requires two ')'
            } else {
                closingRequired--; // Current ')' satisfies one pending requirement

                if (closingRequired < 0) { // case where we have one closing
                    insertions++; // Insert '(' to match the current ')' 
                    closingRequired = 1; // Inserted '(' still needs one ')'
                }
            }
        }
        return insertions + closingRequired;
    }
}
```

```cpp

class Solution {
public:
    int minInsertions(string s) {
        int closingRequired = 0;
        int insertions = 0;

        for (int i = 0; i < s.length(); i++) {
            char ch = s[i];

            if (ch == '(') {
                if (closingRequired % 2 != 0) {
                    insertions++;
                    closingRequired--;
                }

                closingRequired += 2;
            } else {
                closingRequired--;

                if (closingRequired < 0) {
                    insertions++;
                    closingRequired = 1;
                }
            }
        }

        return insertions + closingRequired;
    }
};

```

```python

class Solution:
    def minInsertions(self, s: str) -> int:
        closingRequired = 0
        insertions = 0

        for ch in s:
            if ch == '(':
                if closingRequired % 2 != 0:
                    insertions += 1
                    closingRequired -= 1

                closingRequired += 2
            else:
                closingRequired -= 1

                if closingRequired < 0:
                    insertions += 1
                    closingRequired = 1

        return insertions + closingRequired

```
