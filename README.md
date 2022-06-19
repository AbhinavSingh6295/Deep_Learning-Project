# Deep Learning

## Multi-image Segmentation using U-Net Architecture in Pytorch Framework

### Goal and Objective 
The goal was to implement and solve the remote sensing problem using the deep learning technique to segment images acquired by a small UAV in the area of Houston, Texas. In total there are 25 categories (ex - roofs, trees, pools, etc.) and the task was to design and implement a deep learning model to perform the automatic segmentation of such images. The model was trained using train images that contained pixel-wise annotations. Using the trained model, a prediction on the test images was performed.

### Methodology - 
- **Dataset Preparation**: Data was available on Kaggle. As a pre-processing step, images were resized to (128 x 128) and (256 x 256) sets. 
For normalization of pixel values between 0-1 range, divided each pixel values by 255. On the augmentation side, tried several image transformations: flipping images vertically and horizontally, shifting, zooming, and rotating by 45 degrees. 
Finally created training and validation data.

<img src="https://github.com/AbhinavSingh6295/Deep_Learning-Project/blob/main/6496.jpg" alt="Sample Test Image" width="200" height="200" />

*Sample Train Image*

<img src="https://github.com/AbhinavSingh6295/Deep_Learning-Project/blob/main/6496.png" width="200" height="200" />

*Sample Mask Image*

- **U-Net Model Architecture**: U-Net is a Fully Convolution Network. It preserves the spatial information and replaces the dense layers in a typical CNN with a transposed convolution layer that upsamples the feature map back to the size of the original input image. It also adds skip-connection to retain information that would otherwise get lost during encoding. Added batch normalization in every conv2d block, which helped in achieving a very good accuracy with basic U-Net implementation.

- **Training the U-Net**: For optimizers, tried Adam and SGD, also tried multiple learning rates. Used cross-entropy as a loss function. Trained the model for different batch sizes and extended epochs.

<img src="https://github.com/AbhinavSingh6295/Deep_Learning-Project/blob/main/Training%20Loss%20Curve.PNG" alt="Sample Test Image" width="400" height="200" />

*Training Loss Curve*

- **Output on Test Images**: To get the predictions, used the best model with the lowest loss (in this case, it was the last epoch) to make the predictions on the test images. 
The predictions would contain the probability for each class for every pixel. Finally, extract the class with the highest probability and assign it to the respective pixel, and then the mask image is saved as a png file.

- **Evaluation**: The results were evaluated on the mean Dice coefficient. The dice coefficient can be used to compare the pixel-wise agreement between a predicted segmentation and its corresponding ground truth.

### Results
Achieved a dice score of .72 on the public leader board and a dice score of 0.74 on the private leader board.

