```java
class Solution {
    int m, n;
    boolean[][][] memo;
    int ans = 1024;
    public int minCost(int[][] grid) {
        m = grid.length;
        n = grid[0].length;
        memo = new boolean[m][n][1024];
        dfs(grid, 0, 0, 0);
        return ans;
    }

    void dfs(int[][] grid, int i, int j, int xor) {
        xor ^= grid[i][j];

        if (memo[i][j][xor]) {
            return;
        }

        memo[i][j][xor] = true;

        if (i == m - 1 && j == n - 1) {
            ans = Math.min(ans, xor);
            return;
        }

        if (i + 1 < m) {
            dfs(grid, i + 1, j, xor);
        }

        if (j + 1 < n) {
            dfs(grid, i, j + 1, xor);
        }
    }
}
```
```cpp
class Solution {
public:
    int m, n;
    vector<vector<vector<bool>>> memo;
    int ans = 1024;

    int minCost(vector<vector<int>>& grid) {
        m = grid.size();
        n = grid[0].size();

        memo.assign(m, vector<vector<bool>>(n, vector<bool>(1024, false)));

        dfs(grid, 0, 0, 0);

        return ans;
    }

    void dfs(vector<vector<int>>& grid, int i, int j, int xorr) {
        xorr ^= grid[i][j];

        if (memo[i][j][xorr]) {
            return;
        }

        memo[i][j][xorr] = true;

        if (i == m - 1 && j == n - 1) {
            ans = min(ans, xorr);
            return;
        }

        if (i + 1 < m) {
            dfs(grid, i + 1, j, xorr);
        }

        if (j + 1 < n) {
            dfs(grid, i, j + 1, xorr);
        }
    }
};
```
```python
class Solution:
    def minCost(self, grid: List[List[int]]) -> int:
        m = len(grid)
        n = len(grid[0])

        memo = [[[False] * 1024 for _ in range(n)] for _ in range(m)]
        ans = 1024

        def dfs(i, j, xorr):
            nonlocal ans

            xorr ^= grid[i][j]

            if memo[i][j][xorr]:
                return

            memo[i][j][xorr] = True

            if i == m - 1 and j == n - 1:
                ans = min(ans, xorr)
                return

            if i + 1 < m:
                dfs(i + 1, j, xorr)

            if j + 1 < n:
                dfs(i, j + 1, xorr)

        dfs(0, 0, 0)

        return ans
```
