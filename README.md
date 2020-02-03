stock price prediction  
  
This project is to predict stock price using deep-learning.  
I used LSTM, GRU with korea stock, index.  
data from yahoo finance.  


00. Technical analysis code(bollinger band, ma, macd, rsi, stochastic)     
  
  
  --------
  
  < Using kospi 200 data >  

  --------
  
1. Kospi 200 close price prediction using OHLC (LSTM)  
-> using 5day data and prediction 10 days later  
-> RMSE : 0.02553430596902424  
-> 문제점 : 기존의 추세를 따라감.   

2. Kospi 200 close price prediction using OHLC (GRU)  
-> using 5day data and prediction 10 days later  
-> RMSE : 0.019429207238005057  
-> 문제점 : 기존의 추세를 따라감.   
  
  
  ---------
   
  < Using Samsung stock price data >  
  
  ----------
  
**LSTM**

  
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

6. samsung stock price prediction(9 var) using PCA, LSTM   
-> using no.5 var+Close price-2var  
-> PCA를 활용하여 2-4개의 변수를 활용하여 LSTM을 돌려봄  
-> RMSE : 0.1691978670334448  
-> 문제점 : 3번,4번을 비교하면 PCA한 모델이 RMSE가 더 작게 나오지만 지금의 상황에서는 PCA하지 않았을때가 작게 나타남.   
-> 향후 계획 : close 추가

  ------------------------

7. samsung stock price prediction(9 var) using LSTM  
-> using no.5 var+Close price-2var  
-> PCA를 활용하여 4개의 변수를 활용하여 LSTM을 돌려봄  
-> RMSE : 0.13191855162665575  
-> 문제점 : 변수의 수를 줄이고 PCA를 활용해 주성분을 2-4개 조절해보았지만 큰 변화는 보이지 않음.

8. samsung stock price prediction(9 var) using LSTM  
-> using no.5 var+Close price-2var   
-> 변수의 수를 9개로 줄여서 그대로 돌려봄    
-> RMSE : 0.21823781565146547  
-> 문제점 : Close를 추가하여 다른 변수를 제외하고 하니 종가가 너무 많이 차이 나므로 ma나 다른 지표가 필요함.   
-> 향후 계획 : close로 파생된 변수 추가 해보기
-> 모델을 LSTM뿐만이 아닌 GRU도 추가하고 epoch, batch size를 설정하면서 튜닝이 필요할것 같음.

  ---------------------
  
  **LSTM 사용 결과 RMSE 비교**

  1. 변수만 활용 (모두 1층으로 구성)

| 22var | 10var | 9var | 
| ---------- | :---------: | :----------: |
| 0.191563825 | 0.170772379 | 0.152846769 |

  2. PCA 활용

| 22var(4PCA) | 10var(4PCA) | 9var(4PCA) | 9var(2PCA) |  
| ---------- | :---------:| :----------: | ----------: | 
| 0.153323195 | 0.120311047 | 0.138247439 | 0.135970351 |

-> 이를 통해 PCA가 더 낮은 RMSE를 보이는 것을 알수 있다.  
-> 아직 RMSE가 크므로 줄이는 방향으로 나아가야한다.  

  -----------------------

**facebook prophet**


