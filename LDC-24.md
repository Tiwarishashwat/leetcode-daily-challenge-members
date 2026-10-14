```java
class Solution {

    public String maxSumOfSquares(int num, int sum) {
        if (sum > 9 * num) {
            return "";
        }
        StringBuilder res = new StringBuilder();
        int totalNine = sum / 9;
        for (int i = 0; i < totalNine; i++) {
            res.append('9');
        }
        int r = sum % 9;
        if (r > 0) {
            res.append((char) ('0' + r));
        }
        int zeros = num - res.length();
        for (int i = 0; i < zeros; i++) {
            res.append('0');
        }
        return res.toString();
    }
}
```
```cpp
class Solution {
public:
    string maxSumOfSquares(int num, int sum) {
        if (sum > 9 * num) {
            return "";
        }

        string res = "";
        int totalNine = sum / 9;

        for (int i = 0; i < totalNine; i++) {
            res += '9';
        }

        int r = sum % 9;

        if (r > 0) {
            res += (char)('0' + r);
        }

        int zeros = num - res.length();

        for (int i = 0; i < zeros; i++) {
            res += '0';
        }

        return res;
    }
};
```
```python
class Solution:
    def maxSumOfSquares(self, num: int, sum: int) -> str:
        if sum > 9 * num:
            return ""

        res = ""
        totalNine = sum // 9

        for i in range(totalNine):
            res += '9'

        r = sum % 9

        if r > 0:
            res += str(r)

        zeros = num - len(res)

        for i in range(zeros):
            res += '0'

        return res
```
