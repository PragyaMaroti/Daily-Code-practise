[Link](https://leetcode.com/problems/rectangle-area/)   

Description:  
Given the coordinates of two rectilinear rectangles in a 2D plane, return the total area covered by the two rectangles.

The first rectangle is defined by its bottom-left corner (ax1, ay1) and its top-right corner (ax2, ay2).

The second rectangle is defined by its bottom-left corner (bx1, by1) and its top-right corner (bx2, by2).



- Solution: 

```cpp
class Solution {
public:
    int computeArea(int ax1, int ay1, int ax2, int ay2, int bx1, int by1, int bx2, int by2) {
        // area1+ area2 - common area
        int  area1 = (ax1-ax2)* (ay1-ay2);
            if(area1<0)area1*= -1;
        int area2 = (bx1-bx2) * (by1-by2);
        if(area2<0)area2*= -1;
        
        int common_area ;
         int x1, x2, y1,y2, l=0, b=0;
         x1 = max(bx1, ax1); x2 = min (ax2, bx2);
        
        y1  = max(by1, ay1); y2 = min(by2, ay2);
        if(x1>x2 || y1>y2) return (area1+ area2);
         l = ((x1-x2)>0)?(x1-x2): (x2-x1); b= (y1-y2)>0 ?(y1-y2): (y2-y1);
        common_area = l*b;
        return (area1 +area2 -common_area);
        
    }
};
```

![image](https://user-images.githubusercontent.com/64036955/149754772-44949736-7b23-4d3b-81d0-52ecfb80b2e8.png)
