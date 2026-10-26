```java

class Solution {
    static final int[] dr = {-1, 0, 1, 0};
    static final int[] dc = {0, 1, 0, -1};
    int m, n;
    public int countIslands(int[][] grid, int k) {
        m = grid.length;
        n = grid[0].length;
        // boolean[][] visited = new boolean[m][n];
        int count = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] > 0) {
                    long sum = dfs(i, j, grid);
                    if (sum % k == 0) {
                        count++;
                    }
                }
            }
        }
        return count;
    }
    private long dfs(int r, int c, int[][] grid) {
        if (r < 0 || r >= m || c < 0 || c >= n || grid[r][c] == 0) {
            return 0;
        }
        long sum = grid[r][c];
        grid[r][c] =0;
        // visited[r][c] = true;
        for (int i = 0; i < 4; i++) {
            int nr = r + dr[i];
            int nc = c + dc[i];
            sum += dfs(nr, nc, grid);
        }
        return sum;
    }
}

```
```cpp

class Solution {
    const int dr[4] = {-1, 0, 1, 0};
    const int dc[4] = {0, 1, 0, -1};
    int m, n;

public:
    int countIslands(vector<vector<int>>& grid, int k) {
        m = grid.size();
        n = grid[0].size();

        int count = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] > 0) {
                    long long sum = dfs(i, j, grid);

                    if (sum % k == 0) {
                        count++;
                    }
                }
            }
        }

        return count;
    }

private:
    long long dfs(int r, int c, vector<vector<int>>& grid) {
        if (r < 0 || r >= m || c < 0 || c >= n ||
            grid[r][c] == 0) {
            return 0;
        }

        long long sum = grid[r][c];
        grid[r][c] = 0;

        for (int i = 0; i < 4; i++) {
            int nr = r + dr[i];
            int nc = c + dc[i];

            sum += dfs(nr, nc, grid);
        }

        return sum;
    }
};

```
```python

class Solution:
    def countIslands(self, grid: List[List[int]], k: int) -> int:
        m, n = len(grid), len(grid[0])

        dr = [-1, 0, 1, 0]
        dc = [0, 1, 0, -1]

        def dfs(r, c):
            if (r < 0 or r >= m or c < 0 or c >= n
                    or grid[r][c] == 0):
                return 0

            total = grid[r][c]
            grid[r][c] = 0

            for i in range(4):
                nr = r + dr[i]
                nc = c + dc[i]
                total += dfs(nr, nc)

            return total

        count = 0

        for i in range(m):
            for j in range(n):
                if grid[i][j] > 0:
                    total = dfs(i, j)

                    if total % k == 0:
                        count += 1

        return count

```
