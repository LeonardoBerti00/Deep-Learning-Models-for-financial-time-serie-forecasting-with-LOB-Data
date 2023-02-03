# Deep Learning Models for Financial Time Series Forecasting
In this work I will present the implementation of the models of my bachelor's thesis, that I've used during the experiments. They are three deep learning models, for the prediction of mid-price movements using limit order book data.
In particular I will propose these models:
- Long Short Term Memory (LSTM) 
- Deep Convolutional Neural Network (DCNN)
- DCNN-LSTM LOB 

In every notebook is proposed all the machine learning pipeline, starting from the loading of the dataset, passing from the labeling method, creation of the datasets and dataloaders, ending with the train, validation and test. For specifics refer to the folders.

I have uploaded the normalized [LOBSTER dataset](https://lobsterdata.com/info/DataSamples.php) (in particular I have used the LOB file with 10 levels) in the folder dataset.

# Usage

To run the code you just have to unzip the dataset and change the data path, then the notebook will do the rest, including the training and testing.

# Experiment Setup
The LOBSTER dataset, which you can find on \textit{lobsterdata.com}, contains the LOB of a trading day (2012/06/21) of the following stocks: Apple, Microsoft, Intel, Amazon and Google, all very liquid stocks; the total samples are 2,110,860. 
The labeling method is the one proposed by Tsantekidis et al. in "Forecasting Stock Prices from the Limit Order
Book using Convolutional Neural Networks". 
The method exploits the percentage change ($l_t$) of the average of the $k$ (horizon) mid-prices preceding and succeeding
$t$ to decide the direction, once a threshold $\alpha$ is decided, if $l_t > \alpha$ then it will be considered as an up trend with label $0$, if $l_t < -\alpha$ then it will be considered as a down trend with label $1$, while if $-\alpha \le l_t \le \alpha $ it will be considered as stationary and therefore without trend, with label 2.
