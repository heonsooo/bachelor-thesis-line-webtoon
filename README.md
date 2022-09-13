# Bachelor_Thesis_LineWebtoon
[학사논문] 글로벌 웹툰 서비스(라인 웹툰) 데이터를 이용한 흥행 예측 모델 구축- 머신러닝을 중심으로

## 기획 의도
번역에 필요한 시간과 비용을 성공할 컨텐츠에 집중하여 제한된 자원 속에서 성공 케이스를 늘려 이용자를 증가시키기 위한 최적화(최소 비용, 최대 이용자)를 목표로 기획했습니다.

## 연구의 목표
흥행 예측에 영향력이 큰 특징, 피처를 도출하여 웹툰의 번역 우선순위를 선정하는데 도움을 주는 것이었습니다.

## 연구 과정
직접 selenium을 이용한 웹 크롤링을 통해 데이터를 수집했습니다.
수집한 데이터는 pandas 라이브러리를 이용해 저장했습니다.
전처리 과정은 중복 웹툰 제거, 범주형 데이터는 원핫인코딩, 숫자 데이터는 단위 통일 후 피처별 비중 차이를 최소화하기 위해 스케일링을 진행했습니다.
데이터 라벨링 후 사이킷런의 모형을 사용했습니다.
이때, 딥러닝이 아닌 랜덤 포레스트와 로지스틱 회귀 모형을 사용하였습니다. 그 이유는 예측 결과에 영향을 주는 피처를 도출할 수 있었기 때문이었습니다.


## [[라인웹툰]웹툰 데이터 자동 수집](https://github.com/heonsooo/Bachelor_Thesis_LineWebtoon/blob/main/%5B%EB%9D%BC%EC%9D%B8%EC%9B%B9%ED%88%B0%5D%EC%9B%B9%ED%88%B0%20%EB%8D%B0%EC%9D%B4%ED%84%B0%20%EC%9E%90%EB%8F%99%20%EC%88%98%EC%A7%91.ipynb)

[웹툰 데이터 수집 자동화 Logics]
1. 마우스 포인트 좌표 및 함수설정
2. 각 장르의 첫번째 웹툰 클릭
3. 웹툰 상세 페이지의 url 획득
4. 웹툰 상세 페이지의 제목, 장르, 작가, 구독자 수, 별점 스크래핑
5. 최신 회차(2주 전, 혹은 1주 전) 클릭 및 해당 회차 url 복사
6. 해당 회차 각 이미지의 height 총합하여 분량 계산 후 amount변수에 저장 
7. 셀레니움 이용해서 베스트 댓글의 좋아요 수(동적 데이터) 스크래핑
8. 뒤로가기 2번(라인 웹툰 장르 페이지)
9. 하나의 row에 5개 작품이므로 5번 반복 후 
   스크롤 내린 후 해당 작업 반복
10. pandas - DataFrame으로 data저장

### 시연 영상
[![Video Label](http://img.youtube.com/vi/7zwFszKI4YA/0.jpg)](https://youtu.be/7zwFszKI4YA?t=0s)




## [[라인웹툰]데이터 전처리1.ipynb](https://github.com/heonsooo/Bachelor_Thesis_LineWebtoon/blob/main/%5B%EB%9D%BC%EC%9D%B8%EC%9B%B9%ED%88%B0%5D%EB%8D%B0%EC%9D%B4%ED%84%B0%20%EC%A0%84%EC%B2%98%EB%A6%AC1.ipynb)
* 새로운 컬럼(Total Likes)생성 후 각 작품의 좋아요 수를 추가  
  

## [[라인웹툰]데이터 전처리2.ipynb](https://github.com/heonsooo/Bachelor_Thesis_LineWebtoon/blob/main/%5B%EB%9D%BC%EC%9D%B8%EC%9B%B9%ED%88%B0%5D%EB%8D%B0%EC%9D%B4%ED%84%B0%20%EC%A0%84%EC%B2%98%EB%A6%AC2.ipynb)
* 장르 - 원핫인코딩 이용  
  각 장르(SF, Drama, Romance, Superhero, Supernatural, Slice of life, Thriller, Action, Comedy, Fantasy)의 새로운 컬럼을 만들고,  
  해당 웹툰의 장르 값을 df.loc사용하여 1, 0으로 기입.   
    
* df.str.replace() 이용하여 특정 컬럼(Total Likes, Subscribers) 숫자 단위(M:1,000,000 ,K:1,000)를 숫자로 변환 처리.  
   

## 수집 데이터 결과
![data_webtoon](https://user-images.githubusercontent.com/68042068/119069846-d975df80-ba21-11eb-8df9-4b530dde7df9.jpg)


## [[라인웹툰]데이터 라벨링(Target_등급) .ipynb](https://github.com/heonsooo/Bachelor_Thesis_LineWebtoon/blob/main/%5B%EB%9D%BC%EC%9D%B8%EC%9B%B9%ED%88%B0%5D%EB%8D%B0%EC%9D%B4%ED%84%B0%20%EB%9D%BC%EB%B2%A8%EB%A7%81(Target_%EB%93%B1%EA%B8%89)%20.ipynb)

[사용 기술 : 웹크롤링, Pandas, 스케일링]

* 머신러닝(분류)을 위한 데이터 라벨링
* 라인웹툰에서 제공하는 요일별 현재 인기 웹툰을 2단계의 등급으로 target 라벨링


## [[라인웹툰]영어_이진분류.ipynb](https://github.com/heonsooo/Bachelor_Thesis_LineWebtoon/blob/main/%5B%EB%9D%BC%EC%9D%B8%EC%9B%B9%ED%88%B0%5D%EC%98%81%EC%96%B4_%EC%9D%B4%EC%A7%84%EB%B6%84%EB%A5%98.ipynb)
  
* 머신러닝 : Scikit-learn 랜덤 포레스트, 로지스틱 회귀를 이용한 이진분류 분류 모델 정확도 비교 

![image](https://user-images.githubusercontent.com/68042068/144777372-c25c50d6-5742-491d-bba2-6141718db949.png)
![image](https://user-images.githubusercontent.com/68042068/144777388-597d0cff-469d-408d-9b9e-cf51042fbc19.png)

![image](https://user-images.githubusercontent.com/68042068/144777550-7f9d268d-ea0f-4f7b-9bd4-eb39d0892463.png)
: 랜덤포레스트 / 피처 중요도
![image](https://user-images.githubusercontent.com/68042068/144777526-bb6a2fad-57b3-49b7-a094-0311961465e1.png)
: 로지스틱 회귀 상관계수

## [[라인웹툰]스페인어_이진분류.ipynb](https://github.com/heonsooo/Bachelor_Thesis_LineWebtoon/blob/main/%5B%EB%9D%BC%EC%9D%B8%EC%9B%B9%ED%88%B0%5D%EC%8A%A4%ED%8E%98%EC%9D%B8%EC%96%B4_%EC%9D%B4%EC%A7%84%EB%B6%84%EB%A5%98.ipynb)
  
* 머신러닝 : Scikit-learn 랜덤 포레스트, 로지스틱 회귀를 이용한 이진분류 분류 모델 정확도 비교 

![image](https://user-images.githubusercontent.com/68042068/144777589-1ba3f892-a3f5-4982-84bf-769648a32c17.png)
![image](https://user-images.githubusercontent.com/68042068/144777598-fb7ad6c4-14cb-4601-996b-8cedc6595bef.png)

![image](https://user-images.githubusercontent.com/68042068/144777579-562838ef-6d83-4131-85a4-1795dd79650d.png)
: 랜덤포레스트 / 피처 중요도
![image](https://user-images.githubusercontent.com/68042068/144777575-2e97c0ac-d02f-4157-8cb3-2820a0de1ebc.png)
: 로지스틱 회귀 상관계수


## [[라인웹툰]인도네시아어_이진분류.ipynb](https://github.com/heonsooo/Bachelor_Thesis_LineWebtoon/blob/main/%5B%EB%9D%BC%EC%9D%B8%EC%9B%B9%ED%88%B0%5D%EC%9D%B8%EB%8F%84%EB%84%A4%EC%8B%9C%EC%95%84%EC%96%B4_%EC%9D%B4%EC%A7%84%EB%B6%84%EB%A5%98.ipynb)
  
* 머신러닝 : Scikit-learn 랜덤 포레스트, 로지스틱 회귀를 이용한 이진분류 분류 모델 정확도 비교 

![image](https://user-images.githubusercontent.com/68042068/144777626-27cc8e87-26d5-45c8-8ddf-e28008ad04da.png)
![image](https://user-images.githubusercontent.com/68042068/144777637-806141d9-d84d-46f4-bc7c-00825934f25d.png)

![image](https://user-images.githubusercontent.com/68042068/144777619-caa54cfe-fd9c-4d16-ba4d-0bb0ee7b27d5.png)
: 랜덤포레스트 / 피처 중요도

![image](https://user-images.githubusercontent.com/68042068/144777610-1c9f7938-3a62-403a-a872-f45be1b065dd.png)
: 로지스틱 회귀 상관계수

