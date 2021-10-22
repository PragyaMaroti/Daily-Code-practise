- Problem Link:  https://leetcode.com/problems/container-with-most-water/

- Problem:  
Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of the line i is at (i, ai) and (i, 0). Find two lines, which, together with the x-axis forms a container, such that the container contains the most water.

Notice that you may not slant the container.


- Solution: 
```cpp


int maxArea(int* height, int heightSize){

    
    int max=0;
    int i=0,j=heightSize-1;
    int area=0;
    while(i<j){
            if(height[i]<height[j])
            {
                area=(j-i)*height[i];
         i++;
            } 
            else
            {
                area=(j-i)*height[j];
                j--;
            }        
        
            
           // if(height[i]<height[j])
                
               
            //else
               
            if(max<area)
                max=area;
           
            }
return max;

}     
    
    
    
    
    
    
