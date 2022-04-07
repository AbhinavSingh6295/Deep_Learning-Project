# Deep Learning Project

## Multi-image Segmentation using U-Net Architecture in Pytorch Framework

### Goal and Objective 
Goal was to implement and solve the remote sensing problem using the recent deep learning techniques. 
The main objective was to segment images acquired by a small UAV in the area of Houston, Texas. In total there are 25 categories of segments (ex - roof, trees, pools, etc.) and the task was to design and implement a deep learning model in order to perform the automatic segmentation of such images. 
The model was trained using train images which contained pixel-wise annotations. 
Using the trained model, a prediction on the test images was performed.

### Methodology - 
- **Dataset Preparation**: Data was available on Kaggle. We resized the images to (128 x 128) and (256 x 256) sets. 
For data normalization, we divided the pixel values by 255, so all the pixel value range between 0-1. 
On the augmentation side, we tried several image transformation: flipping vertically and horizontally, shifting, zooming and rotating by 45 degrees. 
Finally created a training and validation data.

<img src="https://github.com/AbhinavSingh6295/Deep_Learning-Project/blob/main/6496.jpg" alt="Sample Test Image" width="200" height="200" />

*Sample Train Image*

<img src="https://github.com/AbhinavSingh6295/Deep_Learning-Project/blob/main/6496.png" width="200" height="200" />

*Sample Mask Image*

- **U-Net Model Architecture**: U-Net is a Fully Convolution Network, while preserving the spatial information, replaces the dense layers in a typical CNN with a transposed convolution layer that upsamples the feature map back to the size of the original input image.
It also adds skip connection to retain information that would other lost during encoding. We added the Batch Normalization in every conv2d block, 
which help in achieving very good score with basic U-Net implementation.

- **Traing the U-Net**: For optimizers, we used Adam and SGD. We tried several learning rate. Used cross-entropy as loss function. Trained model for batch size and extended epochs.

<img src="https://github.com/AbhinavSingh6295/Deep_Learning-Project/blob/main/Training%20Loss%20Curve.PNG" alt="Sample Test Image" width="400" height="200" />

*Training Loss Curve*



- **Output on Test Images**: To get the predictions, we basically used the trained model in the last epoch to make the predictions for the test data. 
The predictions would contain the probability for each class for every pixel. Finally, we extract the class with highest probability and assign it to respective pixel, 
and then mask is saved as png file.

- **Evaluation**: The results were evaluated on the mean Dice coefficient. The dice coefficient can be used to compare the pixel-wise agreement between a predicted segmentation and its corresponding ground truth.

### Results
We achieved a dice score of .72 on public leader board and dice score of 0.74 in private leader board. We were ranked 9 among the 40 teams in class.

