```java
class Solution {
    public boolean hasValidPath(char[][] grid) {
        int r = grid.length;
        int c = grid[0].length;
        int pathLen = (r-1) + (c-1) + 1;

        if (pathLen % 2 == 1) {
            return false;
        }
        if (grid[0][0] != '(' || grid[r - 1][c - 1] != ')') {
            return false;
        }
        
        boolean[][][] dp = new boolean[r][c][pathLen + 1];
        dp[0][0][1] = true;

        for (int i = 0; i < r; ++i) {
            for (int j = 0; j < c; ++j) {
                int change = grid[i][j] == '(' ? 1 : -1;

                if (i > 0) {
                    for (int openCount = 0; openCount <= pathLen; ++openCount) {
                        if (!dp[i - 1][j][openCount]) {
                            continue;
                        }

                        int newOpenCount = openCount + change;

                        if (newOpenCount >= 0) {
                            dp[i][j][newOpenCount] = true;
                        }
                    }
                }

                if (j > 0) {
                    for (int openCount = 0; openCount <= pathLen; ++openCount) {
                        if (!dp[i][j - 1][openCount]) {
                            continue;
                        }

                        int newOpenCount = openCount + change;

                        if (newOpenCount >= 0) {
                            dp[i][j][newOpenCount] = true;
                        }
                    }
                }
            }
        }

        return dp[r - 1][c - 1][0];
    }
}
```

```cpp
class Solution {
public:
    bool hasValidPath(vector<vector<char>>& grid) {
        int r = grid.size();
        int c = grid[0].size();

        int pathLen = (r - 1) + (c - 1) + 1;

        if (pathLen % 2 == 1) {
            return false;
        }

        if (grid[0][0] != '(' || grid[r - 1][c - 1] != ')') {
            return false;
        }

        vector<vector<vector<bool>>> dp(
            r, vector<vector<bool>>(c, vector<bool>(pathLen + 1, false))
        );

        dp[0][0][1] = true;

        for (int i = 0; i < r; ++i) {
            for (int j = 0; j < c; ++j) {

                int change = grid[i][j] == '(' ? 1 : -1;

                if (i > 0) {
                    for (int openCount = 0; openCount <= pathLen; ++openCount) {

                        if (!dp[i - 1][j][openCount]) {
                            continue;
                        }

                        int newOpenCount = openCount + change;

                        if (newOpenCount >= 0) {
                            dp[i][j][newOpenCount] = true;
                        }
                    }
                }

                if (j > 0) {
                    for (int openCount = 0; openCount <= pathLen; ++openCount) {

                        if (!dp[i][j - 1][openCount]) {
                            continue;
                        }

                        int newOpenCount = openCount + change;

                        if (newOpenCount >= 0) {
                            dp[i][j][newOpenCount] = true;
                        }
                    }
                }
            }
        }

        return dp[r - 1][c - 1][0];
    }
};
```

```python
class Solution:
    def hasValidPath(self, grid):
        r = len(grid)
        c = len(grid[0])

        pathLen = (r - 1) + (c - 1) + 1

        if pathLen % 2 == 1:
            return False

        if grid[0][0] != '(' or grid[r - 1][c - 1] != ')':
            return False

        dp = [
            [
                [False] * (pathLen + 1)
                for _ in range(c)
            ]
            for _ in range(r)
        ]

        dp[0][0][1] = True

        for i in range(r):
            for j in range(c):

                change = 1 if grid[i][j] == '(' else -1

                if i > 0:
                    for openCount in range(pathLen + 1):

                        if not dp[i - 1][j][openCount]:
                            continue

                        newOpenCount = openCount + change

                        if newOpenCount >= 0:
                            dp[i][j][newOpenCount] = True

                if j > 0:
                    for openCount in range(pathLen + 1):

                        if not dp[i][j - 1][openCount]:
                            continue

                        newOpenCount = openCount + change

                        if newOpenCount >= 0:
                            dp[i][j][newOpenCount] = True

        return dp[r - 1][c - 1][0]
```
