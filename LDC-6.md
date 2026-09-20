```java
class Solution {
    public int reverseDegree(String s) {
        int sum=0;
        int n=s.length();
        for(int i=0;i<n;i++){
            sum = sum + (('z' - s.charAt(i) + 1) * (i+1));
        }
        return sum;
    }
}
```


```python
class Solution:
    def reverseDegree(self, s: str) -> int:
        total = 0

        for i in range(len(s)):
            total += (ord('z') - ord(s[i]) + 1) * (i + 1)

        return total
```

```cpp
class Solution {
public:
    int reverseDegree(string s) {
        int sum = 0;

        for (int i = 0; i < s.length(); i++) {
            sum += ('z' - s[i] + 1) * (i + 1);
        }

        return sum;
    }
};
```

