# 미래 사회문제 해결 아이디어 해커톤

### 로드킬 발생 저감을 위한 도로 생태계 안전 강화 아이디어 제시
#### 경기남부 및 충청도를 중심으로

팀원 : [유수정](https://github.com/아줌마), [한지성](https://github.com/jiseong99), [조예은]



## 1. 개요
#### [공모 주제]
+ 환경, 질병/재난, 도시, 직업 관련 미래 사회문제 예측 및 해결방안 제시

#### [주최 / 주관]
+ 주최 : 미래와 소프트
+ 주관 : ET EDU (이티에듀)
+ 링크 : https://edu.ggumeasy.com/?pn=product.view&pcode=H7843-R5115-J7144

#### [분석 배경 및 필요성]
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/573f2795-f1c1-42d7-8670-5d2e108b445c)
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/d4bff781-a57c-48a6-9851-ff161b3e9bac)
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/2a02ca7c-b997-4e1f-8efc-b8db437b9f77)
+야생동물 '로드킬' 1년새 72% 증가, 보호종까지 예외는 없음
+로드킬 건수가 점차 증가하자, 정부는 동물 찻길 사고 저감 대책(20~22)를 추진한 바 있음
+생태통로, 유도울타리 등을 통하여 실제 로드킬 횟수가 줄어듦
+하지만 유지보수가 제대로 되지 않고, 현재에도 많이 로드킬이 일어나고 있기에 이용 효율을 높이는 생태통로 입지 재선정 및 유지보수가 중요하다고 판단 



  
## 2. EDA
### 활용 데이터 확인
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/23d40689-de62-47cd-b0a6-3c0977c3801e)



### 분석 로드맵
<img src="https://github.com/svng-zu/LG-AIMERS/assets/70852514/fc7496a8-71a4-4e15-9745-3ab54bb6fa59" alt="data1" width="50%" height="50%">

+ 타겟 변수 is_converted 의 True, False 비율이 약 11: 1로 불균형이 있음을 알 수 있음
+ 클래스 불균형 데이터는 모델 학습 시 과적합의 위험이 큼
  + 언더샘플링으로 해결

<br/>

### 범주형 변수
<img src="https://github.com/svng-zu/LG-AIMERS/assets/70852514/c3bd18ae-8371-4e30-8cad-2c185750fd4c" alt="data" width=30% height=30%>
<img src="https://github.com/svng-zu/LG-AIMERS/assets/70852514/ee3fd6df-0429-46b3-927c-ac8293a9e9bf" alt="data" width=30% height=30%>
<img src="https://github.com/svng-zu/LG-AIMERS/assets/70852514/fdb061c3-9a6c-4c4c-aa0f-f3c916246ef3" alt="data" width=30% height=30%>

+ 대부분의 변수에서 희소 범주의 개수가 많음
+ 희소 범주들은 모델 학습 시 트리의 깊이가 깊어지고 과적합으로 모델 성능 저하시킴
  + 희소 범주를 '기타' 범주로 처리

### 수치형 변수
<img src="https://github.com/svng-zu/LG-AIMERS/assets/70852514/ccff87f9-e838-4de0-aec4-47fe1caab7e8" alt="data" width=50% height=50%>

<br/>

#### 상관계수
<img src="https://github.com/svng-zu/LG-AIMERS/assets/70852514/5d40481f-2a2b-4191-be82-bd957a022311" alt="data" width=50% height=50%>

+ 변수간의 상관성이 적음을 알 수 있음
  
<br/>

## 3. 데이터 전처리
### 컬럼 삭제
+ 중복 변수 제거 : customer_country.1
+ 결측치가 과반인 변수는 제거 : product_subcategory, product_modelname, business_area, business_subarea
+ 변수 중요도가 매우 낮은 변수 제거 : id_strategic_ver, it_strategic_ver, idit_strategic_ver, ver_cus, ver_pro

<img src="https://github.com/svng-zu/LG-AIMERS/assets/70852514/0b20e0d1-c783-4a7f-a6d9-bcb66c09792e" alt="data" width=70% height=70%>

### 같은 의미의 다른 데이터는 같은 범주로 처리
+ etc, other, others $\rightarrow$ etc
+ end-customer, end customer, end-user $\rightarrow$ end_user

<br/>

### 개수가 1개인 범주들을 기타 처리
+ 결측치와는 다르게 처리

<br/>

### 결측치 처리
+ 수치형 데이터는 0 대체해도 무방 했음
+ 범주형은 None이라는 문자열로 범주처럼 처리
<br/>

## 4. 모델링

### 모델 선택
#### autoML - pycaret 사용

__pycaret__ <br/>
ML workflow을 자동화 하는 opensource library로 여러 머신러닝 task에서 사용하는 모델들을 하나의 환경에서 비교하고 튜닝하는 등 간단한 코드를 통해 편리하게 사용할 수 있도록 자동화환 라이브러리

#### autoML 실행결과
<img src="https://github.com/svng-zu/LG-AIMERS/assets/70852514/1571c80d-74b2-40ce-bf06-91e4caea475e" alt="data" width=70% height=70%>

+ 각 모델에 대해서 어떤 모델을, 몇 개를 조합할 것인지에 대한 실험이 필요

<br/>

## 5. 과적합 핸들링

### 1. 언더샘플링
+ 타겟 변수의 True와 False 값의 비율이 약 11:1로 클래스 불균형이 심한 상태임
+ 이를 그대로 학습하게 되면 False 클래스에 편향된 모델이 되기 때문에 오버 샘플링 / 언더 샘플링을 진행
+ 실험 결과 언더 샘플링의 F1-score가 더 높아 언더 샘플링을 진행

정보 손실의 위험 $\rightarrow$ 앙상블 + 보팅으로 해결

<img src="https://github.com/svng-zu/LG-AIMERS/assets/70852514/cec9466f-2b4e-4ecc-9aae-41c4f86337ef" alt="data" width=50% height=50% left=0>

+ public score 0.2.. 에서 0.6 대로 상승

<br/>

### 2. 앙상블
+ 여러개의 예측 모델을 결합하여 과적합을 줄이고 모델을 일반화하는 방법
+ 앞서 고른 상위 5개 모델을 앙상블하여 모델 일반화 진행 함.

<br/>

### 3. 모델 학습 시 편향되어 학습되는 요인 찾기
+ train 데이터에서 customer_idx = 25096 의 경우 영업 횟수 2421 모두 성공한 것으로 관측됨. 
+ train 데이터의 True 개수가 4850개 임을 생각하면 위 idx에 편향되어 학습된다고 판단함
+ pubilc score 0.7대로 상승

<br/>

### 4. Voting
+ 언더 샘플링 시 정보손실의 문제가 있음.
+ False 데이터 54449 개를 랜덤 셔플 후, 모두 20등분하고 True와 합쳐 클래스 비율이 1:1인 데이터셋 20개를 생성.
+ 각 셔플의 모델에서의 결과를 확률로 받은 후 0, 1 클래스의 확률을 평균을 내어 최종 결과로 생성 (Soft voting)
$\rightarrow$ public score 0.02 정도 상승을 보임

<br/>

## 6. AB test
![image](https://github.com/Junoflows/LG_Aimers_phase2/assets/108385417/2717cbda-04ff-43da-87d6-7e2d8b8ca309)

+ 모델 학습은 GridSearch를 이용

<br/>

## 7. 결과 및 리뷰

### 모델 선택
앞서 선택한 5개 모델 중 5개, 3개, 1개로 나누어 앙상블 후 가장 public score가 높은 모델 선택
+ 'xgb' 1개 사용시 가장 성능이 높음.

### 리뷰
+ 실제 현업에서 사용하는 데이터는 전처리에 많은 시간을 쏟아야 한다는 것을 느낌
+ 과적합을 해결하기 위해 많은 고민을 했고 그 과정에서 데이터와 모델에 대한 이해를 키울 수 있었음
+ AutoML 의 pycaret 을 일찍 적용했더라면 실험 과정의 튜닝 시간을 효율적으로 사용했을 것 같음
+ 임의로 설정한 값들에 대해 정확한 튜닝을 하지 못하였던 것이 아쉬움(시간 및 제출 횟수 부족)

