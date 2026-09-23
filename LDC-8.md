```java
class Solution {
    public int minOperations(int[] nums, int x) {
        int n=nums.length;
        int total = 0;
        for(int num : nums){
            total += num;
        }
        if(total < x){
            return -1;
        }
        if(total == x){
            return n;
        }
        int target = total - x;
        int cur=0;
        int maxLen = Integer.MIN_VALUE;
        int l=0;
        int r=0;
        while(r<n) {
            //exp
            cur+=nums[r];
            r++;
            //shrinking
            while(l<r && cur > target){
                cur -= nums[l];
                l++;
            }
            if(cur == target){
                maxLen = Math.max(maxLen, r-l);
            }
        }
        return (maxLen == Integer.MIN_VALUE) ? -1 : n-maxLen;
    }
}
```

```cpp
class Solution {
public:
    int minOperations(vector<int>& nums, int x) {

        int n = nums.size();

        int total = 0;

        for (int num : nums) {
            total += num;
        }

        if (total < x) {
            return -1;
        }

        if (total == x) {
            return n;
        }

        int target = total - x;

        int cur = 0;
        int maxLen = INT_MIN;

        int l = 0;
        int r = 0;

        while (r < n) {

            // expand
            cur += nums[r];
            r++;

            // shrinking
            while (l < r && cur > target) {
                cur -= nums[l];
                l++;
            }

            if (cur == target) {
                maxLen = max(maxLen, r - l);
            }
        }

        return (maxLen == INT_MIN) ? -1 : n - maxLen;
    }
};
```

```python
class Solution:
    def minOperations(self, nums, x):

        n = len(nums)

        total = 0

        for num in nums:
            total += num

        if total < x:
            return -1

        if total == x:
            return n

        target = total - x

        cur = 0
        maxLen = -1

        l = 0
        r = 0

        while r < n:

            # expand
            cur += nums[r]
            r += 1

            # shrinking
            while l < r and cur > target:
                cur -= nums[l]
                l += 1

            if cur == target:
                maxLen = max(maxLen, r - l)

        return -1 if maxLen == -1 else n - maxLen
```
