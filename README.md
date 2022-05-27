# YOLOV3_TO_TENSORFLOW_OBJECT_DETECTION
Yolo v3 detection  &lt;images/video> &lt;iou threshold> &lt;confidence threshold> &lt;filenames> . 
-Note that only one video can be processed at one run. 
-Note STILL NOT CONFIGURED FOR REALTIME  
-GLITCH IS SAYING HI HERE <3

HOW TO WORK :
-Add your custom weights file to weights folder and your custom .names file into data/labels folder.

-Change 'n_classes=80' on line 97 of load_weights.py to 'n_classes=<number of classes in .names file>'.
-Change './weights/yolov3.weights' on line 107 of load_weights.py to './weights/'.
-Change './data/labels/coco.names' on line 25 of detection.py to './data/labels/'
  
  -Save the weights in Tensorflow format ... YOLO_TO_TF_CONVERTOR.py
  -The script works on images, video or your webcam. Don't forget to set the IoU (Intersection over Union) and confidence thresholds ... detect.py
  -try this on terminal to make realtime detection on cam ... python detect.py webcam 0.5 0.5
  
  
  
  WHAT REALLY HAPPENDS IN CODES :
  
  - Skip first 5 values containing irrelevant info
  - Load weights for Darknet part.
  - Each convolution layer has batch normalization.
  - Loading weights for Yolo part.
  - 7th, 15th and 23rd convolution layer has (biases , no batch norm)
  - Performs a batch normalization using a standard set of parameters
  - Pads the input along the spatial dimensions independently of input size
  - Strided 2-D convolution with explicit padding
  - Creates a residual block for Darknet.
  - Creates Darknet53 model for feature extraction.
  - Creates convolution operations layer used after Darknet.
  - Creates Yolo final detection layer , boxes with respect to anchors.
  - Upsamples to `out_shape` using nearest neighbor interpolation.
  - Computes top left and bottom right points of the boxes
  - Performs non-max suppression separately for each class
  - Creates the model
  - Add operations to detect boxes for a batch of input images.
  - Draws detected boxes in a video frame.
  
  
  THATS IT <3
  
  
