# Pedestrian_detection_EE722_course_project

This is an implementation of the HOG + SVM approach for pedestrian detection first done by Dalal & Triggs in their paper [Histograms of Oriented Gradients for Human Detection] (https://lear.inrialpes.fr/people/triggs/pubs/Dalal-cvpr05.pdf) in 2005.

## Objectives :
1. Get HOG features using opencv or skimage on images of size 64*128.
2. Detect pedestrians in the image using SVM.

## Dataset :
[ETHZ] (https://data.vision.ee.ethz.ch/cvl/aess/dataset/)\
To create the positive samples we can used the annotation provided by them and negative samples were generated by sampling some random points in each image. Since, the number of pedestrians are generally less random sampling gives us negative samples.

## Training and Hyper-parameter tuning :
We have tried 2 ways to detect pedetrians in the image.\
(i) Load the pre-trained Linear SVM model from openCV.\
(ii) Train a SVM with rbf kernel only on this dataset and see the results after NMS (Non-max suppression).

## Testing :


## Results : 



# References :
