# Financial Transaction Balance Prediction using Time Series

## **Overview**

This project focuses on predicting the balance of financial accounts based on historical transaction data using **Time Series Forecasting** and machine learning models. The dataset contains transaction details for multiple accounts, and the model aims to forecast future account balances using past data and time-based features.

The project is part of the **Pesta Data Nasional (PEDAS) 2024** competition, specifically in the **Data Scientist** category. It provides insights into time series forecasting by applying **machine learning algorithms** on transaction data.

## **Dataset**

The dataset used for this project contains the following attributes:
1. **trx_code**: A unique transaction code that identifies each transaction.
2. **trx_id**: The unique transaction number.
3. **rek_code**: A unique code representing the account.
4. **rek**: The account number (unique identifier for each financial account).
5. **creationdate**: The timestamp when the transaction was created.
6. **type**: The type of transaction (e.g., Deposit, Withdrawal).
7. **amount**: The transaction amount (deposit or withdrawal).
8. **balance**: The account balance after the transaction.

The project uses the **Train Data** for model training, **Test Data** for evaluating model performance, and **Inference Data** for making predictions on missing balance values.

## **Preprocessing**

The data is preprocessed by:
1. **Feature Extraction**: Extracting time-based features such as hour, day of the week, month, and year from the transaction dates.
2. **Lag Features**: Creating lag features like `lag1`, `lag2`, and `lag3`, which represent the account balance from the previous time steps (1, 2, and 3).
3. **Handling Missing Values**: Interpolating missing balance data using **time-based interpolation**, which estimates missing values based on existing time-stamped data. This interpolation method ensures that the balance data remains continuous and smooth over time without introducing abrupt changes.
4. **Resampling**: The data is resampled to an hourly frequency to ensure consistent time intervals, with duplicate timestamps removed.

### **Interpolation Method**:
To handle missing values in the balance data, **time-based interpolation** is used. This method estimates missing values based on the time index. The values are interpolated linearly between two existing data points, ensuring the balance follows a consistent pattern without sudden jumps. This method is suitable for time series data as it preserves the temporal relationship between observations.

## **Model Training and Evaluation**

The model is trained using time series data, where features like **hour**, **day of week**, **month**, and **lag features** are used to predict the **account balance**. Various machine learning models like **Random Forest Regressor** and **Linear Regression** are used to train the data. 

### **Metrics for Evaluation**:
- **SMAPE (Symmetric Mean Absolute Percentage Error)**: Measures prediction accuracy.
- **MAE (Mean Absolute Error)**: Evaluates the average prediction error.
- **RMSE (Root Mean Squared Error)**: Measures the square root of the average squared differences between actual and predicted values.

## **Model Inference**

Once the model is trained, it can be used to predict the missing balances in the **inference data**. The predicted balances are inserted into the dataset, replacing the missing (`NaN`) values.

### **Key Features**:
1. **Time Series Forecasting**: Predicting future balances based on historical transaction data.
2. **Lag Features**: Using previous balance data to improve predictions.
3. **Model Evaluation**: Using SMAPE, MAE, and RMSE to evaluate the accuracy and performance of the model.

## **Results**

The project successfully predicts account balances using the historical transaction data. The accuracy of the predictions is evaluated using various metrics (SMAPE, MAE, RMSE), and the results are used to assess the model’s performance.

## **Future Work**

- **Model Improvement**: Further fine-tuning and exploring advanced models like **LSTM** or **ARIMA** for better time series predictions.
- **Real-Time Prediction**: Implementing real-time forecasting for ongoing transaction data.
- **Handling Outliers**: Improving the handling of outliers in the transaction data to improve model robustness.

## **Contributors**

- **Steve Marcello Liem**
- **Matthew Lefrandt**
- **Marvel Martawidjaja**

## **License**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
