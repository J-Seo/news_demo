## 추천 시스템 모델 설명서

### 1. 필수 설치 항목 설치

본 저장소의 requirements.txt를 작업 공간에 다운로드한 이후 아래와 같이 설치한다.  

```
pip install -r requirements.txt
```
### 2. 훈련 모델 정보

학습된 모델 checkpoint에 해당하는 파일을 제공한 구글 드라이브 링크를 통해 다운로드 받고

- sts_checkpoint/checkpoint_10.bin

- sts_checkpoint/news_checkpoint/checkpoint_51203.bin

에 위치할 수 있도록 한다.

### 3. 뉴스 기사 전처리

make_news_dataset.py를 실행하여, 훈련이 가능한 데이터셋 및 추천 기사 목록으로 활용할 데이터셋으로 분리하여 저장한다. 

```
python make_news_dataset.py
```

### 4. KorSTS 훈련

sts_fine_tune.py를 실행하여, KorSTS 데이터셋을 바탕으로 문장 유사도에 대한 파인 튜닝을 진행한다. 

```
python sts_fine_tune.py
```

### 5. news dataset labeling 작업

label_news_dataset.py를 싱행하여, 4번에서 저장한 파인튜닝 파라미터를 로드하여 뉴스 데이터에 대해서 레이블링을 진행한다. 

```
python label_news_dataset.py
```

### 6. news data 훈련

sts_news_finetune.py를 실행하여, 4번에 저장한 파인튜닝 파라미터를 로드하여, 추가적인 파인튜닝을 진행한다. 

```
python sts_news_finetune.py
```

### 7. 최종 추천 시스템 작동

recommendation_model.py를 실행하여, 6번에서 저장한 파인튜닝 파라미터를 로드하여, korsts/demo.txt에 저장한 샘플 기사와 추천 목록화되어 있는

korsts/news_db.txt 사이의 문서 유사도를 측정하고 지정한 하이퍼 파라미터 (임계값 및 N rank)에 만큼 추천 기사로 보여준다.

```
python recommendation_model.py --selecte_sample_index $샘플 번호 --similarity_threshold $추천 점수 임계값 --max_rank $최대 노출 순위
```

### 7.1 예시

단, similarity_threshold와 max_rank의 경우 default 값을 각각 3.0, 2으로 설정하여서 별도의 입력 없이도 실행 가능하다.

```
python recommendation_model.py --selecte_sample_index 0 --similarity_threshold 3.0 --max_rank 2
```


### 추가 자료

news_check.py: 간단한 news.json에 대한 데이터 분포 및 이상치 검출

gpt2_tokenizer.py: gpt2의 cls, sep token 임베딩 및 토크 나이징을 위한 모듈 

### windows 관련 이슈

mac Catalina (10.15.7), Ubuntu 16.04, 18.04, Windows 10에서 모두 작동했을 때, 크게 이상이 없으나

아래와 같이 multi cpu processing에서 windows 10의 경우 별도의 설정을 따로 해주어야해서 

'num_workers = 4' 부분을 제거하면 해결됩니다.

![issue1](https://github.com/J-Seo/news_recommendation/blob/main/sample_images/num_workers.png)






