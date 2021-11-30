# Pedestrian_detection_EE722_course_project

This is an implementation of the HOG + SVM approach for pedestrian detection first done by Dalal & Triggs in their paper [Histograms of Oriented Gradients for Human Detection](https://lear.inrialpes.fr/people/triggs/pubs/Dalal-cvpr05.pdf) in 2005.

In this approach, we parse a window of fixed size over the whole image, and for each window we get a fixed number of HOG features which are then passed to a SVM to classify if a person is present or not.

## Objectives :
1. Get HOG features using opencv or skimage on images of size 64x128.
2. Detect pedestrians in the image using SVM.

## Dataset :
[ETHZ](https://data.vision.ee.ethz.ch/cvl/aess/dataset/)\
To create the positive samples we can used the annotation provided by them and negative samples were generated by sampling some random points in each image. Since, the number of pedestrians are generally less random sampling gives us negative samples.

## Training and Hyper-parameter tuning :
We have tried 2 ways to detect pedetrians in the image.\
(i) Load the pre-trained Linear SVM model from openCV.\
(ii) Train a SVM with rbf kernel only on this dataset and see the results after NMS (Non-max suppression).

The first approach involves using a `HoGDescriptor` from openCV whoce parameters can be set either using variables or using a .xml file. Here we have used the `hog.xml` file to set the parameters for the HOG.\
We set the SVM detector for this by using `setSVMDetector()` and then passing the `HOGDescriptor_getDefaultPeopleDetector()` from opencv into it. We put a threshold on the weight so that trees are not detected as pedestrians, which is quite a common error for a pre-trained model. `Opencv_HOG` contains the scripts for this.

In the second approach since there are not many negative samples given in the datatset hence choosing random windows and labelling them negative does work but still it is tough for the model to differentiate between the pedestrians and the side-walk. Hence, we decided to stick with the Linear SVM pre-trained on INRIA dataset. `HOG_SVM_train` conatins the notebook for training the SVM and testing.

## Results : 
<img src="https://github.com/Dibyakanti/Pedestrian_detection_EE722_course_project/blob/main/results/1.png">

The blue rectangles represent the ones not selected by non-max supression.
<img src="https://github.com/Dibyakanti/Pedestrian_detection_EE722_course_project/blob/main/results/2.png">

This is an example when a non-human object gets chosen as a pedestrian.
<img src="https://github.com/Dibyakanti/Pedestrian_detection_EE722_course_project/blob/main/results/3.png">
<p float="left">
  <img src="https://github.com/Dibyakanti/Pedestrian_detection_EE722_course_project/blob/main/results/4.png" width="100" />
  <img src="https://github.com/Dibyakanti/Pedestrian_detection_EE722_course_project/blob/main/results/5.png" width="100" /> 
  <img src="https://github.com/Dibyakanti/Pedestrian_detection_EE722_course_project/blob/main/results/6.png" width="100" />
</p>
<!-- <img src="https://github.com/Dibyakanti/Pedestrian_detection_EE722_course_project/blob/main/results/4.png">
<img src="https://github.com/Dibyakanti/Pedestrian_detection_EE722_course_project/blob/main/results/5.png">
<img src="https://github.com/Dibyakanti/Pedestrian_detection_EE722_course_project/blob/main/results/6.png">
<img src="https://github.com/Dibyakanti/Pedestrian_detection_EE722_course_project/blob/main/results/7.png"> -->

#### tSNE plot of the HOG features classified using the SVM classifier. (orange-1,blue-0)
<img src="https://github.com/Dibyakanti/Pedestrian_detection_EE722_course_project/blob/main/results/tSNE-plot.png">
