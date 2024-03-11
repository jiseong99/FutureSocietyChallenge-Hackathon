# 미래 사회문제 해결 아이디어 해커톤

### 로드킬 발생 저감을 위한 도로 생태계 안전 강화 아이디어 제시
#### 경기남부 및 충청도를 중심으로

팀원 : [유수정](https://github.com/CristalU), [한지성](https://github.com/jiseong99), [조예은]



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
<br/>

+야생동물 '로드킬' 1년새 72% 증가, 보호종까지 예외는 없음
+로드킬 건수가 점차 증가하자, 정부는 동물 찻길 사고 저감 대책(20~22)를 추진한 바 있음
+생태통로, 유도울타리 등을 통하여 실제 로드킬 횟수가 줄어듦
+하지만 유지보수가 제대로 되지 않고, 현재에도 많이 로드킬이 일어나고 있기에 이용 효율을 높이는 생태통로 입지 재선정 및 유지보수가 중요하다고 판단 



  
## 2. EDA
### 활용 데이터 확인
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/23d40689-de62-47cd-b0a6-3c0977c3801e)



### 분석 로드맵
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/855675bc-dd91-47d1-b6d2-6942df4f2059)



<br/>

### 데이터 시각화 / Data Visualizaiton
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/f6b78e94-e788-4c01-9818-4e79fb5dbe5a)

<br/>

![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/df8dfb03-fb26-4c25-8dcc-717be463d9ad)

+ 충청, 경기남부 지역에서 로드킬 다수 발생 및 야생동물 밀집 -> 충청, 경기남부 위주의 분석 진행
  
<br/>

![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/8efa05a5-418c-45b6-8a9f-03242a4c5ef1)

<br/>

![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/87c7cab7-b07b-47db-b0dc-b224ad87b8b2)

<br/>

  
## 3. 해결방안
### 생태통로 신규입지 우선순위 선정
+ 파생 변수 생성

<br/>

+ km 당 차로 수 = 노선 일 평균 이동 차량 수 / 노선 길이
+ 개체 마리 당 생태통로 = 반경 생태통로 수 / 반경 동물 개체 수
+ 개체 마리 당 울타리 길이 = 울타리 평균 길이 / 반경 동물 개체 수

<br/>

### 입지 선정 우선 순위 결정 가중치 결정
+ 변수 간 상관관계 확인
  
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/5e1acd10-3200-4870-b319-7e7586c3d47d)


### Elbow, Silhouette, Gap Statistic Algorithm
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/192c7fff-48e9-4e8f-a314-39364ddba816)
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/abc209c0-e732-4e9b-9035-0d11dfbaf27e)
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/2dcbd6f1-779a-4bbd-b84f-7176835537ab)


+ 최적의 클러스터 개수 선정 (n_clusters = 8)
+ Elbow : 9, Silhouette : 12, Gap Statistic : 4
+ (9 + 12 + 4 ) / 3 = 8
  
<br/>

### 경기 남부 및 충청 지역에 우선순위 맵핑
+ 색의 진하기가 진할수록 우선순위가 높음
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/a5cb526d-cbd5-4db5-aeff-a61b6e478c69)

<br/>

## 4. 관련 정책 아이디어
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/914209cd-a388-4414-98df-7d7dd7dfde74)
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/9d52b756-ae36-4f09-bee4-33f2a60b8902)

<br/>

## 5. 기대효과 및 한계점
### 기대효과
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/22c1f7c1-8d2a-4999-942e-7f583700812e)

+ 지역 사회의 환경 인프라 향상에 다양한 긍정적인 영향을 미칠것으로 사료됨

  <br/>

### 한계점
+ 활용할 수 있는 데이터 부족으로 인한 로드킬 요인 분석 및 원인 파악 어려움
+ 작은 동물이나 교통량이 적은 지역에서는 사고가 감지되지 않아 실제 규모를 정확하게 판단하는 것이 어려움 
+ 로드킬 관련 데이터는 지리적, 시간적, 지역에 따라 일관된 데이터가 아닌 편향된 데이터가 많음
+ 도로 교통 데이터의 정확도가 낮음 
+ 관련 선행연구 부족으로 참고 자료 한계 존재
![image](https://github.com/jiseong99/FutureSocietyChallenge-Hackathon/assets/137580822/35ad9be4-29e4-4552-ae75-e894935577af)


  
