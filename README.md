# GPT2를 활용한 뉴스 기사 추천 시스템 &#128568;

- 2020.10.03 (1차 업데이트)
- 2002.11.10 (2차 업데이트)

### 간략한 소개👈&#128573;

GPT2 언어 모델을 활용해서 제목 및 본문을 바탕으로 

현재 열람하고 있는 기사와 유사한 문맥과 어휘를 지니고 있는 뉴스 기사를 추천하는 시스템입니다.

유사도 점수는 0점에서 5점까지 설정되어 있으며, 기본 값은 3점으로 설정했습니다. 

(&#10069; 수 차례 실험으로 3점을 설정했습니다!)

**새로운 뉴스 기사**를 추가하려는 경우 demo.txt 파일에 id, title, content를 형식에 맞게 다음 행에 추가하면 됩니다.

**추천 뉴스기사 목록**을 추가하려는 경우 news_db.txt 파일에 제목+본문을 형식에 맞게 다음 행에 추가하면 됩니다.

Created by: 서재형(Jaehyung Seo), NLP & AI Lab (고려대학교)

email: wolhalang@gmail.com

### 코드 실행 예시

![sample](https://github.com/J-Seo/news_recommendation/blob/main/sample_images/sample_image.png)
