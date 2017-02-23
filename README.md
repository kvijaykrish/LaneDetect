# LaneDetect
carND Term1 Lane Detection Project

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Find lanes on provided Images
* Then find lanes on provided video and save the ouptut video. Hint video is a series of image frames.


---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of below steps. 

1. Convert the Image to gray scale
2. Define a kernel size and apply Gaussian smoothing
3. Apply Canny Edge Detection
4. Select region of interest based on the image size
5. Run Hough on edge detected image
6. Filter, Average and Extrapolate the raw line to draw solid lines from bottom of image to the region of interest

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by alternate lane_line_image() funtion. The steps done are:

1. Filter: use slope of lines to filter horizontal lines, 
2. Seperate Left, Right Lanes: Use slope to create two groups:  left and right lanes
3. Average: compute the average x1,y1, x2,y2 in left and right lanes
4. Extrapolate: use slope and intercept to extrpolate the lines to the region of interest
5. Draw solid line: Draw the extrapolated solid lane line


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when horizontal lanes are present during sharp turn at road intersections. Becuase presently horizontal lines are skipped.

Another shortcoming could be the difference in the road surface causes unwanted edges which might have to be filtered


###3. Suggest possible improvements to your pipeline

A possible improvement would be to adapt the parameters for edge detection, hough trasform based on the road, size of lane lines, gap between lane lines.

Another potential improvement could be to apply adaptive image filtering to compensate for the road surface, lighting, environment changes.
