```java
class Solution {
    public int minSwaps(int[] nums) {
        int n = nums.length;
        int[] digitSum = new int[n];
        for (int i = 0; i < n; i++) {
            int x = nums[i],
                sum = 0;
            while (x > 0) {
                sum += x % 10;
                x /= 10;
            }
            digitSum[i] = sum;
        }
        Integer[] indices = new Integer[n];
        for (int i = 0; i < n; i++) {
            indices[i] = i;
        }
        Arrays.sort(indices, (a, b) -> {
            if (digitSum[a] != digitSum[b]) {
                return Integer.compare(digitSum[a], digitSum[b]);
            }
            return Integer.compare(nums[a], nums[b]);
        });

        int[] targetPos = new int[n];
        for (int pos = 0; pos < n; pos++) {
            targetPos[indices[pos]] = pos;
        }

        int[] parent = new int[n];
        int[] rank = new int[n];
        for (int i = 0; i < n; i++) {
            parent[i] = i;
        }
        int components = n;
        for (int i = 0; i < n; i++) {
            int rootElement1 = find(parent, i);
            int rootElement2 = find(parent, targetPos[i]);
            if(rootElement1 == rootElement2){
                continue;
            }
            components--;
            if(rank[rootElement1] < rank[rootElement2]){
                parent[rootElement1] = rootElement2;
            } else if(rank[rootElement2] < rank[rootElement1]){
                parent[rootElement2] = rootElement1;
            } else{
                parent[rootElement2] = rootElement1;
                rank[rootElement1]++;
            }
        }
        return n - components;
    }

    private int find(int[] parent, int element) {
        if(element == parent[element]){
            return element;
        }
        parent[element] = find(parent, parent[element]);
        return parent[element];
    }
}
```
```cpp
class Solution {
public:
    int find(vector<int>& parent, int element) {
        if (element == parent[element]) {
            return element;
        }
        return parent[element] = find(parent, parent[element]);
    }

    int minSwaps(vector<int>& nums) {
        int n = nums.size();
        vector<int> digitSum(n);

        for (int i = 0; i < n; i++) {
            int x = nums[i], sum = 0;
            while (x > 0) {
                sum += x % 10;
                x /= 10;
            }
            digitSum[i] = sum;
        }

        vector<int> indices(n);
        iota(indices.begin(), indices.end(), 0);

        sort(indices.begin(), indices.end(), [&](int a, int b) {
            if (digitSum[a] != digitSum[b]) {
                return digitSum[a] < digitSum[b];
            }
            return nums[a] < nums[b];
        });

        vector<int> targetPos(n);
        for (int pos = 0; pos < n; pos++) {
            targetPos[indices[pos]] = pos;
        }

        vector<int> parent(n), rank(n, 0);
        iota(parent.begin(), parent.end(), 0);

        int components = n;

        for (int i = 0; i < n; i++) {
            int root1 = find(parent, i);
            int root2 = find(parent, targetPos[i]);

            if (root1 == root2) {
                continue;
            }

            components--;

            if (rank[root1] < rank[root2]) {
                parent[root1] = root2;
            } else if (rank[root2] < rank[root1]) {
                parent[root2] = root1;
            } else {
                parent[root2] = root1;
                rank[root1]++;
            }
        }

        return n - components;
    }
};
```
```python
class Solution:
    def find(self, parent, element):
        if element == parent[element]:
            return element

        parent[element] = self.find(parent, parent[element])
        return parent[element]

    def minSwaps(self, nums: list[int]) -> int:
        n = len(nums)
        digit_sum = [0] * n

        for i in range(n):
            x = nums[i]
            total = 0

            while x > 0:
                total += x % 10
                x //= 10

            digit_sum[i] = total

        indices = list(range(n))

        indices.sort(key=lambda i: (digit_sum[i], nums[i]))

        target_pos = [0] * n

        for pos in range(n):
            target_pos[indices[pos]] = pos

        parent = list(range(n))
        rank = [0] * n

        components = n

        for i in range(n):
            root1 = self.find(parent, i)
            root2 = self.find(parent, target_pos[i])

            if root1 == root2:
                continue

            components -= 1

            if rank[root1] < rank[root2]:
                parent[root1] = root2
            elif rank[root2] < rank[root1]:
                parent[root2] = root1
            else:
                parent[root2] = root1
                rank[root1] += 1

        return n - components
```
