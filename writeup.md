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

My pipeline consisted of 5 steps
1. Read in an image
2. Create a polygon to mask out unimportant parts of the image
3. Convert the image to grayscale and blur the image
4. Use Canny algorithm to detect edges and use the previously created polygon to mask out unimportant parts
5. Use hough transform to find lines in the canny output image

In order to draw a single line on the left and right lanes I modified the draw_lines() function in the following way:
* Each pair of coordinates representing lines was used to find a slope and intercept
* The slopes and intercepts were seperated into left and right lanes based on the sign of the slope.
* The slopes and intercepts were then averaged to obtain final line equations
* This average line equation was used to draw a line across the bounds of the y axis

Working of the pipeline:

![solidWhiteCurve][test_images_output/solidWhiteCurve.jpg]
![solidWhiteRight][test_images_output/solidWhiteRight.jpg]
![solidYellowCurve][test_images_output/solidYellowCurve.jpg]
![solidYellowCurve2][test_images_output/solidYellowCurve2.jpg]
![solidYellowLeft][test_images_output/solidYellowLeft.jpg]
![whiteCarLaneSwitch][test_images_output/whiteCarLaneSwitch.jpg]


### 2. Identify potential shortcomings with your current pipeline


One shortcoming is that curved lane lines will cause the line equation to fail

Another shortcoming could be that sparse lane markings are picked up incorrectly


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to modify the hough algorithm to detect curved lines

Another potential improvement could be to tweak the line detection functions to be more robust.
