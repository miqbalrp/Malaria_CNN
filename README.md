# Malaria_CNN

My wife is a researcher at an research institute of molecular biology in Indonesia. One of her studies is related to malaria and she has been in Timika, Papua for about 5 months for patients who are indicated to have had malaria.</br> 

Therefore, since I first saw the Malaria Cell Image dataset in Kaggle (taken from: [LHNCBC](https://lhncbc.nlm.nih.gov/LHC-downloads/downloads.html#malaria-datasets)), I was interested and tried confirm whether she is familiar with this image or not. Without waiting long, my wife immediately lectured me about how a cell was said to be infected with Malaria and it turned out that there were several stages (ring, trophozoite, schizont, etc).</br> 

However, in this dataset, image cells are only divided into two classes: Malaria infected and healthy ones. Maybe for the next step we will try to classify not only infected or not, but also at what stage. For now we will look at this dataset, analyze and build a CNN model to classify image cells into these two classes: Malaria infected and healthy.</br>

## 1. Data and Visualization ([notebook](https://github.com/miqbalrp/Malaria_CNN/blob/main/notebook/1.%20Image%20Read%20and%20Visualization.ipynb))
From the source, the data set consists of 27,558 images which are divided into two folders for each class. To ensure that the data used to evaluate the model is not mixed with training and validation data, I randomly take 100 images from each class as testing data.

<p align="center">
  <img width="400" height="400" src="https://user-images.githubusercontent.com/38918617/118417166-01410c80-b6dd-11eb-832a-8f4bfb8b75a9.png">
</p>

For training, I use 50% of randomly selected data then check whether the data is still in balance or not. Based on the chart we can see that the data is still in balance. 
<p align="center">
  <img width="400" src="https://user-images.githubusercontent.com/38918617/118417800-f176f780-b6df-11eb-97c1-419b00dc7bb6.png">
</p>

From the sample data shown above we can see at a glance that the images have different dimensions. To make sure I plot the dimensions of all the images used and look at their distribution.

<p align="center">
  <img width="400" src="https://user-images.githubusercontent.com/38918617/118417938-9560a300-b6e0-11eb-9689-2d2f9eedad80.png">
</p>

As expected, the data varied in dimensions and were distributed with the mean around (130.130). This figure will be used to standardize dimensions before the data is used for model training.

## 2. Model Building ([notebook](https://github.com/miqbalrp/Malaria_CNN/blob/main/notebook/2.%20Image%20Augmentation%20and%20Modelling.ipynb))
The model used is inspired by the LeNet-5 architecture developed in 1998 to classify handwritten images from the MNIST dataset. This model is a very basic convolutional neural network architecture consisting of 7 layers, namely 3 convolutional layers, 2 subsampling layers and 2 fully connected layers (for more detailed: [Understanding and Implementing LeNet-5 CNN Architecture (Deep Learning)](https://towardsdatascience.com/understanding-and-implementing-lenet-5-cnn-architecture-deep-learning-a2d531ebc342)).</br>

Some adjustments were made to this model because the LeNet-5 was originally used to detect 28x28 grayscale handwritten images and had 10 classes (numbers 0-9). In general, the model used can be seen in the following summary.

![image](https://user-images.githubusercontent.com/38918617/118418338-461b7200-b6e2-11eb-8d06-00fb546046c6.png)

Model training and validation consists of 10 epochs where the data is generated using the `ImageDataGenerator` function to generate simple augmentation (horizontal and vertical flip) and resize images. Graphs of changes in accuracy and loss in each epoch can be seen in the following figure.

<p align="center">
  <img width="600" src="https://user-images.githubusercontent.com/38918617/118418622-4c5e1e00-b6e3-11eb-9e8a-95101dd79291.png">
</p>

## 3. Model Evaluation ([notebook](https://github.com/miqbalrp/Malaria_CNN/blob/main/notebook/3.%20Evaluation.ipynb))
Using 200 test data, I did a model evaluation and got an excellent accuracy of 99%. In the confusion matrix we can see that there is only 1 misclassified image.
<p align="center">
  <img width="500" src="https://user-images.githubusercontent.com/38918617/118419381-022a6c00-b6e6-11eb-8736-3f70af598ad6.png">
</p>

<p align="center">
  <img width="300" src="https://user-images.githubusercontent.com/38918617/118418882-7106c580-b6e4-11eb-846a-aa0ba6e02195.png">
</p>

## 4. Conclusion
