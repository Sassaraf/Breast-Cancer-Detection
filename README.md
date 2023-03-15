## Breast-Cancer-Detection


 
### Key Learnings

- 

- 

### Key Learnings

- Data Preprocessing:Problems: Images are different sizes with different aspect ratio, the background can be black and the image white, or vice versa. The image can be on the left side and on the right, in many images the empty background takes up a lot of space
Solution.
0 - convert all pixels to the range 0-255
1 - We need to determine which side of the image. To do this, we consider the standard deviation for the pixels on the left and right borders (10% of the image width on each side). The side with the background will have a smaller value. Next we mirror all the "right" images
2. Then we convert all the images into this format: dark background, light image. For this we count the sum of the pixel values for each side of the image (also 10% of the width). The left side is the image, the right side is the background. If the background is light, the sum will be greater. Then we invert the colors (255 minus the pixel value for each pixel)
3. Next, we crop the empty background to the right. To do this, we count the standard deviation of the pixels for each column in the loop from right to left. As soon as the value exceeds the threshold (in our case it is 4) it means that we have reached the image and crops this column
4. Now we need to convert the image to the same resolution. Let's perform the previous steps for 1000 images and calculate the ratio of height to width for the processed image. On average it is 4:1. So we chose a resolution of 2048*512
Add reshape as the last preprocessing step and run the script for all images


- Baseline model: Used pixel value as X. Random Forest showed 0 for each class (worked like a dummy classifier). Gaussian NB, showed something, but a lot of false positives.
There's not much to tell about the base model, the data is ready so you just have to put it into the model



### Files

- train_csv - CSV file for tabular data

- EDA - EDA on the tabular data 

- preprocess - for image preprocessing from .dcm to .jpg

- baseline_nb - Baseline model

- train_model - train the model on the train data

- cnn_v1_20_epoch - saved model, weights after training

- model _eval -run the model on the test data without training, for evaluation

