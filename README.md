stock price prediction

This project is to predict stock price using deep-learning.
I used LSTM, GRU with korea stock, index.
data from yahoo finance.


00. Technical analysis code(bollinger band, ma, macd, rsi, stochastic)
1. Kospi 200 close price prediction using OHLC (LSTM)
-> using 5day data and prediction 10 days later
-> 문제점 : 기존의 추세를 따라감. 

2. Kospi 200 close price prediction using OHLC (GRU)
-> using 5day data and prediction 10 days later
-> 문제점 : 기존의 추세를 따라감. 

3. samsung stock price prediction LSTM
-> using Bollinger band, moving average, macd, rsi, stochastic, roc, ohlc
-> using 5day data and prediction 10 days later
-> 문제점 : PCA 검사 결과 차원의 저주 문제 발생. 

4. samsung stock price prediction using PCA, LSTM
-> using no.3 
-> PCA를 활용하여 4개의 변수를 활용하여 LSTM을 돌려봄
-> 문제점 : 테스트 결과 RMSE가 약간 하락하였지만 큰 의미가 없음.
