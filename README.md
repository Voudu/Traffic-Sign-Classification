# Traffic-Sign-Classification
A Traffic sign classification system created using python and TensorFlow, and trained on the GTSRB dataset.
The objective of this program is to demonstrate the ability to classify road indicators, such as signage, in live footage.

# TODO:
* Handle video (input and post-processing)
* Extract bounding boxes (and relevant information)
* Test and Statistics

# Core Model Functionality
Classifies traffic signs into 43 classes using the GTSRB dataset. The model classifies traffic signs into 43 different classes.

# Dataset
We will use the GTSRB benchmark dataset (https://www.kaggle.com/datasets/meowmeowmeowmeowmeow/gtsrb-german-traffic-sign/data). which contains around 50,000+ images classified into 40+ individual classes. The dataset is partitioned like:
 * 35,000 training set
 * 4,500 images in the validation set
 * 12,600 images in the test set which
 * totals to ~51,000 images in the dataset

# Installation and Usage
We start off by first installing and then importing all the required dependencies such as the frameworks and libraries.

The data has already been split for us so we just load the data onto our jupyter notebook and then open it.

We shuffle the data and then convert the image to one dimension and apply normalization to get better results.

Now we start building the model:

Our first layer consists of a convolution layer of 20 nodes with a 3x3 filter and use the relu activation and then apply max pooling to it. We also apply dropout with 20%. The reason I added dropout was that when I trained the model earlier, I had seen high variance between the training and validation accuracies and so to reduce this variance, we apply dropout regularization.

Our second layer is similar to the first layer. The only difference I have done is to increase the number of nodes in the Convoluton layer to 30.

For passing on the output of our second layer to the Dense layer that we will add, we first need to flatten the output from the second layer and so we first add a Flatten layer. We now add a Dense layer with 128 nodes and the activation will be relu. In this layer, we also have L1-L2 regularization. We add one more Dense layer with 256 nodes but without regularization and the activation as relu.

For our last layer, we add a softmax layer with 43 nodes since we have 43 classes to differentiate from.

This marks the completion of building the model. We now compile it using the Adam optimizer and the sparse categorical crossentropy loss. For checking our progress, we use the metrics as accuracy so that we can see the accuracy as well as the validation accuracy.

We finally train our model on the training set on a batch size of 32 for 40 epochs. At the end of our training we get an accuracy of 98.9% and a validation accuracy of 96.24%. We then evaluate our model on the test set accuracy and we see a test set accuracy of 95%.

We also plot the graphs to visualize the changes in both the accuracies as well as both the losses. We also visualize a few of our predictions.

Finally we save the weights separately as well as the whole model which also consists of the weights so that it can be loaded and used elsewhere.

The index for the 43 Classes are as listed below:

- 0 = Speed limit (20km/h)
- 1 = Speed limit (30km/h)
- 2 = Speed limit (50km/h)
- 3 = Speed limit (60km/h)
- 4 = Speed limit (70km/h)
- 5 = Speed limit (80km/h)
- 6 = End of speed limit (80km/h)
- 7 = Speed limit (100km/h)
- 8 = Speed limit (120km/h)
- 9 = No passing
- 10 = No passing for vehicles over 3.5 metric tons
- 11 = Right-of-way at the next intersection
- 12 = Priority road
- 13 = Yield
- 14 = Stop
- 15 = No vehicles
- 16 = Vehicles over 3.5 metric tons prohibited
- 17 = No entry
- 18 = General caution
- 19 = Dangerous curve to the left
- 20 = Dangerous curve to the right
- 21 = Double curve
- 22 = Bumpy road
- 23 = Slippery road
- 24 = Road narrows on the right
- 25 = Road work
- 26 = Traffic signals
- 27 = Pedestrians
- 28 = Children crossing
- 29 = Bicycles crossing
- 30 = Beware of ice/snow
- 31 = Wild animals crossing
- 32 = End of all speed and passing limits
- 33 = Turn right ahead
- 34 = Turn left ahead
- 35 = Ahead only
- 36 = Go straight or right
- 37 = Go straight or left
- 38 = Keep right
- 39 = Keep left
- 40 = Roundabout mandatory
- 41 = End of no passing
- 42 = End of no passing by vehicles over 3.5 metric tons
