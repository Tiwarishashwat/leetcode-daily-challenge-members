```java
class Solution {
    static final int[] dr = {-1, 0, 1, 0};
    static final int[] dc = {0, 1, 0, -1};
    int m=0;
    int n=0;
    public int closedIsland(int[][] grid) {
        m = grid.length;
        n = grid[0].length;
        int count = 0;
        for (int i = 0; i < grid.length; i++) {
            for (int j = 0; j < grid[0].length; j++) {
                if (grid[i][j] == 0){ 
                    if(dfs(i, j, grid)) {
                        count++;
                    }
                }
            }
        }
        return count;
    }

    public boolean dfs(int r, int c, int[][] grid) {
        if (r < 0 || r >= m || c < 0 || c >= n) {
            return false;
        }
        if (grid[r][c] == 1 || grid[r][c] == 2) {
            return true;
        }
        grid[r][c] = 2;
        boolean isClosed = true;
        for (int i = 0; i < 4; i++) {
            int nr = r + dr[i];
            int nc = c + dc[i];
            if (!dfs(nr, nc, grid)) {
                isClosed = false;
            }
        }

        return isClosed;
    }
}
```
```cpp

class Solution {
    int dr[4] = {-1, 0, 1, 0};
    int dc[4] = {0, 1, 0, -1};
    int m, n;

public:
    int closedIsland(vector<vector<int>>& grid) {
        m = grid.size();
        n = grid[0].size();

        int count = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == 0) {
                    if (dfs(i, j, grid)) {
                        count++;
                    }
                }
            }
        }

        return count;
    }

    bool dfs(int r, int c, vector<vector<int>>& grid) {
        if (r < 0 || r >= m || c < 0 || c >= n) {
            return false;
        }

        if (grid[r][c] == 1 || grid[r][c] == 2) {
            return true;
        }

        grid[r][c] = 2;
        bool isClosed = true;

        for (int i = 0; i < 4; i++) {
            int nr = r + dr[i];
            int nc = c + dc[i];

            if (!dfs(nr, nc, grid)) {
                isClosed = false;
            }
        }

        return isClosed;
    }
};

```
```python

class Solution:
    def closedIsland(self, grid: List[List[int]]) -> int:
        self.m = len(grid)
        self.n = len(grid[0])

        self.dr = [-1, 0, 1, 0]
        self.dc = [0, 1, 0, -1]

        count = 0

        for i in range(self.m):
            for j in range(self.n):
                if grid[i][j] == 0:
                    if self.dfs(i, j, grid):
                        count += 1

        return count

    def dfs(self, r: int, c: int, grid: List[List[int]]) -> bool:
        if r < 0 or r >= self.m or c < 0 or c >= self.n:
            return False

        if grid[r][c] == 1 or grid[r][c] == 2:
            return True

        grid[r][c] = 2
        isClosed = True

        for i in range(4):
            nr = r + self.dr[i]
            nc = c + self.dc[i]

            if not self.dfs(nr, nc, grid):
                isClosed = False

        return isClosed

```
