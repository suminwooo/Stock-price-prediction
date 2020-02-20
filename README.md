stock price prediction  
  
This project is to predict stock price using deep-learning.  
I used LSTM, GRU with korea stock, index.  
data from yahoo finance.  


+00. Technical analysis code(bollinger band, ma, macd, rsi, stochastic)    
-> 기술적 지표를 위해 파이썬으로 코드 구현  

--------
  
  < Using kospi 200 data >  

  --------
  
01. Kospi 200 close price prediction using OHLC (LSTM) ->[코드]()    
-> using 5day data and prediction 10 days later  
-> RMSE : 0.02553430596902424  
-> 문제점 : 기존의 추세를 따라감.   

02. Kospi 200 close price prediction using OHLC (GRU)->[코드]()     
-> using 5day data and prediction 10 days later  
-> RMSE : 0.019429207238005057  
-> 문제점 : 기존의 추세를 따라감.   
  
  
  ---------
   
  < Using Samsung stock price data >  
  
  ----------
  
**LSTM**

  
03. samsung stock price prediction LSTM->[코드]()  
-> using Bollinger band, moving average, macd, rsi, stochastic, roc, ohlc(22var)  
-> using 5day data and prediction 10 days later  
-> RMSE : 0.19156382527348761  
-> 문제점 : PCA 검사 결과 차원의 저주 문제 발생.   
  
04. samsung stock price prediction using PCA, LSTM->[코드]()  
-> using no.3 var  
-> PCA를 활용하여 4개의 변수를 활용하여 LSTM을 돌려봄  
-> RMSE : 0.13721298327731987  
-> 문제점 : 테스트 결과 RMSE가 약간 하락하였지만 큰 의미가 없음.  

05. samsung stock price prediction(10 var) using LSTM->[코드]()  
-> 3번 모델에서 사용한 변수의 상관계수를 확인한후 var을 축소함. 
-> PCA를 활용하여 4개의 변수를 활용하여 LSTM을 돌려봄  
-> RMSE : 0.12660472013769297  
-> 문제점 : 3번의 모델보다는 향상되었으나 아직 RMSE가 큼.  

06. samsung stock price prediction(9 var) using PCA, LSTM->[코드]()   
-> using no.5 var+Close price-2var  
-> PCA를 활용하여 2-4개의 변수를 활용하여 LSTM을 돌려봄  
-> RMSE : 0.1691978670334448  
-> 문제점 : 3번,4번을 비교하면 PCA한 모델이 RMSE가 더 작게 나오지만 지금의 상황에서는 PCA하지 않았을때가 작게 나타남.   
-> 향후 계획 : close 추가

  ------------------------

07. samsung stock price prediction(9 var) using LSTM->[코드]()  
-> using no.5 var+Close price-2var  
-> PCA를 활용하여 4개의 변수를 활용하여 LSTM을 돌려봄  
-> RMSE : 0.13191855162665575  
-> 문제점 : 변수의 수를 줄이고 PCA를 활용해 주성분을 2-4개 조절해보았지만 큰 변화는 보이지 않음.

08. samsung stock price prediction(9 var) using LSTM->[코드]()  
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

9. samsung stock price prediction prophet->[코드]()   

-> close와 날짜만 활용하여 모델을 만듬  
-> holiday는 주말과 공휴일로 모두 설정함  
-> 문제점 : 그래프가 2번씩 중복되어 사용되어짐.  
-> prophet은 정확한 예측보다는 추세를 확인하는데 좋을 것같음.(주가 자체가 주기가 없어서 규칙성을 보기 힘듬)  
-> 정확한 알고리즘을 모르다 보니, 파라미터에 의존하면서 모델을 만드는 경향이 큼.

-------------------------------------

10. 재무상태표와 주가를 활용한 주가예측  
  
-> train set = 2017-01-01 ~ 2019-06-31
-> test set = 2019-07-31 ~ 2020-12-31

-> 많은 논문에서는 단순히 OHLC를 사용하지 않고 새로운 방법으로 변형시키거나 다양한 변수를 포함시켰다.  
-> 따라서 지금까지는 단순히 OHLC를 활용하여 주가를 예측하였지만, OHLC뿐만 아니라 재무제표를 통해 6개의 새로운 변수를 같이 활용하여 주가예측을 해볼예정.  

    10_1. dart 크롤링->[코드]()  
    -> 기본적 분석을 위한 지표를 만들기 위해서 dart에서 api 인증키를 받고 삼성 3년치 재무제표를 크롤링함  
    -> 하나의 보고서는 쉽게 가져올 수 있지만, dart의 단점이 매년 for문으로 뽑아올수 없다는 단점이 있어서 몇 개는 수동으로 뽑아줌.(재무상태표는 동일하나 현금흐름표과 손익계산서의 위치가 다 다르다)  
    -> 이를 활용하여 기본적 분석을  지표를 만들예정  

    10_2. 재무제표 정리->[코드]()  
    -> 위에서 크롤링한 재무제표를 기반으로 다양한 변수를 생성.   
    -> 주식의 수를 분기별로 알수 없으므로 분기별로 알 수 있는 정보를 활용함.   
    -> ROE, 유동비율, 부채비율 등 6개 변수를 뽑음.   
    -> 추후 추가 예정   
    
    10_3. 기술적 지표 설정-> [예측한 주가 추세](https://github.com/suminwooo/project1/blob/master/prophet1%20%EA%B0%9C%EB%B0%9C%ED%9B%84%20%EC%8B%9C%EA%B0%81%ED%99%94.ipynb)  
    -> 지금까지는 재무상태표를 활용한 기본적 분석 지표를 만들었음.
    -> 3번에서는 OHLC와 Volume을 살짝 변형하여 2번의 변수와 같이 사용할 예정
