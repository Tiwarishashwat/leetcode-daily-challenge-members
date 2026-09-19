```java
class Solution {
    public boolean checkOverlap(int radius, int xCenter, int yCenter, int x1, int y1, int x2, int y2) {
        double dist=0;
        int xDist=0;
        if(xCenter < x1){
            xDist = x1 - xCenter;
        } else if(xCenter > x2){
            xDist = x2 - xCenter;
        }

        int yDist=0;
        if(yCenter < y1){
            yDist = y1 - yCenter;
        } else if(yCenter > y2){
            yDist = y2 - yCenter;
        }

        dist = Math.pow(xDist,2) + Math.pow(yDist,2);
        return dist <= radius * radius;
    }
}
```

```cpp
class Solution {
public:
    bool checkOverlap(int radius, int xCenter, int yCenter,
                      int x1, int y1, int x2, int y2) {

        double dist = 0;

        int xDist = 0;

        if (xCenter < x1) {
            xDist = x1 - xCenter;
        } 
        else if (xCenter > x2) {
            xDist = x2 - xCenter;
        }

        int yDist = 0;

        if (yCenter < y1) {
            yDist = y1 - yCenter;
        } 
        else if (yCenter > y2) {
            yDist = y2 - yCenter;
        }

        dist = pow(xDist, 2) + pow(yDist, 2);

        return dist <= radius * radius;
    }
};
```

```python
class Solution:
    def checkOverlap(self, radius, xCenter, yCenter,
                     x1, y1, x2, y2):

        dist = 0

        xDist = 0

        if xCenter < x1:
            xDist = x1 - xCenter
        elif xCenter > x2:
            xDist = x2 - xCenter

        yDist = 0

        if yCenter < y1:
            yDist = y1 - yCenter
        elif yCenter > y2:
            yDist = y2 - yCenter

        dist = xDist ** 2 + yDist ** 2

        return dist <= radius ** 2
```




