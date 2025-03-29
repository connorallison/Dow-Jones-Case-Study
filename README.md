Connor Allison
Joel Fry
Nicholas Mata
Royalpriesthood Olola
DA-6813
Dow Jones Case Study
Executive Summary
This study explores the use of machine learning models to predict stock price changes for the Dow Jones Index. By applying Linear Regression (LM), Support Vector Regression (SVR), and Decision Tree (DT) models, we aim to forecast percent_change_next_weeks_price based on previous_weeks_volume. The models are compared based on their Mean Squared Error (MSE), with an additional risk analysis performed using the Capital Asset Pricing Model (CAPM). Our analysis finds that the SVR with radial kernel performs best in terms of prediction accuracy, while Linear Regression provides insights into the most significant factors affecting price movements.

Problem
The challenge is to predict stock price percentage changes for the next week based on weekly performance data. Identifying the best model to forecast price movements with accuracy is crucial for making informed financial decisions. The study compares three machine learning techniques (LM, SVR, and DT) to determine which model provides the most reliable predictions of stock price changes based on historical data, particularly previous_weeks_volume. This report will first review related work, followed by a description of the methodology, a discussion of results, and a conclusion on how the findings can be applied practically.

Literature Review
Stock price prediction has been a subject of interest in financial modeling, with various machine learning methods being applied to predict future price movements (Krollner et al., 2013). Linear regression has been commonly used for predicting price changes, though its performance in stock market prediction can be limited by non-linear relationships (Kou et al., 2015). Support Vector Regression, particularly with non-linear kernels, has been found to improve prediction accuracy in complex datasets (Wang et al., 2014). Decision Trees, on the other hand, capture non-linear patterns and interactions that may not be easily modeled by traditional methods. The combination of these methods provides a comprehensive approach to understanding stock price dynamics (Bansal, Malti, et al 2022).

Methodology
We plan to use three different machine learning models to predict percent_change_next_weeks_price based on previous_weeks_volume. These models will be trained on historical stock data, and their performance will be evaluated using Mean Squared Error (MSE). Additionally, CAPM will be used to assess stock risk and volatility. Linear Regression (LR), Support Vector Regression (SVR), and Decision Trees (DT) are the models that will be used, each with distinct assumptions. 

Linear Regression assumes a linear relationship between the independent variables (e.g., previous week's volume) and the target (e.g., stock price change). It also assumes independence of errors and homoscedasticity (constant variance of residuals), as well as a normal distribution of errors for inference. While easy to interpret, LR may not perform well with highly volatile financial data due to its inability to capture non-linear relationships (Abraham and Ledolter 1983). This model will explore the linear relationship between previous_weeks_volume and percent_change_next_weeks_price. Lag variables as well as a stepwise selection using all variables for the model will be explored to see if any improvements are made.

SVR uses different kernels to model non-linear relationships by mapping data to a higher-dimensional space. Assumptions include linearity in transformed space, error tolerance, allowing the model to ignore small errors, and sparsity of support vectors to define the decision boundary. SVR is effective in capturing complex patterns in stock price data, but choosing the right kernel and parameters can be computationally intensive and sensitive to noise (Smola and Scholkopf 2004). Using a radial kernel, this model will capture non-linear relationships in hopes to improve prediction accuracy.

Decision Trees split data based on feature values, capturing non-linear relationships. Key assumptions are feature independence within each split, no need for feature scaling, risk of overfitting. DTs excel at handling complex interactions but can overfit without pruning or regularization, which is a concern in stock market prediction (Breiman, Leo, et al 2017).

We will compare the models based on their MSE, selecting the model that minimizes this error as the most effective for stock price prediction. To ensure our comparisons are accurate, we will train our models on 1st quarter data and evaluate them on 2nd quarter data for all 30 stocks in the dataset. Once we have the MSE’s from all models for each stock, the average MSE for each model over the 30 stocks will be used to conclude the most effective model. We will use the most effective model to compute beta values and along with the CAPM, we will assess the risks of the stocks.

Data
The dataset consists of stock data from the Dow Jones Index, with each record representing weekly stock performance. The target variable is percent_change_next_weeks_price, and key attributes include:

Market data: quarter, stock, and date

Price data: open, high, low, close, next_weeks_open and next_weeks_close.

Volume metrics: volume and previous_weeks_volume.

Percentage change metrics: percent_change_volume_over_last_wk, percent_change_price and percent_change_next_weeks_price.

Dividend information: days_to_next_dividend and percent_return_next_dividend.

The dataset was cleaned and transformed to ensure consistency: Price values were converted from string format with currency symbols to numeric values. Percentage changes in price were transformed into numerical types. The quarter and stock columns were encoded as factors for analysis. The date column was parsed into a standard date format. The amount of data between Q1 and Q2 was close to evenly split with 12 observations per stock in Q1 and 13 for Q2. Correlation between numeric variables used in the model were also found to not be highly correlated with each other.


Results
A linear regression model, SVR, and decision tree were trained for each stock to model how previous_weeks_volume influences percent_change_next_weeks_price. The models were evaluated based on Mean Squared Error (MSE), with the lowest average MSE indicating the best model.

Based on the MSEs, the SVR outperformed the other models, offering the most accurate predictions for stock price changes. Linear Regression provided valuable insights into the most significant factors affecting price changes, while Decision Tree Regression was useful for capturing non-linear interactions, though it didn’t perform as well in terms of prediction accuracy.

Stepwise regression was applied to the linear model to identify the most significant predictors of stock price changes, but the result was a drastic increase in average MSE, indicating that our initial predictor of previous_weeks_volume was better.

Lag variables were also introduced to account for temporal dependencies in stock price changes. We explored the effects of lag periods 1 week through 4 for all 30 stocks, but there was no significant influence of any of the lags on percent_change_next_weeks_price.

To assess the risk of individual stocks, we computed beta coefficients using the Capital Asset Pricing Model (CAPM). This involved computing weekly returns for each stock, computing weekly market returns using the Dow Jones Industrial Average (DJI), and performing SVR of stock returns against market returns to estimate beta. The beta values provided insights into relative volatility compared to the overall market. Stocks with higher beta values tend to exhibit more volatility, while those with lower beta values are more stable. According to the beta values resulting from using SVR, all 30 stocks are less than 1 and stable in relation to the market.

This indicated that the weekly returns for stable stocks exhibit low volatility, and their price fluctuations would only be a fraction from what historical data showed. In other words, their weekly returns would most likely behave the same way in the future. If a stock lost money the past week, it will lose money the following week. Below is the average return and standard deviation for each stock. 

Beta values derived from our linear model were also explored. They were found to contain more variation from the beta values from SVR, indicating both sides of volatility in relation to the market.


Conclusion
This study demonstrates that machine learning techniques can predict stock price changes in the Dow Jones Index. The SVR was the best-performing model, while Linear Regression provided valuable insights into the predictors of stock price changes. CAPM was useful for assessing stock risk. For future improvements, incorporating deep learning methods and macroeconomic indicators could enhance prediction accuracy. Additionally, exploring alternative time-series forecasting models may provide further insights into stock price dynamics.



Works Cited

Abraham, Bovas, and Johannes Ledolter. Statistical methods for forecasting. John Wiley & Sons, 2009.

Bansal, Malti, et al. “Stock Market Prediction with High Accuracy Using Machine Learning Techniques.” Procedia Computer Science, vol. 215, Elsevier, Amsterdam, 2022, pp. 247–265.

Breiman, Leo, et al. Classification and regression trees. Routledge, 2017.

Smola, Alex J, and Bernhard Scholkopf. Kluwer Academic Publishers, 2004, pp. 1–24, A Tutorial on Support Vector Regression.















