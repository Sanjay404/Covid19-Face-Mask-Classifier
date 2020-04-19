# Covid19 Face-Mask Classifier. 
  -  A LeNet Computer-vision model that can classify humans based on whether or not they are wearing a face mask. 
  -  Optimized from Santa/Not-Santa model: https://www.pyimagesearch.com/2017/12/11/image-classification-with-keras-and-deep-learning/ 
  
Uses a moderately sized dateset of  2323 images with masked and nonmasked individuals to train the model. The images was then split into training and validation data: 75% of the data was used for training and the remaining 25% was used for testing.

### Data Modeling
My input data consisted of 2323 RGB images with masked and nonmasked humans. Given a directory containing all the images, I iterate through, append a list representing the data with an array representation of the image, and then append another list called labels with a 1 if the path contains "mask" and 0 otherwise. The list containing data variable is then normalized and both label and data lists are re-assigned as numpy arrays. Finally the data is split up and divided into training and testing. Finally, the code uses an Keras' ImageDataGenerator to perfrom some transformations on the data, such as zooming or rotating the image,  to make it more impactful when training.


### Architecture:
I used a LeNet Architecture with a convolutional neural network because it is relatively 'cheap' in terms of computing. LeNet defines a sequential model with two sets of 2-Dimensional Convolutional Layers which include a Convo2D layer, Relu activation layer, and a MaxPooling2D layer to reduce the complexity/noise of the image (20 and 50 convultional filters in each respectively set). Subsequently, the model contains a flatten, dense, and relu layer, followed by another Dense and a softmax output layer.  
Finally, becuase this specific classification has only two possible outcomes I used 'binary crossentropy' as my loss function when compiling the LeNet model, along with the Adam optimizer and a constant learning rate. I then passed in my training and validation data which has been transformed as described in the above section.

### Limitations
The LeNet Architecture was originally developed for classifying the MNIST handwriting dataset; as a result, the inputted data is initially resized to a 28 by 28 array, which may cause some important features in the image to be reduced and classified as noise. As a result, the data i used for training contained images that were both zoomed on on a person's face and conversely zoomed out. In addition, I believe that the dataset I used can be further divsersified; however, I was limited by time and the scope of the internet. 

### Possible Improvements
 -  More data for training or data augmentation
 -  Another CNN for Facial recognition or an extremely effective algorithm for preprocessing the data and forming a 'region of interest' around a person's face(perhaps a modified Haar Cascade Classifier). This would work well with the LeNet, which resizes the image to a measly 28 by 28.
 -  Should someone wish to scale this model, I believe it to be on the verge of being extremely effective. Once again, the LeNet allows for classification at a extremely small cost (it does not even require a GPU). As a result, if a facial detection algorithm preprocesses the images and focuses on the target's face, the feature(in this case whether or not the target is wearing as mask), would remain significant.

