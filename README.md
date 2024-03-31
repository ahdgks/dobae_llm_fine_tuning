# dobae_llm_fine_tuning

도배 하자 질의 응답 처리 : 한솔데코 시즌2 AI 경진대회

[![대회정보](https://github.com/ahdgks/dobae_llm_fine_tuning/assets/113077320/948bd6f6-fbb1-4a69-8235-1b1e54a1c105)](https://dacon.io/competitions/official/236216/overview/description)

## Private 순위

![순위](https://github.com/ahdgks/dobae_llm_fine_tuning/assets/113077320/649f2a19-73d3-4ae7-97fb-0695355f1ad5)

---
## Data  
![train_data](https://github.com/ahdgks/dobae_llm_fine_tuning/assets/113077320/2ae8e3cb-cbfb-4d5a-b0bd-7d18423e4878)

### train.csv
    id : 질문 - 답변 (QA) 샘플 고유 번호  
    질문_1, 질문_2 : 샘플 별 동일한 내용으로 구성된 질문 2개  
    category : 질문 - 답변 (QA) 샘플의 도메인 세부 분야  
    답변_1, 답변_2, 답변_3, 답변_4, 답변_5 : 샘플 별 질문에 대한 동일한 답변 Reference 5개  

### test.csv
    id : 평가 질문 샘플 고유 번호
    질문 : 평가 샘플의 질의 내용

### sample_submission.csv 
    id : 평가 질문 샘플 고유 번호  
    vec_0, vec_1 ... vec_511 : 생성된 답변을 512 차원의 Embedding Vector로 표현된 결과  

## 평가 산식
    평가 산식 : Cosine Similarity (코사인 유사도)
    Public score : 전체 테스트 데이터 중 사전 샘플링된 40%
    Private score : 전체 테스트 데이터 100%

## 추가 데이터

### train data 활용
![추가_질문](https://github.com/ahdgks/dobae_llm_fine_tuning/assets/113077320/c3bf1b29-6a84-45e1-b3da-6b7809310189)

    한솔데코에서 제공한 train data를 활용하여, 명사를 추출
    각 명사들을 건축구조, 마감재, 하자, 시공, 인테리어 등의 카테고리로 분류
    각 카테고리별로 질문 유형을 만들고 데카르트 곱을 이용해 명사와 질문 유형으로 추가 질문 생성
    생성된 질문들 중 기존 train data에 포함된 질문과 유사한 것들을 코사인 유사도 분석을 통해 식별
    코사인 유사도가 0.85 이하인 질문들만을 이용해 질문 목록 구성

