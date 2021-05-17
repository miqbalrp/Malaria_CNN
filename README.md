# Malaria_CNN

My wife is a researcher at an institute of molecular biology research in Indonesia. One of her studies is related to malaria and she has been in Timika, Papua for about 5 months for patients who are indicated to have had malaria.</br> 

Therefore, since I first saw the Malaria Cell Image dataset in Kaggle (taken from: [LHNCBC](https://lhncbc.nlm.nih.gov/LHC-downloads/downloads.html#malaria-datasets)), I was interested and tried confirm whether she is familiar with this image or not. Without waiting long, my wife immediately lectured me about how a cell was said to be infected with Malaria and it turned out that there were several stages (ring, trophozoite, schizont, etc).</br> 

However, in this dataset, image cells are only divided into two classes: Malaria infected and healthy ones. Maybe for the next step we will try to classify not only infected or not, but also at what stage. For now we will look at this dataset, analyze and build a CNN model to classify image cells into these two classes: Malaria infected and healthy.</br>

## 1. Dataset
From the source, the data set consists of 27,558 images which are divided into two folders for each class. To ensure that the data used to evaluate the model is not mixed with training and validation data, I randomly take 100 images from each class as testing data.

<p align="center">
  <img width="400" height="400" src="https://user-images.githubusercontent.com/38918617/118417166-01410c80-b6dd-11eb-832a-8f4bfb8b75a9.png">
</p>

