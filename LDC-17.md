```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> res = new ArrayList<>();
        backtrack(res, new StringBuilder(""),n, 0, 0);
        return res;
    }
    private void backtrack(List<String> res, StringBuilder current,int n, int open, int close){
        //base case
        if(open==n && close==n){
            res.add(current.toString());
            return;
        }
        if(open<n){
            current.append('(');
            backtrack(res, current, n, open+1, close);
            current.deleteCharAt(current.length()-1);
        }

        if(close < open){
            current.append(')');
            backtrack(res, current, n, open, close+1);
            current.deleteCharAt(current.length()-1);
        }
    }
}
```

```cpp

class Solution {
public:
    void backtrack(vector<string>& res, string& current, int n, int open, int close) {
        // Base case
        if (open == n && close == n) {
            res.push_back(current);
            return;
        }

        if (open < n) {
            current.push_back('(');
            backtrack(res, current, n, open + 1, close);
            current.pop_back();
        }

        if (close < open) {
            current.push_back(')');
            backtrack(res, current, n, open, close + 1);
            current.pop_back();
        }
    }

    vector<string> generateParenthesis(int n) {
        vector<string> res;
        string current = "";
        backtrack(res, current, n, 0, 0);
        return res;
    }
};
```

```python

class Solution:
    def backtrack(self, res, current, n, open, close):
        # Base case
        if open == n and close == n:
            res.append(current)
            return

        if open < n:
            self.backtrack(res, current + '(', n, open + 1, close)

        if close < open:
            self.backtrack(res, current + ')', n, open, close + 1)

    def generateParenthesis(self, n):
        res = []
        self.backtrack(res, "", n, 0, 0)
        return res
```
