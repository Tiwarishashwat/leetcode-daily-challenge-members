```java
class Solution {
    public long[] resultArray(int[] nums, int k) {
        long dp[] = new long[k];
        long ans[] = new long[k];
        // N*K
        for(int num : nums){
            long newDp[] = new long[k];
            int rem = num%k;
            //a new subarray
            newDp[rem]++;
            //prev subarrays (extend)
            for(int r=0;r<k;r++){
               if(dp[r]>0){
                int newRem = (r * rem)%k;
                newDp[newRem] += dp[r];
               }
            }
            // update ans
            for(int r=0;r<k;r++){
                ans[r] += newDp[r];
            }
            dp = newDp;
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    vector<long long> resultArray(vector<int>& nums, int k) {

        vector<long long> dp(k, 0);
        vector<long long> ans(k, 0);

        // O(N * K)
        for (int num : nums) {

            vector<long long> newDp(k, 0);

            int rem = num % k;

            // Start a new subarray
            newDp[rem]++;

            // Extend previous subarrays
            for (int r = 0; r < k; r++) {
                if (dp[r] > 0) {
                    int newRem = (r * rem) % k;
                    newDp[newRem] += dp[r];
                }
            }

            // Update answer
            for (int r = 0; r < k; r++) {
                ans[r] += newDp[r];
            }

            dp = newDp;
        }

        return ans;
    }
};
```

```python
class Solution:
    def resultArray(self, nums, k):

        dp = [0] * k
        ans = [0] * k

        # O(N * K)
        for num in nums:

            new_dp = [0] * k

            rem = num % k

            # Start a new subarray
            new_dp[rem] += 1

            # Extend previous subarrays
            for r in range(k):
                if dp[r] > 0:
                    new_rem = (r * rem) % k
                    new_dp[new_rem] += dp[r]

            # Update answer
            for r in range(k):
                ans[r] += new_dp[r]

            dp = new_dp

        return ans
```




