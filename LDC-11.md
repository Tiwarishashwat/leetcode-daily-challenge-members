```java
class Solution {
    public String evaluate(String s, List<List<String>> knowledge) {
        //create a map
        HashMap<String,String> map = new HashMap<>();
        for(List<String> pair : knowledge){
            map.put(pair.get(0), pair.get(1));
        }
        int n = s.length();
        StringBuilder key = new StringBuilder("");
        StringBuilder res = new StringBuilder("");
        int i=0;
        while(i<n){
            if(s.charAt(i) == '('){
                i++; //(
                while(i<n && s.charAt(i)!=')'){
                    key.append(s.charAt(i));
                    i++;
                }
                if(map.containsKey(key.toString())){
                    res.append(map.get(key.toString()));
                }else{
                    res.append("?");
                }
                key.setLength(0);
            }else{
                res.append(s.charAt(i));
            }
            i++;
        }
        return res.toString();
    }
}
```

```cpp
class Solution {
public:
    string evaluate(string s, vector<vector<string>>& knowledge) {

        // create a map
        unordered_map<string, string> mp;

        for (auto& pair : knowledge) {
            mp[pair[0]] = pair[1];
        }

        int n = s.length();
        string key = "";
        string res = "";

        int i = 0;

        while (i < n) {

            if (s[i] == '(') {

                i++; // skip '('

                while (i < n && s[i] != ')') {
                    key += s[i];
                    i++;
                }

                if (mp.find(key) != mp.end()) {
                    res += mp[key];
                } else {
                    res += "?";
                }

                key.clear();

            } else {
                res += s[i];
            }

            i++;
        }

        return res;
    }
};
```

```python
class Solution:
    def evaluate(self, s: str, knowledge: list[list[str]]) -> str:

        # create a map
        mp = {}

        for pair in knowledge:
            mp[pair[0]] = pair[1]

        n = len(s)
        key = ""
        res = ""

        i = 0

        while i < n:

            if s[i] == '(':

                i += 1  # skip '('

                while i < n and s[i] != ')':
                    key += s[i]
                    i += 1

                if key in mp:
                    res += mp[key]
                else:
                    res += "?"

                key = ""

            else:
                res += s[i]

            i += 1

        return res
```
