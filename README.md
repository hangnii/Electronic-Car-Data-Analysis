# Electronic Car Data Analysis (전기차 데이터 EDA)
![image](https://user-images.githubusercontent.com/92846399/158539972-71753c2c-9a1c-4abf-bb53-7f5923f1ac7c.png)

## Contents
- 1.[프로젝트 소개](#1-프로젝트-소개)
- 2.[데이터 수집](#2-데이터-수집)
- 3.[SQL ETL](#3-SQL-ETL)
- 4.[분석 및 시각화](#5-분석-및-시각화)
- 5.[REIVEW](#6-REVIEW)

----
</br>
</br>

## 1. 프로젝트 소개

</br>
</br>
</br>

## 2. 데이터 수집
### 🗃 2-1. 지역별 전기차 등록 현황 데이터
https://www.data.go.kr/data/15039554/fileData.do

### 🗃 2-2. 시도별 전기차 보조금 데이터 (웹 페이지 크롤링)
https://www.ev.or.kr/portal/buyersGuide/incenTive

### 🗃 2-3. 지역별 전기차 충전소 현황 데이터
https://www.data.go.kr/data/15039765/fileData.do

### 🗃 2-4. 지역별 환경문제에 대한 인식 데이터
- 현재 체감환경 : 대기
  - https://kosis.kr/statHtml/statHtml.do?orgId=101&tblId=DT_1SSEN011R&conn_path=I2
- 환경문제 인식 : 미세먼지 유입
  - https://kosis.kr/statHtml/statHtml.do?orgId=101&tblId=DT_1SSEN053R&conn_path=I2
- 환경문제 인식 : 기후변화
  - https://kosis.kr/statHtml/statHtml.do?orgId=101&tblId=DT_1SSEN051R&conn_path=I2

### 🗃 2-5. 지역별 미세먼지 데이터
- 초미세먼지(PM2.5)
  - https://kosis.kr/statHtml/statHtml.do?orgId=106&tblId=DT_106N_03_0200145&conn_path=I2
- 미세먼지(PM10)
  - https://kosis.kr/statHtml/statHtml.do?orgId=106&tblId=DT_106N_03_0200045&conn_path=I2
</br>
</br>

## 3. SQL ETL
### 🛰️ 3-1. database 생성
### 🛰️ 3-2. 테이블 생성
### 🛰️ 3-3. 데이터 적재
### 🛰️ 3-4. 데이터 전처리
  - 전국 17개 시도명 통일
    (ex. '경상북도' -> '경북', '제주특별자치도' -> '제주')
### 🛰️ 3-5. pandas로 옮기기




</br>
</br>

## 4. 분석 및 시각화

<img width="864" alt="image" src="https://user-images.githubusercontent.com/92846399/158545825-fe3707eb-b4f5-43de-9da8-440042a67279.png">


<img width="881" alt="image" src="https://user-images.githubusercontent.com/92846399/158545748-59c7ff5c-79b0-478f-bbb2-df9f11ac5b13.png">


<img width="793" alt="image" src="https://user-images.githubusercontent.com/92846399/158545606-f2b9335a-fe86-495b-9883-8d2e89c61d58.png">

'지역별 전기차 등록차량 수'와 상관계수가 높은 것은 '충전소 수' 뿐이다. 기후 변화 인식이 그나마 0.44로 다른 변수들 보다는 높지만 0.5를 넘기지 못하므로 크게 유의미하다 볼 수는 없다.

미세먼지와 초미세먼지 간 상관계수는 0.95로 상당히 높다.(어찌보면 당연한 결과)

초미세먼지(PM2.5)와 체감 대기환경, 미세먼지 유입에 대한 인식 간 상관계수는 각각 0.76, 0.75로 높은편인 반면, 기후 변화 인식은 0.34로 높은 편은 아니다.

미세먼지(PM10)와 체감 대기환경, 미세먼지 유입에 대한 인식 간 상관계수는 각각 0.71, 0.8로 높은편이고, 역시나 기후 변화 인식은 0.42로 높은 편이 아니다.

체감 대기환경과 미세먼지 유입 인식 간 상관계수는 0.71로 높은 편이나, 체감 대기환경과 기후 변화 인식 간 상관계수는 0.2로 낮다. 그런데, 미세먼지 유입 인식과 기후변화 인식 간 상관계수는 0.68로 높은 편이다. 흥미로운 지점이다.

전기차 보조금은 대부분 음의 상관관계로 나타나므로 현재 보조금의 금액 자체가 전기차 구매에 미치는 영향은 크지 않다고 볼 수도 있다.

</br>
</br>

## 6. REVIEW

### 결론 및 한계점
1. 전기차 구매 예상 요인으로 선정한 '미세먼지, 초미세먼지, 주관적 환경인식(체감 대기환경, 미세먼지 유입, 기후변화)' 변수들은 실제로 유의미한 영향을 미치지는 않는다. 
2. 하지만, 데이터가 많지 않고 지역별로 나누어 본 것이므로 실제로 변수 간 관계를 파악하기 위해선 더 고차원의 데이터가 필요하다.

3. 대체로 지역별 전기차 등록 수와 충전소 수는 연관이 있는 것으로 나타났는데, 구체적인 선후관계 파악 및 분석까지 이루어진다면 인과관계도 파악해볼 수 있을 것으로 보인다.
