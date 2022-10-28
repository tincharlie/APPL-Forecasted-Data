# APPL-Forecasted-Data
*In this data we are taking the data of apple stock and doing the Forcasted analysis on it.*
<div id="header" align="center">
  <img src="https://github.com/tincharlie/APPL-Forecasted-Data/blob/main/ImpFile/giphy.gif" width="30%"/>
</div>
Here we will take past data like and get the output. This output will consider as a input and predict another forecasted value.

For Example:
200, 250, 300 -- 250
250, 300, 250 -- 267
300, 250, 267 -- 272


This is how it works and after completion of that process we will get that approximate forecasted stock price on the daywise.

Lets Assume a use case:
We have 3 burger points in the city.
If we want to predict the sales of each one of the point. So in the A Burger Point need 220 burger, B point need 200 Burger, and c point need 300 burger. So on an average for tomorrow how Burger much they will need in all the Burger Point that we can forecaste on the basis of previous data.

Similarly We will take the day wise data and will do sum and average of it then we will get the forecaste.

**Steps We Generally follow.**
  **1. Data Reading Part :**
    In this step we will read the data by using the pandas library. 
  
  **2. Making Plots :**
    This shows the data is in which pattern multiplicative or additive.
    
  **3. Taking moving Avg :**
    Here it will take the past data and predict the average. Then again this will do the same till your forecasted date.
   
  **4. Scaling Down Values :**
    We will scale down the price so it will give you the near to accurate forecaste.
    
  **5. Create Train array :**
    In this process you will see we took empty list of xtrain or ytrain. Because we have to take the average. So that we are running a for loop taking the respected       average for our forecaste.
  **6. Neural Network LSTM :**
    Here we are using the LSTM Long Short Term Memmory which the part of RNN Recurrent Neural Network. Through this we are making the model.
    
  **7. Model Building :**
    There we are taking some sort of layers and get the accurate forecaste.
    
  **8. Model Summary :**
    It will show the all detail of your units and layers. This data is summary of your model in first to last layer how much values and units will pass. All this detals we can see in it.
  **9. Model Compilation :**
    This is the time to compile and pass the training data to train and get the best forecaste of the stock. By passing the different epochs.
    
  **10. Create Test array :**
    There we are creating testing array. So that we are able to see the accurate forecaste.
    
  **11. Prediction and Actual Plots :**
    Now in the end we will see the prediction and actual plot. To compare the accuracy of forecasted plot.
