```java
class Solution {
    public int minSumOfLengths(int[] arr, int target) {
        int start=0;
        int end=0;
        int n = arr.length;
        int minLen=Integer.MAX_VALUE;
        int best[] = new int[n];
        Arrays.fill(best,Integer.MAX_VALUE);
        int sum=0;
        int ans=Integer.MAX_VALUE;
        while(end<n){
            //expand
            sum+=arr[end];
            end++;
            //shrink

            while(sum>target && start<end){
                sum-=arr[start];
                start++;
            }
            if(sum == target){
                int curLen = end-start;
                minLen = Math.min(minLen, curLen);
                //ans
                if(start>0 && best[start-1]!=Integer.MAX_VALUE){
                    ans = Math.min(ans, curLen + best[start-1]);
                }
            }
            best[end-1] = minLen;
        }
        return (ans==Integer.MAX_VALUE) ? -1 : ans;
    }
}
```

```c++
class Solution {
public:
    int minSumOfLengths(vector<int>& arr, int target) {

        int start = 0;
        int end = 0;
        int n = arr.size();

        int minLen = INT_MAX;
        vector<int> best(n, INT_MAX);

        int sum = 0;
        int ans = INT_MAX;

        while (end < n) {

            // expand
            sum += arr[end];
            end++;

            // shrink
            while (sum > target && start < end) {
                sum -= arr[start];
                start++;
            }

            if (sum == target) {
                int curLen = end - start;

                minLen = min(minLen, curLen);

                // ans
                if (start > 0 && best[start - 1] != INT_MAX) {
                    ans = min(ans, curLen + best[start - 1]);
                }
            }

            best[end - 1] = minLen;
        }

        return (ans == INT_MAX) ? -1 : ans;
    }
};
```


```python
class Solution:
    def minSumOfLengths(self, arr, target):
        start = 0
        end = 0
        n = len(arr)

        minLen = float('inf')
        best = [float('inf')] * n

        total = 0
        ans = float('inf')

        while end < n:

            # expand
            total += arr[end]
            end += 1

            # shrink
            while total > target and start < end:
                total -= arr[start]
                start += 1

            if total == target:
                curLen = end - start

                minLen = min(minLen, curLen)

                # ans
                if start > 0 and best[start - 1] != float('inf'):
                    ans = min(ans, curLen + best[start - 1])

            best[end - 1] = minLen

        return -1 if ans == float('inf') else ans
```
