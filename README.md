# IDX Bank Stock's Analysis and Forecasting - Fajar Zulkautsari Muhammad

## Project Domain
In recent years, Indonesia has had consistent economic development, which has provided critical support to the business sector and publicly traded enterprises. Trends in investment have also shifted[[1]](https://journal3.uin-alauddin.ac.id/index.php/Iqtisaduna/article/view/20214). The function of regulation in increasing stock market transparency and safety is also critical. Furthermore, the COVID-19 epidemic cannot be overlooked[[2]](https://journal.ipb.ac.id/index.php/jmo/article/view/32657), which brings significant volatility and liquidity[[3]](https://ejournal.unisnu.ac.id/JDEB/article/view/20) and pressuring markets to adjust to rapidly changing economic conditions. Finally, increased worldwide investor interest in Indonesian equities has produced new dynamics in the domestic stock market. A thorough awareness of all of these elements is essential for making sound and informed investing decisions.

Stock price forecasting is particularly significant in investment decision making in current digital age[[4]](https://ieeexplore.ieee.org/abstract/document/9350582). To find investment possibilities and manage risks, investors, stock traders, and financial institutions rely on rigorous analysis and precise forecasts. To construct a strong and trustworthy stock price forecasting model, this project will use artificial intelligence, especially Long Short-Term Memory (LSTM).

The goal of this research is to describe and assess the stock price forecasting process using historical data, market conditions, and pertinent trends. We will examine the function of banks in the economy and the significance of understanding the behavior of bank stock prices in the context of a banking backdrop. Then, having gained a thorough understanding of the business problem, we will develop project objectives and a framework to solve the problems of stock price forecasting.

## Business Understanding
### Problem Statements
The following issues are at the heart of this project: 
- How is the share price of the banking industry analyzed?
- What is the best investment strategy for banking stocks?

### Goals
The objectives of this project include:
- Implement Exploratory Data Analysis (EDA) to determine the performance of stocks in the banking sector.
- Perform stock price predictions that can be used as a reference in making investment strategy decisions.

### Solution Statements:
The problems and objectives described above can be solved with a Machine Learning approach for forecasting stock price movements. One of the models that can do this is the LSTM model _(Long-Short Term Memory)_ as a baseline model.

## Data Understanding
The dataset used is the stock price movement data of the TOP 5 Bank stocks included in the Indonesia Stock Exchange (IDX). The dataset is obtained from the [Yahoo! Finance](https://finance.yahoo.com/) site using the [Yahoo! Finance API](https://pypi.org/project/yfinance/). In the analysis, the data used is data in the last 3 years with a total of 729 data per bank issuer. With a total of 5 bank issuers being analyzed, the total data for analysis is 3645 data. As for _forecasting_, the data used is BBCA stock issuer data with the maximum total data that can be obtained from the Yahoo! Finance site, which is from June 08, 2004 to the present (September 10, 2023) with a total of 4773 data.

### Variabel-variabel pada dataset adalah sebagai berikut:
- **Open**      : Share price when the market opens in the morning
- **High**      : The highest share price point reached on the same day
- **Low**       : The lowest share price point reached on the same day
- **Close**     : Share price when the market closes in the afternoon
- **Adj Close** : Adjusted stock price at market close (e.g. stock split, etc.)
- **Volume**    : Total volume of stock transactions that occurred on the same day

To get detailed information on stock price comparisons in the banking industry, exploratory data analysis (EDA) and visualization were used. EDA and visualization were used to gather data on stock price fluctuations and daily transaction volume, as well as each bank's daily return and risk level.

![image](https://github.com/Loically/IDX_Bank_Stocks_Analysis_and_Forecasting/assets/114181235/007b9f10-0b16-4dde-92b2-cb124bd21284)

According to the stock price movement pattern shown above, BBCA, BBNI, and BBRI are in an uptrend. Actually, BMRI has an upward pattern as well, although there is a spike in 2023 that might be considered an abnormal price movement. BRIS, on the other hand, saw an upswing until 2021, followed by a downturn and sideways movement.

![image](https://github.com/Loically/IDX_Bank_Stocks_Analysis_and_Forecasting/assets/114181235/79984cfb-64b3-4911-b68d-0d6f463bbb29)

Furthermore, the connection between issuer prices is examined in order to identify issuers who have an impact on other bank issuers. According to the heatmap above, there is no extremely significant association between daily stock returns. However, four out of five banks have a very substantial link in terms of share price; only BRIS does not have a correlation with all banks.

One method for determining possible risk is to compare the average daily return to the standard deviation. The average daily return represents the expected value of profit produced, while the standard deviation represents the dispersion of profit that may be achieved. The higher the standard deviation, the larger the danger.

![image](https://github.com/Loically/IDX_Bank_Stocks_Analysis_and_Forecasting/assets/114181235/8958489b-6079-46db-a897-087f90ffb927)

BBCA has the lowest possible danger, which is roughly 1%. Following that are BBRI and BBNI, both of which have a relatively modest potential risk of roughly 1.7%. Then there's BRIS, which has a risk of 3.5%, and BMRI, which has a risk of 4.5%.
According to the findings of the investigation, **BBCA** is the bank issuer with the most consistent performance and the lowest potential risk.

## Data Preparation 
Data preparation is a critical stage in stock analysis and forecasting projects such as this one. In this stage, raw data is collected, loaded, cleaned, and converted into a form that can be used for analysis and modeling. Here is a further explanation of data preparation in this project:
- **Data Collection**: The first stage is to collect the data required for analysis. The data is sourced from the [Yahoo! Finance](https://finance.yahoo.com/) using the Yahoo! Finance API.
- Data Transformation**: Some data transformation techniques are performed to obtain information that is not provided by the dataset directly. For example, to get the value of _'Daily Return'_ which describes the percent profit/loss of the issuer in a day. The _'Daily Return'_ is obtained by finding the difference (in percentage form) of the _'close'_ price on this day with the _'close'_ price on the previous day. This value can be obtained by using a function from the Pandas _library_, namely [pct_change()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.pct_change.html)
- **Split Data**: Data is usually divided into two parts, namely training data and testing data. The training data is used to train the forecasting model, while the testing data is used to test the performance of the model. Since the data used is a time series that is highly dependent on the date sequence, this data is split by cutting with a proportion of 80% of the initial data as training data and 20% of the last data as training data.
- **Normalization and Standardization**: Since the data used may have different value ranges, normalization or standardization is required. The normalization used is [_MinMaxScaler()_](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MinMaxScaler.html). The _MinMaxScaler_ will convert the data interval into a range between 0 and 1. It aims to ensure that the data attributes have a wide range of scales. MinMaxScaler_ is used because it is suitable for normalizing price data that cannot have negative values. The stock price range that ranges from 729 - 9400 will be normalized to a range of 0 - 1.

$$
X_{\text{scaled}} = \frac{X - X_{\text{min}}}{X_{\text{max}} - X_{\text{min}}}
$$

- **_Windowing_ Data**: The main purpose of _windowing_ data is to divide time series data into smaller segments, allowing for more effective analysis and modeling. By dividing the data into time windows, the data will be separated into attributes and labels. The window size used in the data is 50 data (50 days) with a lag of 1 data (1 day).
- **Data Validation**: Data validation involves a final check to ensure that the data is ready for use. This includes ensuring there are no outstanding issues and that the data has the appropriate format such as data shape, etc.

## Modeling
The base machine learning model used in this project is LSTM (Long-Short Term Memory). LSTM is suitable for stock analysis and forecasting projects because it can handle stock price time series data with the ability to understand long-term patterns and trends, remember important information from the past, and process large data with flexibility. LSTM can also model complex patterns, stock price volatility, and can integrate with additional data such as financial news to enhance forecasting capabilities. 

The infrastructure of this model uses 2 LSTM layers, 2 hidden layers and an output layer with the following details: 

**1. First LSTM Layer (LSTM):**
Output Shape: (None, 50, 128)
Number of Parameters: 66,560
The first LSTM layer has 128 neuron units. It is a sequential layer that takes inputs in the form of data sequences of length 50 (corresponding to windowed_data) and produces sequential outputs. This output will be the input for the next LSTM layer.

**2. Second LSTM Layer (LSTM_1):**
Output Shape: (None, 64)
Number of Parameters: 49,408
The second LSTM layer has 64 neuron units. It is an LSTM layer that takes the sequential output of the previous layer and produces an output that is not sequential, but 64-dimensional.

**3. First Dense Layer (Dense):**
Output Shape: (None, 10)
Number of Parameters: 650
Activation Function: ReLU
This layer is the first hidden layer with 10 neuron units and ReLU activation function. This layer is responsible for combining and processing information from the previous LSTM layer.

**4. Second Dense Layer (Dense_1):**
Output Shape: (None, 5)
Number of Parameters: 55
Activation Function: ReLU
This layer is the second hidden layer with 5 neuron units and ReLU activation function. This layer helps the model in understanding more complex patterns in the data.

**5. Output Layer (Dense_2):**
Output Shape: (None, 1)
Number of Parameters: 6
This layer is an output layer with 1 neuron unit with no specific activation function. This layer generates stock price predictions.
The total parameters in this model are 116,679, and all these parameters can be adjusted during the training process. The model is designed to understand sequential patterns in stock price data and generate accurate predictions.

This model uses [**Adam**](https://keras.io/api/optimizers/adam/) optimizers and [**Huber**](https://www.tensorflow.org/api_docs/python/tf/keras/losses/Huber) loss functions. Adam's optimizer was chosen because it has the ability to adapt the learning rate. The learning rate is the speed at which the model learns during training. It determines how large a step is taken in the direction that reduces the value of the loss function. A larger learning rate will result in larger steps, while a smaller learning rate will result in smaller steps. Stock prices can experience significant fluctuations over time. Adam's optimizer with its ability to dynamically adapt the learning rate helps the model adapt to these fluctuations. It is also quite efficient in terms of convergence. This is a positive thing because the model needs to quickly adjust to changes in stock price data that can occur in a short period of time.

Meanwhile, Huber's loss function was chosen because stock price data is often susceptible to external events or news that can produce outliers. Huber's loss function, which is a combination of Mean Absolute Error (MAE) and Mean Squared Error (MSE), is more tolerant of outliers than MSE. This allows the model to be less affected by unusual events or anomalies in the stock price data. 

The training process of this model uses the GSD (Graduate Student Descent) method to manually search for the hyperparameters that get the best results. This resulted in a learning rate of 1e-3, 15 epochs, and a batch size of 5. Where one epoch is one training process using the entire dataset. A batch size of 5 means that the model will be updated every 5 times a data sample is given. 

![image](https://github.com/Loically/IDX_Bank_Stocks_Analysis_and_Forecasting/assets/114181235/4d384d4b-802b-4561-b449-56d85c35db39)

According to the training history graph, the MAE obtained tends to decrease, indicating that the model is improving. The results of training the model using the hyperparameter are rather satisfactory, with MAE 0.0043, or 0.43%, and a training loss of 1.7753e-05.

## Evaluation
The MAE measure is used in the assessment process, and the prediction results generated by the model are shown against the test data. The average absolute error between the model's forecast and the real value in the data is measured by MAE. MAE generates a non-negative error score; the lower the MAE number, the better the model predicts the target value. The MAE formula is presented below:

$$
MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|
$$

Where:
- $MAE$ is the Mean Absolute Error.
- $n$ is the number of samples.
- $y_i$ is the true value of the i-th sample.
- $hat{y}_i$ is the estimated value of the i-th sample.

![image](https://github.com/Loically/IDX_Bank_Stocks_Analysis_and_Forecasting/assets/114181235/640399e1-ebc1-4e70-8fcb-df40b26303f8)

The above graphic depicts the model forecast results. The predictions provided by the model (green line) are pretty close to the actual value (yellow line) in the test data. As a result, the model is claimed to be pretty good at forecasting stock values, with an MAE of 86.902 from a high of 9400 (0.9244%). 

With these findings, it is believed that the model would be able to assist investors in making better investment plan selections. For example, traders can engage in short/medium-term trading by purchasing when the model forecast is lower or the stock price is undergoing a correction and selling when it reaches its top (before the correction returns). Also for investors who know when to purchase.


