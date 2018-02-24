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

My pipeline consists of 5 steps. First, I converted the images to grayscale, then I applied gaussian smoothing with kernel size 5, a canny edge filter, some masking using a trapezoid and finally a hough transform to identify the dominant lines.  

In order to draw a single line on the left and right lanes, I modified the draw_lines() function such that it identifies a left line versus a right line based on the line position within the image. The draw line function avergaes a left and right line segments. Furthermore the draw line functions extrapolates the resulting averaged left and right line segment along the entire region of interest. The region of interest is identified based on the calculated intersection point of the resulting averaged left and right lines.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when trees or traffic signs with identifiable line segments appear above the lane. 

Another shortcoming could be if the car is not centered in between the left and right line. This will lead to failure of the line classification as left or right line.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use the slope information and apply some statistics in order to identify the most likely left and right line.
