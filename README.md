# Bachelor_Thesis_LineWebtoon
[학사논문] 글로벌 웹툰 서비스(라인 웹툰) 데이터를 이용한 흥행 예측 모델 구축- 머신러닝을 중심으로


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

