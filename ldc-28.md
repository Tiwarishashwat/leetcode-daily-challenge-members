```java
class Solution {
    public int minOperations(int[] nums) {
        final int n = nums.length;
        if (n == 1) {
            return 0;
        }
        int start = 0;
        while (nums[start] != 0) {
            start++;
        }
        boolean asc = true;
        boolean desc = true;
        for (int i = 1; i < n; i++) {
            int value = nums[(start + i) % n];
            if (value != i) {
                asc = false;
            }
            if (value != n - i) {
                desc = false;
            }
            if (!asc && !desc) {
                return -1;
            }
        }
        if (asc) {
            return Math.min(start, n - start + 2);
        }
        return Math.min(n - start, start + 2);
    }
}
```

```cpp

class Solution {
public:
    int minOperations(vector<int>& nums) {
        int n = nums.size();

        if (n == 1) {
            return 0;
        }

        int start = 0;
        while (nums[start] != 0) {
            start++;
        }

        bool asc = true;
        bool desc = true;

        for (int i = 1; i < n; i++) {
            int value = nums[(start + i) % n];

            if (value != i) {
                asc = false;
            }

            if (value != n - i) {
                desc = false;
            }

            if (!asc && !desc) {
                return -1;
            }
        }

        if (asc) {
            return min(start, n - start + 2);
        }

        return min(n - start, start + 2);
    }
};

```

```python

class Solution:
    def minOperations(self, nums: List[int]) -> int:
        n = len(nums)

        if n == 1:
            return 0

        start = 0
        while nums[start] != 0:
            start += 1

        asc = True
        desc = True

        for i in range(1, n):
            value = nums[(start + i) % n]

            if value != i:
                asc = False

            if value != n - i:
                desc = False

            if not asc and not desc:
                return -1

        if asc:
            return min(start, n - start + 2)

        return min(n - start, start + 2)

```
