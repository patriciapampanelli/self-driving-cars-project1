#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image0]: ./test_images/solidWhiteCurve.jpg "Input image"

[image1]: ./results/gray_solidWhiteCurve.jpg "Grayscale Image"

[image2]: ./results/gaussian_solidWhiteCurve.jpg "Gaussian Blur"

[image3]: ./results/cannyImage_solidWhiteCurve.jpg "Canny Edge-Detection"

[image4]: ./results/line_img_solidWhiteCurve.jpg "Lines"

[image5]: ./results/masked_image_solidWhiteCurve.jpg "Masked Image"

[image6]: ./results/solidWhiteCurveResult.jpg "Lane lines"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

The pipeline I designed for finding lane lines has the following steps:
- Read the input image:
![alt text][image0]
- Transform the input image from RGB to grayscale:
![alt text][image1]
- Apply a gaussian blur to the grayscale image with the kernel size of 7:
![alt text][image2]
- Find edges using canny edge detection method with these parameters: low_threshold = 25 and high_threshold = 75:
![alt text][image3]
- Find the region of interest:
![alt text][image4]
- Get the lines using Hough Transform using these parameters: max_line_gap = 2, min_line_len = 3, rho = 1, theta = np.pi/180, threshold = 50:
![alt text][image5]
- Finally, combine the output lines with the original image:
![alt text][image6]

First, in order to get a single line on the left and right, I evaluated the slope of each line. Then, I was able to distinguish left lines from the right lines. Finally, I draw these lines using the linear equation and fixing the ymax and ymin.


###2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be what would happen when the region of interest is different from the input images. In other words, it could be difficult to find the lane lines in a bigger dataset with a lot of different images. The images used in this project have similar parameters for the region of interest. Another shortcoming would be the gaussian parameters, that can be different for images with different noise rates.

###3. Suggest possible improvements to your pipeline

A possible improvement would be to get the region of interest automatically using a Machine Learning approaches to identifying them. The same thing can be done in order to get the gaussian kernel size.

This project could be also used as a preprocessing step to create a dataset where deep learning method could learn what a lane line is and then find them automatically.


