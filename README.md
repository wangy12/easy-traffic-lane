# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_image_output/solidYellowCurve.jpg

[image2]: ./test_image_output/solidWhiteRight.jpg

---


### 1. Describe pipeline.

## My pipeline consisted of 6 steps:

1) Convert the images to grayscale,

2) Apply Gaussian smoothing to blur the grayscale images,

3) Define low and high threshold and implement Canny edge detector,

4) Creat a four side polygon to mask the edges image,

5) Apply Hough transform to extract lines,

6) Draw lines on the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by separately averaging lines with positive slopes (left lanes) and negative slopes (right lanes).



![alt text][image1]
![alt text][image2]


### 2. Identify potential shortcomings


One potential shortcoming would be that are the parameters used in Canny and Hough general enough? I can see that the current parameters work well for the test images and test videos but not the challenge video. I don't think there exists optimal parameters or a set of parameters for the pipeline that works well for all scenarios. In other words, the pipeline is not robust. 



### 3. Suggest possible improvements

Possible improvements consist of:

1) A priori information about the field of view (FOV) of the camera is known, so that the four corners of the polygon to mask images can be properly configured. 

2) A priori information about the road is known, e.g., is the road straight or curve, is the road uphill or downhill. The polygon can be configured adaptively based on the road condition.

3) Select white and yellow from the images to detect edges and lines.

4) Adaptively configure the set of parameters in smoothing/polygon/Canny/Hough based on history data by the machine rather than hard code these parameters by human experience.

5) Apply Kalman-based filters on the slopes of left/right lanes: use Kalman filter to tackle miss detection of lanes and false alarm.

6) Train the machine to find the 'optimal' parameter set for Canny/Hough by supervised learning instead of tuning the parameters artificially. 

7) Develop metrics to evaluate the performance of lane detection.

