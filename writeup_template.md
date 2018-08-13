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

My pipeline consisted of 6 steps. First, I converted the images to grayscale, then I applied gaussian noise with kernel size 7.
I then applied canny transform with low threshold as 50 and high threshold as 150. The algorithm will detect strong gradients/edges above
the high threshold value and reject those below the low threshold value. I selected the region of interest using some hardcoded values. y-Minimum being 311.
I then got to draw lines on a blank image using the hough transform function. Lastly, I superimposed the original with the result from hough lines function to get the final image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by calculating the slope. I stored the end points
in two different arrays based on the slope. I averaged out individual points(x1,x2,y1,y2) for the left and right lane markers.
I used hardcoded minY value 311 for calculating slope and intercept for the mean values. Next step was to find  minX and maxX from slope, intercept, minX and maxY.
Finally, draw the line using thickness 14.
If you'd like to include images to show how the pipeline works, here is how to include an image:

![alt text][image1]: ./test_images_output/solidWhiteRight_Output.jpg "Solid White Right Output"]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the road is curved.

Another shortcoming could be when faced with intermittent light and shadows.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to average over similar looking frames and keeping history of slopes.

Another potential improvement could be to read positions, sizes and pertinent attributes of vehicles in the vicinity
 and come up with a probabilistic model of lanes.
