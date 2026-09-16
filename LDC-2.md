```java
class Solution {
    static final int mod = 1_000_000_007;
    public int numberOfSets(int n, int k) {
        // 1D -> convert???
        // dp[n-1][k]
        long dp[][] = new long[n][k+1];
        long prefixSum[][] = new long[n][k+1];
        //base cases
        for(int i=0;i<n;i++){
            dp[i][0] = 1;
            prefixSum[i][0] = i+1;
        }
        // dp[0][0], dp[1][0], dp[2][0], dp[3][0]
        // 1,1,1,1
        // 1,2,3,4
        // for(int j=1;j<k;j++){
        //     dp[0][j] = 0;
        // }
        // N*K
        for(int i=1;i<n;i++){
            for(int j=1;j<=k;j++){
                //no pick
                dp[i][j] = dp[i-1][j];

                //pick
                dp[i][j] += prefixSum[i-1][j-1];
                dp[i][j] %= mod;
                prefixSum[i][j] = (prefixSum[i-1][j] + dp[i][j])%mod;
                // for(int start=0;start<=i-1;start++){
                //     dp[i][j] += dp[start][j-1];
                //     dp[i][j] %= mod;
                // }

            }
        }
        return (int)dp[n-1][k];
    }
}
```
```c++
class Solution {
public:
    static const int MOD = 1'000'000'007;

    int numberOfSets(int n, int k) {

        // dp[n][k]
        vector<vector<long long>> dp(n, vector<long long>(k + 1, 0));

        // prefixSum[n][k]
        vector<vector<long long>> prefixSum(
            n, vector<long long>(k + 1, 0)
        );

        // Base cases
        for (int i = 0; i < n; i++) {
            // 0 segments = 1 way
            dp[i][0] = 1;

            // prefix sum of dp[0][0] ... dp[i][0]
            prefixSum[i][0] = i + 1;
        }

        // O(N * K)
        for (int i = 1; i < n; i++) {

            for (int j = 1; j <= k; j++) {

                // NO PICK
                dp[i][j] = dp[i - 1][j];

                // PICK
                dp[i][j] += prefixSum[i - 1][j - 1];
                dp[i][j] %= MOD;

                // Update prefix sum
                prefixSum[i][j] =
                    (prefixSum[i - 1][j] + dp[i][j]) % MOD;
            }
        }

        return dp[n - 1][k];
    }
};
```

```python
class Solution:
    MOD = 1_000_000_007

    def numberOfSets(self, n: int, k: int) -> int:

        # dp[n][k]
        dp = [[0] * (k + 1) for _ in range(n)]

        # prefixSum[n][k]
        prefixSum = [[0] * (k + 1) for _ in range(n)]

        # Base cases
        for i in range(n):
            # 0 segments = 1 way
            dp[i][0] = 1

            # prefix sum of dp[0][0] ... dp[i][0]
            prefixSum[i][0] = i + 1

        # O(N * K)
        for i in range(1, n):

            for j in range(1, k + 1):

                # NO PICK
                dp[i][j] = dp[i - 1][j]

                # PICK
                dp[i][j] += prefixSum[i - 1][j - 1]
                dp[i][j] %= self.MOD

                # Update prefix sum
                prefixSum[i][j] = (
                    prefixSum[i - 1][j] + dp[i][j]
                ) % self.MOD

        return dp[n - 1][k]
```


