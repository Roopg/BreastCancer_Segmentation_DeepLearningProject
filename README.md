# BreastCancer_Segmentation_DeepLearningProject
A deep learning model that detects, classifies and segments breast cancer lesions in mammograms.
Public Mammogram datasets- CBIS-DDSM used for testing and training the deep learning model

Training Dataset: CBIS-DDSM (Curated Breast Imaging Subset of DDSM),includes decompressed images, data selection and curation by trained mammographers, updated mass segmentation and bounding boxes, and pathologic diagnosis for training data.The data set contains 753 calcification cases and 891 mass cases.
Metadata for each abnormality is included as an associated CSV file containing the following:

● Patient ID: the first 7 characters of images in the case file 
● Density category 
● Breast: Left or Right 
● View: CC or MLO
● Number of abnormality for the image (This is necessary as there are some cases containing multiple abnormalities. 
● Mass shape (when applicable)
● Mass margin (when applicable) 
● Calcification type (when applicable)
● Calcification distribution (when applicable) 
● BI-RADS assessment
● Pathology: Benign, Benign without call-back, or Malignant
● Subtlety rating: Radiologists’ rating of difficulty in viewing the abnormality in the image
● Path to image files There are individual files for mass and calcification training and test sets: 
● mass_case_description_train_set.csv 
● mass_case_description_test_set.csv
● calc_case_description_train_set.csv 
● calc_case_description_test_set.csv


Testing Dataset: We plan to use a different public dataset for testing-INbreast OR MIAS (availabel on Kaggle)

The code is divided into the following main sections-

1. Understanding and Visualizing the CBIS-DDSM dataset.
2. The dataset contains images, masks and ROI images, in a nested folder and the filenames do not help in identification of patient record or type of scan. Hence first step is to walk through the folders and rearrange the files and rename them at the same time.
3. The images are in the DICOM file format and we convert them to a 'jpg' format, in order to process them through our code
4. We perform a series of pre-procesisng steps- CLAHE filtering, Resizing to 512 x 512 ,Cropping the borders and to get the data ready for the machine learning pipeline.
5. The data is augmented using the keras imagedatageneraor and this includes- flip, rotate, shift etc. The same augmentation is applied to the mask as well.
6. Dataset is spilt into training, validation and testing.
7. Sanity checks are performed to ensure that Images and Masks are aligned at all times.
8. Basic U-Net model is defined using keras layers of Conv2D, Dropout,MaxPool, Concatenate and Skip connections.
9. Model compiled using "Dice" Metric and "Focal Loss" and Adam optimizers.
10. THe model is trained using callbacks and the saved model is used to predict a binary mask for the test images.
11. the predicted mask is compared to the actual ground truth images and the IOU (Jaccard Index) and Dice Coefficient(F score) is calculated.
12. 
13. 
