```java
class Solution {
    public int countDaysTogether( String arriveAlice, String leaveAlice, String arriveBob, String leaveBob) {
        int[] days = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
        int[] prefixSum = new int[12];
        prefixSum[0] = days[0];
        for (int i = 1; i < 12; i++) {
            prefixSum[i] = prefixSum[i-1] + days[i];
        }
        int arriveAliceDay = findDay(arriveAlice, prefixSum);
        int leaveAliceDay = findDay(leaveAlice, prefixSum);
        int arriveBobDay = findDay(arriveBob, prefixSum);
        int leaveBobDay = findDay(leaveBob, prefixSum);
        int maxArrival = Math.max(arriveAliceDay, arriveBobDay);
        int minLeave = Math.min(leaveAliceDay,leaveBobDay);
        if(maxArrival<=minLeave){
            return minLeave - maxArrival + 1;
        }
        return 0;
    }

    private int findDay(String day, int[] prefixSum) {
        int month = Integer.parseInt(day.substring(0, 2));
        int date = Integer.parseInt(day.substring(3));
        int index = month-1;
        if(index==0){
            return date;
        }
        return prefixSum[index-1] + date;
    }
}
```
```python

class Solution:
    def countDaysTogether(self, arriveAlice: str, leaveAlice: str,
                          arriveBob: str, leaveBob: str) -> int:
        days = [31, 28, 31, 30, 31, 30,
                31, 31, 30, 31, 30, 31]

        prefixSum = [0] * 12
        prefixSum[0] = days[0]

        for i in range(1, 12):
            prefixSum[i] = prefixSum[i - 1] + days[i]

        arriveAliceDay = self.findDay(arriveAlice, prefixSum)
        leaveAliceDay = self.findDay(leaveAlice, prefixSum)
        arriveBobDay = self.findDay(arriveBob, prefixSum)
        leaveBobDay = self.findDay(leaveBob, prefixSum)

        maxArrival = max(arriveAliceDay, arriveBobDay)
        minLeave = min(leaveAliceDay, leaveBobDay)

        if maxArrival <= minLeave:
            return minLeave - maxArrival + 1

        return 0

    def findDay(self, day: str, prefixSum: list[int]) -> int:
        month = int(day[:2])
        date = int(day[3:])
        index = month - 1

        if index == 0:
            return date

        return prefixSum[index - 1] + date

```
```cpp

class Solution {
public:
    int countDaysTogether(string arriveAlice, string leaveAlice,
                          string arriveBob, string leaveBob) {
        int days[] = {31, 28, 31, 30, 31, 30,
                      31, 31, 30, 31, 30, 31};

        int prefixSum[12];
        prefixSum[0] = days[0];

        for (int i = 1; i < 12; i++) {
            prefixSum[i] = prefixSum[i - 1] + days[i];
        }

        int arriveAliceDay = findDay(arriveAlice, prefixSum);
        int leaveAliceDay = findDay(leaveAlice, prefixSum);
        int arriveBobDay = findDay(arriveBob, prefixSum);
        int leaveBobDay = findDay(leaveBob, prefixSum);

        int maxArrival = max(arriveAliceDay, arriveBobDay);
        int minLeave = min(leaveAliceDay, leaveBobDay);

        if (maxArrival <= minLeave) {
            return minLeave - maxArrival + 1;
        }

        return 0;
    }

private:
    int findDay(string day, int prefixSum[]) {
        int month = stoi(day.substr(0, 2));
        int date = stoi(day.substr(3));
        int index = month - 1;

        if (index == 0) {
            return date;
        }

        return prefixSum[index - 1] + date;
    }
};

```
