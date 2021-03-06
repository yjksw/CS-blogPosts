# [머신러닝] 딥러닝 영화 개인화 추천 - Part.3

영화 개인화 추천 포스트의 마지막 파트이다. 이전까지는 데이터를 입력받아서 전처리하고, 모델을 구축하여 학습의 원리에 대해서 간략하게 알아보았다. 결국 학습을 하면서 loss 값을 optimizing 하는 과정에서 학습된 사용자의 영화에 대한 예측 평점인 y_hat이 출력되는 것인데, 검증셋에 대해서 출력된 y_hat의 값에 대해서 어느 정도의 후처리를 하여 사용자에게 추천할 영화 리스트를 선별하는 작업이 필요하다. 이번 포스트는 학습된 모델을 가지고 검증 및 테스트를 진행한 후에 모델에서 출력한 예측 평점에 대해서 사용자에게 추천할 영화 리스트를 추출하는 작업에 대해서 이야기해보자. 



## 개요

**전체적인 검증 및 테스트 과정은 다음과 같다. **

1. 모델을 포팅해 사용자와 추천 영화 갯수를 입력한다. 
2. 영화 목록이 들어가있는 입력 데이터를 모델에 넣어 prediction을 진행한다. 
3. 모델에서 나온 예측값과 **movieId** 가 있는 데이터를 concat 하여 이어붙인다. 
4. *movies.csv* 파일에 있는 영화 아이디별 영화 제목을 불러서 3번 데이터에 concat 한다. 
5. 예측 평점을 기준으로 sorting 하여 내림차순 정렬을 한다. 
6. 1번에서 입력된 영화 갯수만큼 잘라서 영화 제목을 출력해준다. 



## 세부 구현

파이썬으로 구현한 데이터 후처리 부분이다. 

1. 입력 데이터에 대한 인코딩 후 모델에 넣어 학습하기 

```python
target_usr = df_test['userId'] == userId #특정 유저에 대해서 filtering 하기 
target_df = df_test[target_usr]
users = torch.LongTensor(target_df.userId.values) #유저 목록 데이터 
items = torch.LongTensor(target_df.movieId.values) # 영화 목록 데이터
y_hat = model(users, items) #예측 ratings y_hat에 저장
```



2. 기존 영화 목록 데이터에 예측 평점 매칭하여 이어붙이기

```python
target_df = target_df.reset_index(drop=True)
new_df = pd.concat([target_df, predictions], axis=1) #이어붙인 dataframe
```

아래 이미지는 검증을 위해서 입력된 데이터를 모델에 넣어 학습했을 때 나온 결과 예측 rating이다. 

<img src="prediction.png" width=70% >

 

3. 영화 ID 별 영화 제목 매칭하기 

```python
movies = pd.read_csv('./ml-latest-small/movies.csv')
new_df = pd.merge(new_df, movies, on='movieId')
```

오른쪽에 나와있는 영화제목 데이터를 위의 dataframe에 이어붙여서 영화 아이디에 대한 영화 제목을 매칭하는 과정이 필요하다. 

<img src="movieName.png" width=70%>



최종 영화 목록을 선별하여 출력하기 이전에 필요한 모든 dataframe들을 concat 했을때의 화면이다. 모든 데이터들을 이어붙였기 때문에 다소 지저분하지만 한눈에 볼 수 있는 장점이 있다. 

<img src="test.png" width=50%>



## 결과

다음과 같은 입력에 대한 추천 영화 목록이 아웃풋으로 나온다. 아래 결과는 사용자 1에 대한 상위 6개의 영화추천이다. 

<img src="result.png" width=50%>



overfitting이나 underfitting이 되지 않고, 최적화된 학습 모델을 찾기 위해서는 여러번의 learning rate 조정 분석이 필요하다. 이것은 정답이 없기 때문에 충분한 데이터를 가지고 learning rate와 epoch를 변경하면서 여러 테스트 과정이 필요하다. 나도 굉장히 많은 learning rate를 시도해보면 실제 검증 validation loss와 train loss 를 비교하고 그래프를 그려가면서 나름 최적화 되었다고 생각하는 지점을 찾는 과정을 거쳤다. 

<img src="learningRate.png" width=70%>



매우 간단한 구현이었지만 딥러닝에 대해서 더욱 알 수 있는 경험이었다. 무엇보다 우리 삶에 밀접하게 쓰여지고 있는 기술을 직접 구현해보고 처리해보니 더욱 흥미로웠다. 그렇지만 당근마켓, 페이스북, 유투브의 개인화 추천관련 논문과 블로그 등을 읽어보니, 정말 고려해야할 것도 필터링 해야 할 부분도 많다. 

**생각해볼 것**은 다음과 같다.

1. 데이터베이스에 있는 모든 영화목록을 매번 넣어서 예측 평점을 모두 predict 한 뒤, sorting 하여 최상위 예측 평점 순으로 영화를 고르는 것은 매우 비효율 적이다. 데이터 베이스에 있는 영화가 100만개가 넘어가거나 할 경우 매번 그것을 반복할 수 없기 때문이다. 당근마켓의 블로그를 참고해보면 1차로 후보모델을 추출한 뒤에 일부 후보를 추리는 1차 작업을 한 뒤에, 해당 후보 모델에서 랭킹을 매기는 랭킹모델을 구축한다. 이렇듯 여러 과정을 거쳐서 일부 후보들을 filtering 하는 과정이 필요할 듯 하다. 
2. cold start 문제를 고려해야 한다. 처음 들어온 유저, 아무도 랭킹을 매기지 않은 영화에 대해서는 영영 추천하지 못하는 상황이 되어버릴 것이다. cold start에 대한 여러 고찰과 방법들에 대해서 나와있으니 한번 참고해보자. 