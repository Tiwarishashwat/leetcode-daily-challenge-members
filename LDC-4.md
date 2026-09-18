```java
class Solution {
    public List<String> maxNumOfSubstrings(String s) {
        //count
        int n = s.length();
        int first[] = new int[26];
        int last[] = new int[26];
        Arrays.fill(first,n);
        Arrays.fill(last,-1);
        //a ->0, b->1
        for(int i=0;i<n;i++){
           int index  = s.charAt(i) - 'a'; //a,c
           if(first[index]==n){
                first[index] = i;
           }
           last[index] = i;
        }
        List<int[]> intervals = new ArrayList<>();
        //valid ranges
        for(int i=0;i<26;i++){
            if(first[i]!=n){
                int l = first[i];
                int r = last[i];
                boolean isValid=true;
                for(int j=l;j<=r;j++){
                    char ch = s.charAt(j);
                    if(first[ch-'a'] < l){
                        isValid = false;
                        break;
                    }
                    r = Math.max(r,last[ch-'a']);
                }
                if(isValid){
                    intervals.add(new int[]{l,r});
                }
            }
        }
        intervals.sort((a,b) -> a[1] - b[1]);
        List<String> res = new ArrayList<>();
        int prevEnd=-1;
        for(int interval[] : intervals){
            if(interval[0] > prevEnd){
                res.add(s.substring(interval[0] , interval[1] + 1));
                prevEnd = interval[1];
            }
        }
        return res;
    }
}
```
```c++
class Solution {
public:
    vector<string> maxNumOfSubstrings(string s) {
        // count
        int n = s.size();

        vector<int> first(26, n);
        vector<int> last(26, -1);

        // a -> 0, b -> 1
        for (int i = 0; i < n; i++) {
            int index = s[i] - 'a';

            if (first[index] == n) {
                first[index] = i;
            }

            last[index] = i;
        }

        // valid ranges
        vector<pair<int, int>> intervals;

        for (int i = 0; i < 26; i++) {
            if (first[i] != n) {
                int l = first[i];
                int r = last[i];

                bool isValid = true;

                for (int j = l; j <= r; j++) {
                    int index = s[j] - 'a';

                    if (first[index] < l) {
                        isValid = false;
                        break;
                    }

                    r = max(r, last[index]);
                }

                if (isValid) {
                    intervals.push_back({l, r});
                }
            }
        }

        // Sort by ending position
        sort(intervals.begin(), intervals.end(),
             [](const auto& a, const auto& b) {
                 return a.second < b.second;
             });

        vector<string> res;
        int prevEnd = -1;

        for (auto& interval : intervals) {
            int l = interval.first;
            int r = interval.second;

            if (l > prevEnd) {
                res.push_back(s.substr(l, r - l + 1));
                prevEnd = r;
            }
        }

        return res;
    }
};
```
```python
class Solution:
    def maxNumOfSubstrings(self, s: str) -> list[str]:
        # count
        n = len(s)

        first = [n] * 26
        last = [-1] * 26

        # a -> 0, b -> 1
        for i, ch in enumerate(s):
            index = ord(ch) - ord('a')

            if first[index] == n:
                first[index] = i

            last[index] = i

        # valid ranges
        intervals = []

        for i in range(26):
            if first[i] != n:
                l = first[i]
                r = last[i]

                is_valid = True

                for j in range(l, r + 1):
                    index = ord(s[j]) - ord('a')

                    if first[index] < l:
                        is_valid = False
                        break

                    r = max(r, last[index])

                if is_valid:
                    intervals.append((l, r))

        # Sort by ending position
        intervals.sort(key=lambda interval: interval[1])

        res = []
        prev_end = -1

        for l, r in intervals:
            if l > prev_end:
                res.append(s[l:r + 1])
                prev_end = r

        return res
```


