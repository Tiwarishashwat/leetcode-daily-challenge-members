```java
class Solution {
    public int sumCounts(List<Integer> nums) {
        int n = nums.size();
        int res = 0;
        for (int i = 0; i < n; i++) {
            Set<Integer> s = new HashSet<>();
            for (int j = i; j < n; j++) {
                s.add(nums.get(j));
                res += s.size() * s.size();
            }
        }
        return res;
    }
}
```

```cpp
class Solution {
public:
    int sumCounts(vector<int>& nums) {
        int n = nums.size();
        int res = 0;

        for (int i = 0; i < n; i++) {
            unordered_set<int> s;

            for (int j = i; j < n; j++) {
                s.insert(nums[j]);
                res += s.size() * s.size();
            }
        }

        return res;
    }
};
```

```python
class Solution:
    def sumCounts(self, nums: List[int]) -> int:
        n = len(nums)
        res = 0

        for i in range(n):
            s = set()

            for j in range(i, n):
                s.add(nums[j])
                res += len(s) * len(s)

        return res
```
