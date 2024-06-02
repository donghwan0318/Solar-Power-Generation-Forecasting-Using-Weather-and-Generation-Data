# 2023-2-PSAT-team-deeplearning
2023년 2학기 통계분석학회 P-SAT 딥러닝팀 주제분석  



## 💻 프로젝트 소개

<예측 기상&발전량을 활용한태양광 발전량 예측>☀️

POSTECH과 H energy가 함께 주최하는 태양광 발전량 예측 대회 - 대학 및 대학원생 대상 제5회 OIBC CHALLENGE

활용 데이터: 예측된 발전량, 예측대상 발전소 실제 발전량, 운량/기온/습도 등을 포함한 13개의 기상데이터, 예측된 발전량에 대한 인센티브(모델평가 점수)
데이터 출처: 주최 측

개발 기간(duration): 23.10.22 ~ 23.11.17


## ❤️ 팀 구성 및 역할 (Team members)
- 이정환(팀장): 태양전지 도메인 조사, 파생변수(시간변환/계절변환), LGBM, LSTM, MLP+LGBM 앙상블,RNN+LGBM 앙상블,SCINet
- 김동환: 태양전지 도메인 조사, 시계열 클러스터링, 회귀+LGBM 앙상블,구조적시계열모형
- 권가민: 앙상블, XGB, 상관분석, x변수 클러스터링(오차율/계절), 오차율/발전량 패턴파악(시간별/계절별), 
- 박채원: 앙상블,LGBM, 상관분석, 선형회귀계절, x변수 군집화(오차율/계절), 변수선택(계절)
- 박준영: 앙상블, 상관분석, 선형회귀시간/계절, 유사도예측, x변수 군집화(오차율/계절)

## 🔍 분석 흐름(flow)
1. 도메인 조사
2. 데이터 전처리(기사 데이터 감성분석, 데이터 병합, 결측치 보간, 자료형 수치형으로 통일, 시간 순 정렬)    
4. EDA (X변수간 EDA, Y~X변수간 EDA)
5. 등락률(continuous) -> 매수/유지/매도(categorical) 라벨링
6. 변수 선택 - feature selection
      <br>(인과관계 검정, VIF, PCA, 요인분석, feature importance, KS검정 시도)
7. labeled y변수 예측 모델링 (with imbalanced class problem😭)
8. 예측 결과 시각화 및 결과 분석


## 📈 모델링 개요
![화면 캡처 2023-06-14 212644](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/ef628d73-e77e-4e37-a0ec-97bb7c19c735)


## 🚨 클래스 불균형 문제
매수/매도에 비해 예측 라벨의 수가 많아서 클래스 불균형이 심각 -> 매수/매도에 대한 예측 성능 저조

💡 해결을 위한 노력들
- 단순 정확도나 f1-score가 아닌 평가지표 커스텀을 통해 프로젝트 목적에 적합한 모델 선택 (ex. 매수, 매도의 정확도, 정밀도의 평균 / 매수, 매도, 유지 정확도의 평균 etc)
- 모델 학습 시 클래스별 샘플 가중치 반영
- 라벨 회귀 예측 -> 검증 set으로 분류 threshold 결정 -> 최종 분류


## 📃 결과
![화면 캡처 2023-06-14 212213](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/60fad7c1-5b94-4a24-a004-aaed0c71976c)
![화면 캡처 2023-06-14 212242](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/ab0a5ce1-e32e-4508-a379-f7543abe4bbd)
![화면 캡처 2023-06-14 212511](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/4a5403a3-b952-433f-bd1c-527da7ebc030)
![화면 캡처 2023-06-14 212533](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/e84f0203-acd0-4baa-9579-9108bd9abd88)
![화면 캡처 2023-06-14 212603](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/c36b4367-947a-4837-9d38-32889bfea767)
![화면 캡처 2023-06-14 212619](https://github.com/mminiiii/ModelingStockBuySellPrediction/assets/90174257/1206e5ed-a46d-47a9-b6d2-e7b03b96fd66)
