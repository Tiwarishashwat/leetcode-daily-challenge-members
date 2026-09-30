```java
class Solution {

    public int[] maxDepthAfterSplit(String seq) {
        int depth = 0;
        int length = seq.length();
        int[] ans = new int[length];
        for (int i = 0; i < length; i++) {
            if (seq.charAt(i) == '(') {
                depth++;
                //even
                if(depth%2==0){
                    ans[i] = 1;
                }
            } else {
                //odd
                if(depth%2==0){
                    ans[i] = 1;
                }
                depth--;
            }
        }
        return ans;
    }
}
```

```cpp
class Solution {
public:
    vector<int> maxDepthAfterSplit(string seq) {
        int depth = 0;
        int length = seq.length();
        vector<int> ans(length);

        for (int i = 0; i < length; i++) {
            if (seq[i] == '(') {
                depth++;

                // even
                if (depth % 2 == 0) {
                    ans[i] = 1;
                }
            } else {
                // odd
                if (depth % 2 == 0) {
                    ans[i] = 1;
                }

                depth--;
            }
        }

        return ans;
    }
};
```

```python
class Solution:
    def maxDepthAfterSplit(self, seq: str) -> list[int]:
        depth = 0
        length = len(seq)
        ans = [0] * length

        for i in range(length):
            if seq[i] == '(':
                depth += 1

                # even
                if depth % 2 == 0:
                    ans[i] = 1

            else:
                # odd
                if depth % 2 == 0:
                    ans[i] = 1

                depth -= 1

        return ans
```
