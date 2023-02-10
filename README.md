# Deep Learning Models for Financial Time Series Forecasting
In this work I will present the implementation of the models that I've used to do the experiments for my bachelor's thesis. They are three deep learning models, for the prediction of stock mid-price movements using limit order book data.
In particular I will propose these models:
- Long Short Term Memory (LSTM):  the architecture used has a single layer and a hidden size of 64. The reason for the simplicity of the architecture is that with a greater amount of layers and a greater hidden size the model tends to go in overfitting.
- Deep Convolutional Neural Network (DCNN): the structure is made up of 15 convolutional layer and 3 fully connected layer, I did not find necessary pooling layers since the input dimensions were not particularly large and would have lowered the performance. The activation function used is LeakyReLU.
- DCNN-LSTM LOB: with this model I've wanted to try a modification of DeepLOB. The Architecture of the DCNN is composed of 9 convolutional layers same as those of DeepLOB, subsequently there is an inception module composed of 5 parts, each part is made up of 2 convolutional layers, which however are not applied sequentially but each receives in input, the output of the last of the 9 convolutional layers and subsequently all the outputs of each part of the inception module are concatenated and passed in input to the LSTM layer, which has a hidden size of 64. The activation function used is LeakyReLU. 

All the hyperparameters were optimized with random search.

In every notebooks is proposed all the machine learning pipeline, starting from the loading of the dataset, passing from the labeling method, creation of the datasets and dataloaders, ending with the train, validation and test. For specifics refer to the folders.

I have uploaded the normalized [LOBSTER dataset](https://lobsterdata.com/info/DataSamples.php) (in particular I have used the LOB file with 10 levels) in the folder dataset.

# Usage

To run the code you just have to unzip the dataset and change the data path, then the notebook will do the rest, including the training and testing.

# Results
![alt text](https://github.com//image.jpg?raw=true)

# Experiment Setup
The LOBSTER dataset, contains the LOB of a trading day (2012/06/21) of the following stocks: Apple, Microsoft, Intel, Amazon and Google, all very liquid stocks; the total samples are 2,110,860. 
The labeling method is the one proposed by Tsantekidis et al. in "Forecasting Stock Prices from the Limit Order
Book using Convolutional Neural Networks". 
The method exploits the percentage change $l_t$ of the average of the $k$ (horizon) mid-prices preceding and succeeding
$t$ to decide the direction, once a threshold $\alpha$ is decided, if $l_t > \alpha$ then it will be considered as an up trend with label $0$, if $l_t < -\alpha$ then it will be considered as a down trend with label $1$, while if $l_t$ is included in the interval $[-\alpha, \alpha]$ it will be considered as stationary and therefore without trend, with label 2.


