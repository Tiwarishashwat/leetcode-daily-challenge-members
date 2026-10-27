```java
class Solution {
    public String[] createGrid(int m, int n) {
        String res[] = new String[m];
        StringBuilder row = new StringBuilder("");
        for(int j=0;j<n;j++){
            if(j==0){
                row.append(".");
            }else{
                row.append("#");
            }
        }
        StringBuilder lastRow = new StringBuilder("");
        for(int i=0;i<n;i++){
            lastRow.append(".");
        }
        res[m-1] = lastRow.toString();
        for(int i=0;i<m-1;i++){
            res[i] = row.toString();
        }
        return res;
    }
}
```
```cpp
class Solution {
public:
    vector<string> createGrid(int m, int n) {
        vector<string> res(m);

        string row = ".";
        row += string(n - 1, '#');

        string lastRow(n, '.');

        res[m - 1] = lastRow;

        for (int i = 0; i < m - 1; i++) {
            res[i] = row;
        }

        return res;
    }
};
```
```python
class Solution:
    def createGrid(self, m: int, n: int) -> list[str]:
        res = [""] * m

        row = "." + "#" * (n - 1)
        last_row = "." * n

        res[m - 1] = last_row

        for i in range(m - 1):
            res[i] = row

        return res
```
