```java

class Solution {
    public int sortPermutation(int[] nums) {
        int n = nums.length;
        int k = Integer.MAX_VALUE;

        for (int i = 0; i < n; i++) {
            if (nums[i] != i) {
                k &= nums[i];
            }
        }

        return k == Integer.MAX_VALUE ? 0 : k;
    }
}
```
```cpp


class Solution {
public:
    int sortPermutation(vector<int>& nums) {
        int n = nums.size();
        int k = INT_MAX;

        for (int i = 0; i < n; i++) {
            if (nums[i] != i) {
                k &= nums[i];
            }
        }

        return k == INT_MAX ? 0 : k;
    }
};


```
```python
class Solution:
    def sortPermutation(self, nums: List[int]) -> int:
        n = len(nums)
        k = float('inf')

        for i in range(n):
            if nums[i] != i:
                k = nums[i] if k == float('inf') else k & nums[i]

        return 0 if k == float('inf') else k


```
