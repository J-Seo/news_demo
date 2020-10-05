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

### 5. 


