# **Finding Lane Lines on the Road** 

## Write up for CarND-LaneLines-P1


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Pipeline description

Color filter -> mask -> blur -> edge -> hough -> regression

My pipeline consists of 6 steps

Color filter. The first step is a filter to extract only white and yellow parts of the image that might correspond to lane lines

[image2]: ./results/color.jpg "Color"

Mask. The second step is a mask that filters out space where a line line could not be
Gaussian Blur. The third steps adds gaussian blur to remove high frequency noise and prepare the image for edge detection
Canny edge detector. The fourth filter applies canny edge detection to identify all the edges in the image.
Hough detector. The fifth filter applies the hough transform to detect which of these points are alighned in a line that might be a line
Linear regression. The sixth filter performs linear regression upon the Hough detected points to extraplote a continous line

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


There are several shortcomings with the current pipeline. First of all there are a lot of parameters and thresholds which are fix. These parameters should be adaptive based on the quality of the lines, weather, night or day situations, etc.
The biggest shortcoming in my opinion is that the algorithm doesnt't "know" what a lane line looks like, we are only filtering out lines, but not looking for the specific shapes of lane markings (rectangles with specific length and separation, continuous lines on the side of the road, etc.)


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to change the thresholds based on the image content, this would make the software more robust to changes

I think the biggest improvement could come from applying deep learning to the problem. With deep learning, a convolutional neural network could be trained to look specifically for lane lines, and not just any lines.
We could use the simple "hand crafted" algorithm to generate pseudolabels for the convolutional neural network and then add some noise and variations to force the neural network to obtain a more generalized solution.
I wanted to try this approach but I didn't have time in just one week. I might do this later or on the latest assginment of advanced lane detection.
