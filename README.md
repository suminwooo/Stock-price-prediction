stock price prediction  
  
This project is to predict stock price using deep-learning.  
I used LSTM, GRU with korea stock, index.  
data from yahoo finance.  


00. Technical analysis code(bollinger band, ma, macd, rsi, stochastic)     
  
  
  --------
  
  Using kospi 200 data  
  
1. Kospi 200 close price prediction using OHLC (LSTM)  
-> using 5day data and prediction 10 days later  
-> RMSE : 0.02553430596902424  
-> 문제점 : 기존의 추세를 따라감.   

2. Kospi 200 close price prediction using OHLC (GRU)  
-> using 5day data and prediction 10 days later  
-> RMSE : 0.019429207238005057  
-> 문제점 : 기존의 추세를 따라감.   
  
  
  ---------
   
  Using Samsung stock price data   
  
  
3. samsung stock price prediction LSTM  
-> using Bollinger band, moving average, macd, rsi, stochastic, roc, ohlc(22var)  
-> using 5day data and prediction 10 days later  
-> RMSE : 0.19156382527348761  
-> 문제점 : PCA 검사 결과 차원의 저주 문제 발생.   
  
4. samsung stock price prediction using PCA, LSTM  
-> using no.3 var  
-> PCA를 활용하여 4개의 변수를 활용하여 LSTM을 돌려봄  
-> RMSE : 0.13721298327731987  
-> 문제점 : 테스트 결과 RMSE가 약간 하락하였지만 큰 의미가 없음.  

5. samsung stock price prediction(10 var) using LSTM  
-> 3번 모델에서 사용한 변수의 상관계수를 확인한후 var을 축소함. 
-> PCA를 활용하여 4개의 변수를 활용하여 LSTM을 돌려봄  
-> RMSE : 0.12660472013769297  
-> 문제점 : 3번의 모델보다는 향상되었으나 아직 RMSE가 큼.  

6. samsung stock price prediction(10 var) using PCA, LSTM  
-> using no.5 var  
-> PCA를 활용하여 4개의 변수를 활용하여 LSTM을 돌려봄  
-> RMSE : 0.13191855162665575  
-> 문제점 : 3번,4번을 비교하면 PCA한 모델이 RMSE가 더 작게 나오지만 지금의 상황에서는 PCA하지 않았을때가 작게 나타남.   
