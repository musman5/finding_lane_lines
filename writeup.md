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

My pipeline consisted of multiple steps. First, I converted the images to grayscale and remove noise, then I used canny edge detection to detect edges. 
Next i extracted area of interest by giving co-ordinates of square. Then in the area of interest i used hough transform to detect the lines.

In order to draw a single line on the left and right lanes, i modified draw_lines() function to average and interpolate the lines. In the draw function i used slope and x,y co-ordinates to check which side of the image the line belong to. Now we have separated left and right lines based on slope, we can find average values for a single required line. Then after separating lines, i used polyfit function to extract m and b values for first degree polynomial. Using these values i figured out the x co-ordinates using y co-ordinates, m and b values. Then i draw the single result line on the image in red color. 

At the end wight function is applied to show semitransparent line on the image.

Example image:
![alt text][./test_images/output_solidWhiteCurve.jpg]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when some other lines appear on the road in area of interest.

Another shortcoming could be on curves the line average function does not work as required


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to improve this algorithm to use on curvy roads

Another potential improvement could be to remove garbage lines which do appear randomly on roads with actual lane lines in AOI
