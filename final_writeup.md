#Finding Lane Lines on the Road
by Rakshith Krishnamurthy

### Reflection

### 1. Pipeline:

1. Convert the images to Gray Scale.
2. Then image is blurred using Gaussian Blur with kernel set to 5
3. Used the Canny Edge Detection method to detect the edges of the image/ video. For the video 55 to 165 ratio turned out to be good threshold values.
4. The region of interest was fixed for images and therefore the pipeline had constant pixel values. For the videos I used constant values at first but when I used it on the challenge video I realized that the pixel boundaries should be dynamic.
5. Hough Transform was used to identify the lines and draw them on final image based of slopes and intercepts. To draw the lines I used the mean values of slope and intercept. This worked well on images but not so well on videos and hence I had to change it to weighted average which performed better. Now, weighted average worked was not enough as it performed well on the videos but the challenge video needed more work. To smoothen out the challenge video I used the previous frames slope and intercept values. Using the previous frames values I could find a slope for the current frame by averaging it out with the current frames slope.
6. Challenge video also had issues finding weighted averages due to divide by zero errors and modification were made to draw_lines () function to consider values not equal to zero.

### 2. Shortcomings of the pipeline:

1. The pipeline works well when visibility of the lanes is good. For example in the challenge video there is a strip of road where the left and right lines are not well defined and the final lines constructed were not smooth when compared to the other videos.
2. This implementation can be used only on roads where there left and right lines are well defined lines.
3. The current pipeline also does not consider the aspect of switching lanes or curved roads well.


### 3. Improvements to your pipeline

1. The lane markings are straight and scope of improvement is to follow along the curve.
2. Improvement of the lanes visibility on different road surfaces.
3. The pipeline should improve for roads that are curved and area of interest should change.
