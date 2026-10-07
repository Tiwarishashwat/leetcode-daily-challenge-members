```java
class Solution {
    List<String> result = new ArrayList<>();
    public List<String> removeInvalidParentheses(String s) {
        int extraOpenCount = 0;
        int extraCloseCount = 0;
        for (char ch : s.toCharArray()) {
            if (ch == '(') {
                extraOpenCount++;
            } 
            else if (ch == ')') {
                if (extraOpenCount > 0) {
                    extraOpenCount--;
                } 
                else {
                    extraCloseCount++;
                }
            }
        }
        backtrack(s, 0, 0, extraOpenCount, extraCloseCount, new StringBuilder(), false );
        return result;
    }

    void backtrack(String s, int index, int open, int extraOpenCount, 
        int extraCloseCount, StringBuilder current, boolean previousKept) {
        if (index == s.length()) {
            if (extraOpenCount == 0 && extraCloseCount == 0) {
                result.add(current.toString());
            }
            return;
        }
        char ch = s.charAt(index);
        if (ch == '(') {
            if (extraOpenCount > 0) {
                if (index == 0 || s.charAt(index - 1) != '(' || !previousKept) {
                    backtrack(s, index + 1, open, extraOpenCount - 1, 
                        extraCloseCount, current, false);
                }
            }
            current.append(ch);

            backtrack(s, index + 1, open + 1, extraOpenCount,
                extraCloseCount, current, true
            );
            current.deleteCharAt(current.length() - 1);
        } 
        else if (ch == ')') {
            if (extraCloseCount > 0) {
                if (index == 0 || s.charAt(index - 1) != ')' || !previousKept) {
                    backtrack(s, index + 1, open, extraOpenCount,
                        extraCloseCount - 1, current, false );
                }
            }
            if (open > 0) {
                current.append(ch);
                backtrack(s, index + 1, open - 1, extraOpenCount,
                    extraCloseCount, current, true);
                current.deleteCharAt(current.length() - 1);
            }
        } 
        else {
            current.append(ch);
            backtrack(s, index + 1, open, extraOpenCount,
                extraCloseCount, current, true);
            current.deleteCharAt(current.length() - 1);
        }
    }
}
```

```cpp
class Solution {
    vector<string> result;

public:
    vector<string> removeInvalidParentheses(string s) {
        int extraOpenCount = 0;
        int extraCloseCount = 0;

        for (char ch : s) {
            if (ch == '(') {
                extraOpenCount++;
            }
            else if (ch == ')') {
                if (extraOpenCount > 0) {
                    extraOpenCount--;
                }
                else {
                    extraCloseCount++;
                }
            }
        }

        string current;

        backtrack(
            s, 0, 0,
            extraOpenCount,
            extraCloseCount,
            current,
            false
        );

        return result;
    }

private:
    void backtrack(
        string& s,
        int index,
        int open,
        int extraOpenCount,
        int extraCloseCount,
        string& current,
        bool previousKept
    ) {
        if (index == s.length()) {
            if (extraOpenCount == 0 && extraCloseCount == 0) {
                result.push_back(current);
            }
            return;
        }

        char ch = s[index];

        if (ch == '(') {

            // Delete this '('
            if (extraOpenCount > 0) {
                if (index == 0 ||
                    s[index - 1] != '(' ||
                    !previousKept) {

                    backtrack(
                        s, index + 1, open,
                        extraOpenCount - 1,
                        extraCloseCount,
                        current,
                        false
                    );
                }
            }

            // Keep this '('
            current.push_back(ch);

            backtrack(
                s, index + 1,
                open + 1,
                extraOpenCount,
                extraCloseCount,
                current,
                true
            );

            current.pop_back();
        }

        else if (ch == ')') {

            // Delete this ')'
            if (extraCloseCount > 0) {
                if (index == 0 ||
                    s[index - 1] != ')' ||
                    !previousKept) {

                    backtrack(
                        s, index + 1,
                        open,
                        extraOpenCount,
                        extraCloseCount - 1,
                        current,
                        false
                    );
                }
            }

            // Keep this ')' only if it has a matching '('
            if (open > 0) {
                current.push_back(ch);

                backtrack(
                    s, index + 1,
                    open - 1,
                    extraOpenCount,
                    extraCloseCount,
                    current,
                    true
                );

                current.pop_back();
            }
        }

        else {
            // Normal character: always keep
            current.push_back(ch);

            backtrack(
                s, index + 1,
                open,
                extraOpenCount,
                extraCloseCount,
                current,
                true
            );

            current.pop_back();
        }
    }
};
```

```python
class Solution:
    def __init__(self):
        self.result = []

    def removeInvalidParentheses(self, s: str):
        extraOpenCount = 0
        extraCloseCount = 0

        for ch in s:
            if ch == '(':
                extraOpenCount += 1

            elif ch == ')':
                if extraOpenCount > 0:
                    extraOpenCount -= 1
                else:
                    extraCloseCount += 1

        self.backtrack(
            s,
            0,
            0,
            extraOpenCount,
            extraCloseCount,
            [],
            False
        )

        return self.result

    def backtrack(
        self,
        s,
        index,
        open,
        extraOpenCount,
        extraCloseCount,
        current,
        previousKept
    ):
        if index == len(s):
            if extraOpenCount == 0 and extraCloseCount == 0:
                self.result.append("".join(current))
            return

        ch = s[index]

        if ch == '(':

            # Delete this '('
            if extraOpenCount > 0:
                if (
                    index == 0
                    or s[index - 1] != '('
                    or not previousKept
                ):
                    self.backtrack(
                        s,
                        index + 1,
                        open,
                        extraOpenCount - 1,
                        extraCloseCount,
                        current,
                        False
                    )

            # Keep this '('
            current.append(ch)

            self.backtrack(
                s,
                index + 1,
                open + 1,
                extraOpenCount,
                extraCloseCount,
                current,
                True
            )

            current.pop()

        elif ch == ')':

            # Delete this ')'
            if extraCloseCount > 0:
                if (
                    index == 0
                    or s[index - 1] != ')'
                    or not previousKept
                ):
                    self.backtrack(
                        s,
                        index + 1,
                        open,
                        extraOpenCount,
                        extraCloseCount - 1,
                        current,
                        False
                    )

            # Keep this ')' only if it has a matching '('
            if open > 0:
                current.append(ch)

                self.backtrack(
                    s,
                    index + 1,
                    open - 1,
                    extraOpenCount,
                    extraCloseCount,
                    current,
                    True
                )

                current.pop()

        else:
            # Normal character: always keep
            current.append(ch)

            self.backtrack(
                s,
                index + 1,
                open,
                extraOpenCount,
                extraCloseCount,
                current,
                True
            )

            current.pop()
```
