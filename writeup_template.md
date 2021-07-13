# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, and then I utilized Gaussian blur to reduce the noise of the images. The next step consists of Canny edge detection with low and high thresholds of 50 and 150. By taking advantage of the "fillpoly()" function in OpenCV, I masked the undesired lines in the images. Finally, I used Hough transformation to draw lines on the images.

I modified the draw_lines() function by separating the left and right lines using their slope and x coordinate to draw a single line on the left and right lanes. To make it more robust, too large or too small slopes are filtered out. By averaging the parameters and calculating the intercepts, I then calculated each line's initial and end points. In the final step, the lines are drawn using the line function.


If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the camera is not positioned in the center. The region_of_interest() and draw_lines() functions are not robust to any changes in camera position. It would also be problematic in downhill or uphill and sharp curves.

Another shortcoming could be when other cars nearby or other lines on the road, such as crosswalks or directional arrows.



### 3. Suggest possible improvements to your pipeline

A possible improvement would be to considering curves instead of lines. Also, utilizing linear regression would be beneficial, although it would be computationally expensive. 

Another potential improvement could be to using higher-order polynomial with adaptive parameters to mask the images.

To enhance the efficiency of the pipeline in different light and weather conditions, updating the parameters of Gaussian blur, Canny edge detection, and Hough transformation would be effective.

