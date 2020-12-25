## 네이버 영화 리뷰 감정분석기 개발<br>
(고려대 디지털금융공학석사 과정 기말 프로젝트) <br>
sentimental analysis for 'nsmc:naver sentiment movie corpus'

## **참고한 소스**

- https://github.com/deepseasw/bert-naver-movie-review/blob/master/bert_naver_movie.ipynb

## **분석 순서**

0. 목적
1. colab 연결
2. transformer 설치
3. 필요한 라이브러리 가져오기
4. 데이터 불러오기
5. train set 전처리
6. test set 전처리
7. 모델링
8. 학습 및 검증
9. 최종 제출데이타에 대한 예측 수행

## **실행 방법**

- 코드과정마다 텍스트로 설명이 되어 있으니, 코드 파일을 열어보시기 바랍니다.

## **데이터**

- ratings_test.txt <br>
ratings_train.txt <br>
출처 : https://github.com/e9t/nsmc

- ko_data.csv <br>
출처 : https://www.kaggle.com/c/korean-sa-competition-dfe610/data

- nsmc_final.csv <br>
코드를 돌려서 나온 최종값 <br>
이것을 캐글 클래스 경진대회에 올려서 평가함

## **패키지**

- tensorflow
- torch
- pandas
- numpy
- RobertaTokenizer 등

## **전처리 및 모델링**

 - BERT 사용
 - optimizer는 AdamW 사용
 - parameter 조정 
 
## **평가**

- 캐글 클래스 경진대회에 올린 결과 <br>
public 결과는 0.87573(15등) <br>
private 결과는 0.88219(18등) <br>

![nsmc_c_title](https://user-images.githubusercontent.com/76524741/103125374-3fa64280-46ce-11eb-8415-1cf3f31d0882.png)
![nsmc_public_ldbd](https://user-images.githubusercontent.com/76524741/103125383-43d26000-46ce-11eb-9225-e36ff03fadea.png)
![nsmc_private_ldbd](https://user-images.githubusercontent.com/76524741/103125384-446af680-46ce-11eb-8967-47025e280779.png)

## **팁**

1. 데이터 양이 충분치 않다고 생각될 때는 가용가능한 모든 데이터를 사용하면 정확도 향상에 도움이 될 수도 있음 <br>
실제로 train data만을 가지고 돌렸을 때 보다 성능이 좋아짐
2. Large 모델이 Base 모델보다 시간은 더 걸리지만, 정확도 향상에 도움이 됨 <br>
마찬가지로 대소문자 구분하지 않는 것(소문자화 = true)보다 구분하는 것(flase)가 약간이나마 향상 됨<br>
여기서는 Base 모델 사용
3. 배치사이즈를 크게 하면 속도향상에는 도움이 되나, 메모리가 좋아야 가능함. 256으로 돌려보니, runtime error가 발생하였음. <br>
안전하게 32로 세팅
4. 파라미터 조정(learning rate, epoch, batch size 등) 조정하여 여러번 돌려볼 필요가 있음
