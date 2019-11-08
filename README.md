# Turn OFF the Lights
An image processing pipeline that applies Holistically-Nested Edge Detection (HED) and a discriminative correlation filter tracker with Channel and Spatial Reliability (CSRT). HED is used for 'hiding in the dark' a set of juggling balls while CSRT is used for tracking this set of juggling balls. 

In addition this repo includes useful features for other video processing tasks:
- Rotate Video
- Add Border to Video
- Add Text to Video
- Add an Image for a certain time in a video
- Track object backwards in time in a video

This repo is inspired on PyImageSearch amazing tutorials: [HED](https://www.pyimagesearch.com/2019/03/04/holistically-nested-edge-detection-with-opencv-and-deep-learning/) and [Track](https://www.pyimagesearch.com/2018/07/30/opencv-object-tracking/) 

[//]: # (----Image References List ---)
[image1]: ./README_images/demo.gif
[image2]: ./README_images/rotate.PNG
[image3]: ./README_images/enumerate.PNG
[image4]: ./README_images/hed.PNG
[image5]: ./README_images/intervals.PNG
[image6]: ./README_images/tracking.PNG
[image7]: ./README_images/border.PNG
[image8]: ./README_images/text.PNG
[image9]: ./README_images/question.PNG

![alt text][image1]


## Directory Structure
```
.Turn-OFF-The-Lights
├── demo.ipynb                   # Main file
├── .gitignore                   # git file to prevent unnecessary files from being uploaded
├── README_images                # Images used by README.md
│   └── ...
├── README.md
├── hed_model                    # HED Neural Network information
│   ├── deploy.prototxt                   # Model (architecture)
│   └── hed_pretrained_bsds.caffemodel    # Weights of Model
├── Input_Videos                 # Input Video directory
│   └── sample.mp4
├── Output_Videos                # output directory generated automatically once you run demo.ipynb
    └── ...
```

## Demo File
It is formed of the following subsections:
- Watch Input Video 
    - Needs Rotation?
- Enumerate Frames of Video
- HED Image Processing:
    - Split & Concatenate Small Clips
- Tracking Balls
- Add Borders
- Add Text
- Add Question Game Frame (Add Image to Video)

### Watch Input Video 
Loads/Reads the sample video in `Input_Video`. To add your own video, change info in cell 3 from `demo.ipynb`

### Needs Rotation?
I recorded my video with my phone in horizontal position. So I need to rotate it. If you do not need to rotate your video just skip this subsection.

![alt text][image2]

### Enumerate Frames of Video
The reason we need to enumerate the frames of our video is to know what frames we would like with the "lights OFF" ,i.e., what frame intervals we would like to pass through our HED neural network.

![alt text][image3]

### HED Image Processing
This subsection requires the model (architecture) of HED as well as the weights for the model. Therefore, this subsection makes use of a folder called `hed_model` where all of this is found.

![alt text][image4]

### Split & Concatenate Small Clips
This part prepares the frames that will go through HED by organizing the intervals in lists. In my case Frame intervals [93,184] , [465,1458], and [1588,1662] must be in the "dark." Therefore in seconds we get:

![alt text][image5]

### Tracking Balls
This section has a tricky part. Since the object I want to track is more visible in frame 1520, I will track the set of juggling balls in two parts. First I will track it backwards in time and then forwards, i.e., [1520 ,1459] and from [1520, 1587] In that way I will cover from frame 1459 until frame 1587.

![alt text][image6]

### Add Borders
Addition of movie-style borders.

![alt text][image7]

### Add Text
Addition of text in a video for the time specified.

![alt text][image8]

### Add Question Game Frame (Add Image to Video)
Addition of an image to a video for the time specified.

![alt text][image9]