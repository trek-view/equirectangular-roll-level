# 360 Equirectangular image analysis to identify roll

In this repo we will look at a deep learning method to find the camera roll.
Lets get started!

## Introdution

As we took equirectangular photos from the camera, we started identifying the roll values by the shape of the sine wave. So, we decided why not try Machine Learning method to figure out the camera roll values automatically from the photos.

## Tools Used

* Python
* Tensorflow
* Numpy
* Matplotlib

## Project Description

Data: We took some images of varying roll values and placed them in folder that specified their roll values. The image_dataset_from_directory method automatically labels the images by the their parent directory name. The labels were 0, 45, 90, 135, 180, 225, 270, 315, 360.

Model: We Used a pre-trained VGG-16 model for identifying roll values. The optimizer used in the model was RMSprop with learning rate of .0001 and the loss function was categorical_crossentropy. We trained the model for 30 epochs.

Results: We got 88% accuracy on the training data and 84% accuracy on validation data(which was used for tuning the hyperparameters). We also made a separate directory for test data. The images in the test data was not seen by the model before and the model gave the accuracy of 75%. 

## Future Work

1. The dataset used for the training was quite small. The accuracy can be increased by using a larger dataset of images
2. Using more precise labelling technique, such as using a gyroscope with the camera. The gyroscope can be configured by using arduino. As the images will    be taken by the camera the gyroscope with the help of arduino can record the image label, which can later be used for training the model.
3. Updating the model by adding a regression network at the end and using L2 loss function (Mean Squared Loss). This will output a real number in the range    0-360.
