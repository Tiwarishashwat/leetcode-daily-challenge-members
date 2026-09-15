2472. Maximum Number of Non-overlapping Palindrome Substrings


```java
class Solution {
    public int maxPalindromes(String s, int k) {
        int count=0;
        int start=0;
        int n = s.length();
        //(N * K)
        while(start<n){
            //k len
            int end = start + k - 1;
            if(end>=n) break;
            if(isPalindrome(s, start, end)){
                count++;
                start = end+1;
                continue;
            }
            // k + 1 len
            end++;
            if(end>=n) break;
             if(isPalindrome(s, start, end)){
                count++;
                start = end+1;
                continue;
            }
            start++;
        }
        return count;
    }
    private boolean isPalindrome(String s, int start, int end){
        // K/2 , k+1/2
        while(start<end){
            if(s.charAt(start)!= s.charAt(end)){
                return false;
            }
            start++;
            end--;
        }
        return true;
    }
}
```

```c++
class Solution {
    public:
        int maxPalindromes(string s, int k) {
            int count = 0;
            int start = 0;
            int n = s.length();
    
            // O(N * K)
            while (start < n) {
    
                // k length
                int end = start + k - 1;
    
                if (end >= n)
                    break;
    
                if (isPalindrome(s, start, end)) {
                    count++;
                    start = end + 1;
                    continue;
                }
    
                // k + 1 length
                end++;
    
                if (end >= n)
                    break;
    
                if (isPalindrome(s, start, end)) {
                    count++;
                    start = end + 1;
                    continue;
                }
    
                start++;
            }
    
            return count;
        }
    
    private:
        bool isPalindrome(string& s, int start, int end) {
    
            // k/2, (k+1)/2
            while (start < end) {
    
                if (s[start] != s[end])
                    return false;
    
                start++;
                end--;
            }
    
            return true;
        }
    };
```

```python
class Solution:
    def maxPalindromes(self, s: str, k: int) -> int:
        count = 0
        start = 0
        n = len(s)

        # O(N * K)
        while start < n:

            # k length
            end = start + k - 1

            if end >= n:
                break

            if self.isPalindrome(s, start, end):
                count += 1
                start = end + 1
                continue

            # k + 1 length
            end += 1

            if end >= n:
                break

            if self.isPalindrome(s, start, end):
                count += 1
                start = end + 1
                continue

            start += 1

        return count

    def isPalindrome(self, s: str, start: int, end: int) -> bool:

        # k/2, (k+1)/2
        while start < end:

            if s[start] != s[end]:
                return False

            start += 1
            end -= 1

        return True
```