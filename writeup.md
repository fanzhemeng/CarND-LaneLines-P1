# **Finding Lane Lines on the Road** 


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied Gaussian bluring with kernel size of 5. After that, I applied Canny edge detection with low_threshold=50 and high_threshold=150 to detect edges. Then I imposed a region mask to get desired edges for lane lines. Finally I did Hough transform to draw the lines on original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by 
(1) put all lines into two groups, which are if slope is positive or negative. The two group corresponds to right lane and left lane. 
(2) for each group, I average all slopes and endpoints of all lines, so that we have a slope and one point. Using these I can calculate the intersection of the line with top and bottem frame
(3) A same region of interest mask is applied to get desired portion of both lines



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when it encounters sharp turns as in the optinal challenge at the end of project. In such case, the lave lines appears to be curves but not lines, then we cannot correctly detect them with current pipeline.

Another shortcoming could be it may not work well when there are more than two lane lines in the view.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to try to fit curves for lane lines instead of straight lines.

