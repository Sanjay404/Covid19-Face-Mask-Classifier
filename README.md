# Covid19 Face-Mask Classifier. 
  -  Computer-vision model that can classify humans based on whether or not they are wearing a face mask. 

Uses a moderately sized dateset of  2323 images with masked and nonmasked individuals to train the model. The images was then split into training and validation data: 75% of the data was used for training and the remaining 25% was used for testing.

### Data Modeling
My input data consisted of 2323 RGB images with masked and nonmasked humans.


### Architecture:
I used a LeNet Architecture with a convolutional neural network because it is relatively 'cheap' in terms of computing. LeNet defines a sequential model with two sets of 2-Dimensional Convolutional Layers which include a Convo2D layer, Relu activation layer, and a MaxPooling2D layer reduce the complexity/noise of the image (20 and 50 convultional filters in each respectively set). Subsequently, the model contains a flatten, dense, and relu layer, followed by another Dense and a softmax output layer.  
Finally, becuase this specific classification has only two possible outcomes I used 'binary crossentropy' as my loss function when compiling the LeNet model, along with the Adam optimizer and a constant learning rate. I then passed in my training and validation data.
