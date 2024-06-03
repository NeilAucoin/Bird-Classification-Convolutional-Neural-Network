# Project Description
Build a convolutional neural network that can identify bird species using only images.  

## Data Source
[Kaggle](https://www.kaggle.com/gpiosenka/100-bird-species)

Data set of 525 bird species. 84,635 training images, 2625 test images (5 images per species) and 2625 validation images (5 images per species).  

For this project, only 15 bird species of the 525 were used in order to reduce trianing times and to serve as a simpler introduction into neural networks.

# Process
## Data Selection
I started by isolating the 15 bird species I would be using for this model. I decided to selected the 15 bird species with the most images as this would allow my model to have more data to train off of and potentially improve my results.
![Isolate Species](https://github.com/NeilAucoin/Bird-Classification-Convolutional-Neural-Network/blob/main/Assets/isolate_15.PNG?raw=true)

## Data Augmentation
I then decided to augment my data by shuffling it, randomizing it, and normalizing it. Resizing images also helped reduce training time without losing much (if any) accuracy.  
![Shuffle, Randomize, Normalize](https://github.com/NeilAucoin/Bird-Classification-Convolutional-Neural-Network/blob/main/Assets/shuffle_randomize_normalize.PNG?raw=true)

## Model
I started off with a simple 3-layer model to experiment with and test the rest of my code. I then slowly added more and more layers and experimented with different model infrastructures until training returned promising results (above 75% accuracy). My final model used an increasing number of neurons in order to break down identifying features into multiple steps with increasing complexity. I used a softmax activation on my output layer to convert raw output scores into probabilities by class, used Conv2D layers to extract the most important features, MaxPooling2D layers to reduce spatial dimensions, Flatten layers to allow the dense layers to receive 1D input, Dropout layers to prevent overfitting, BathNormalization layers to stabilize the training process, and a GlobalAveragePooling layer for dimensionality reduction.  
![Final Model](https://github.com/NeilAucoin/Bird-Classification-Convolutional-Neural-Network/blob/main/Assets/final_model.PNG?raw=true)

## Compiler
For my compiler, I use Adam Optimizer for simplicity as it performed well with default hyperparameters. I started off using categorical crossentropy as a loss function due to its good results with many one-hot encoded classes (which I was using through keras), but later switched to sparse categorical cross entropy as it was known to perform better when using a large number of integer labels (which did improve results). For metrics, I used accuracy as it is a simple and effective way to reflect correctly classified instances.  
![Compiler](https://github.com/NeilAucoin/Bird-Classification-Convolutional-Neural-Network/blob/main/Assets/compiler.PNG?raw=true)

## Training Results
I was pleased with my training results (accuracy around 79%) and decided to go with this model as it was more than sufficient for the scope if this project.  
![Training Result](https://github.com/NeilAucoin/Bird-Classification-Convolutional-Neural-Network/blob/main/Assets/training_result.PNG?raw=true)

## Plots
I then plotted my training and validation loss and accuracy to get a visual interpretation of my model's results.  
![Training and Validation Loss](https://github.com/NeilAucoin/Bird-Classification-Convolutional-Neural-Network/blob/main/Assets/Training_and_Validation_Loss.PNG?raw=true)  
![Training and Validation Accuracy](https://github.com/NeilAucoin/Bird-Classification-Convolutional-Neural-Network/blob/main/Assets/Training_and_Validation_Accuracy.PNG?raw=true)

## Test Results
My final test accuracy was 80%, which is slightly better than I was expecting to get from my first CNN. Potential areas for improvement for future models would be further data augmentation, experimenting with different layers and layer layouts, and different compilers and activation methods.  
![Final Results](https://github.com/NeilAucoin/Bird-Classification-Convolutional-Neural-Network/blob/main/Assets/final_results.PNG?raw=true)
