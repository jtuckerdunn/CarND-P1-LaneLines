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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied gaussian blur smoothing to limit noise. I applied the annie function then created a quadrilateral image mask to limit the region of interest to the lane the car is driving in. I applied the hough transform using a modified draw lines function which identified lines associated with the left and right lane lines and averaged the slopes of those lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by dividing the hough lines into lines associated with the left or right lane by dividing them by whether they had a positive or a negative slope. Then I used the polyfit numpy function to average the slopes of all lines associated with one lane line into a single lane line.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the camera resolution changes. I used absolute pixel values for my image mask so it only works with the exact images I am using.

Another shortcoming could be that there could be situations where the camera angle or view changes. This would also throw off the image mask because it uses absolute values.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use a deep neural network with labeled training data that can learn where the lane lines are in a more robust fashion.

Another potential improvement could be to use data that varies in resolution and position so that I can ensure my model will be robust to changes in those variables.
