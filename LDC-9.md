```java
class Solution {
    public int smallestIndex(int[] nums) {
        int ans=-1;
        int n = nums.length;
        //N * log k base 10
        for(int i=0;i<n;i++){
            int num = nums[i];
            int sum=0;
            // log k to the base 10
            while(num>0){
                sum += (num%10);
                num = num/10;
            }
            if(i == sum){
                ans = i;
                break;
            }
        }
        return ans;   
    }
}
```

```cpp
class Solution {
public:
    int smallestIndex(vector<int>& nums) {

        int ans = -1;

        int n = nums.size();

        // N * log(k) base 10
        for (int i = 0; i < n; i++) {

            int num = nums[i];
            int sum = 0;

            // log(k) base 10
            while (num > 0) {
                sum += num % 10;
                num = num / 10;
            }

            if (i == sum) {
                ans = i;
                break;
            }
        }

        return ans;
    }
};
```

```python
class Solution:
    def smallestIndex(self, nums):

        ans = -1

        n = len(nums)

        # N * log(k) base 10
        for i in range(n):

            num = nums[i]
            sum = 0

            # log(k) base 10
            while num > 0:
                sum += num % 10
                num = num // 10

            if i == sum:
                ans = i
                break

        return ans
```
