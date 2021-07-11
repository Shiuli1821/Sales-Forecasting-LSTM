# Future Sales Forecasting using LSTM
## Table of Contents
- [Overview](#Overview)
- [Problem Statement](#Problem-Statement)
- [Methodology](#Methodology)
- [Technology used](#Technology-Used)

## Overview
A company named ‘XYZ’ sells a variety of health products for people of all ages. Company management has decided to make key decisions on their logistics,
supply and production for which they want to check the sales figures for a certain set of years which will help them to invest their bucks and time in taking
decisions on key factors.

## Problem Statement
Given the historical data with respect to multiple regions of India and years (2005 to 2016) forecast sales for the years 2017 and 2018 using LSTM.

## Methodology
1) The train data imported using pandas.
2) The data contained the following columns [HQ, Country, State_of_outlet, City_of_outlet, Month, Day, Year, Total_Sales].
3) 'State of outlet' column was dropped since it only contained null values.
4) Feature column 'HQ' and 'Country' was dropped since it was filled with ony 1 value making them entirely redundant.
5) Remaining feature columns Year, Month and Day were concatenated to generate a single feature against which future sales will be predicted.
6) City of outlet feature contained 4 cities Bombay, Calcutta, Chennai and Delhi for each of which same date were provided.
7) Therefore separate forecasting was done for all the cities.
8) the sales vs date plot showed some outliers which were removed.
9) The data was split serially into train and validation set which were stored in separate dictionaries with city names as keys.
10) The train and test data were then scaled using minmaxscalar in the range (0,1).
11) Input feature table were generated using TimeseriesGenerator with length as 10. This means past 10 records will be used to predict next future record.
12) A tensorflow neural network model was created using keras.Sequential().An LSTM layer of 64 units were added followed by another LSTM of 32 units followed by a 
    single neuron dense layer for predicting single output. All the layers had activation as 'relu'.
13) The model was then run on train data using for 10 epochs using .fit_generator() with simultaneous validation of validation set.
14) This model was then used to predict on validation set. The outputs of the model were inverse transformed to get actual sales price.
15) The plot of overlapping predicted and actual values showed that the model can predict well which was further validated with low RSME values.  

## Technology Used
- Jupyter Notebook
- Python
