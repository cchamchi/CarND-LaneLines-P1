# **Finding Lane Lines on the Road** 


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

My pipeline consisted of big 4 steps. First, I founded lane edges in the pitctue using canny algorithm. before the canny

I have to convert/modify the picture for the canny algorithm to find edges well. Because canny algorithm calculate gradient with

gray scale image, I converted target image to gray and modified it less sensitive using gaussian-blurr with kernel size 5

I tried 3/5/7 size of kernel, size 5 was best. 

The second is detect edges using canny algorithm. Because it found so many edges I have to pick the region of interest

The third is to figure out clean line from edges applying hough transform to detected edges.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by separating egdes with left and right group. From group of edges, I calculated a line y=Ax+b, A is slope and b is intersection. The library stats.linregress calculated slope/intersrctions. To draw lines in region of interest I calculated bottom point across the x axis 

And last I draw the lines on the image


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when lane is a curve. Becasue I assumed 1st-order line and across x-axis If the lane is curve the expectect line could be across y-axis 

Another shortcoming could be shadow. The canny could miss-understand shadow as line. and could be yellow line.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to find curved lane

Another potential improvement could be to detect shadow and yellow lane
