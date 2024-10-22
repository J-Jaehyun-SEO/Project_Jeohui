# Project_Jeohui

이 레포지토리는 연구 “멀리서 읽는 ‘저희’ ― ELECTRA 기반 의미 분류 모델과 N-gram을 활용한 두 가지 ‘저희’의 통시적 변화 양상 연구”에서 사용된 데이터와 코드를 공개하기 위해 제작되었다. 본 연구는 지난 70년간(1954년~2024년) 조선일보와 동아일보에 등장한 두 가지 유형의 ‘저희’(겸양의 저희와 저편을 가리키는 저희)의 사용 추이를 분석하고, 그 변화 양상을 거시적으로 고찰하는 것을 목적으로 한다. 이를 위해 조선일보와 동아일보의 신문 데이터를 바탕으로, 두 유형의 '저희'가 시간에 따라 어떻게 변화했는지를 디지털 방법론(ELECTRA 기반 의미 분류 모델과 N-gram 분석)을 통해 분석하였다.

**논문 링크**  
(추후 게재 시 추가 예정)

### 연구 제목:  
멀리서 읽는 “저희” ― ELECTRA 기반 의미 분류 모델과 N-gram을 활용한 두 가지 ‘저희’의 통시적 변화 양상 연구 

---

## 1. 코드 설명

### 데이터 수집 및 전처리

- ‘저희’가 포함된 문장 총 32,803개를 추출하여 데이터 구성
- 조선·동아일보 100년 아카이브로부터 1954년부터 1999년까지 ‘저희’ 단어가 포함된 총 7,067건(동아일보 3,287건, 조선일보 3,781건)의 기사에서 문장을 추출
- 2000년부터 2024년 5월까지의 빅카인즈 DB에서 조선·동아일보 기사 중 ‘저희’가 포함된 16,195건(동아일보 9,010건, 조선일보 7,185건)의 기사를 추출

#### 추출 과정
문장 추출은 다음 과정을 통해 이루어졌습니다:
1. **1단계**: 문장 분리가 되지 않은 상태의 기사 텍스트를 Kiwi의 문장 분리 기능을 사용해 문장을 분리
2. **2단계**: 마침표와 한국어의 종결어미 등을 기계 학습 모델로 판단해 문장 분리
3. **3단계**: 문장 분리 알고리즘을 통해 기사당 문장 수를 추출

Kiwi 형태소 분석기 알고리즘에 대한 자세한 내용은 다음 논문을 참조:  
이민철, 「Kiwi: 통계적 언어 모델과 Skip-Bigram을 이용한 한국어 형태소 분석기 구현」, 『디지털인문학』 1, 2024, 109-136면.

### ELECTRA 기반 의미 분류 모델

- Pytorch + HuggingFace 사용
- [KoElectra Model](https://monologg.kr/2020/05/02/koelectra-part1/)
- [KoElectra-small(박장원)](https://github.com/monologg/KoELECTRA)

#### 참고 자료
- https://huggingface.co/transformers/training.html
- https://tutorials.pytorch.kr/beginner/data_loading_tutorial.html
- https://tutorials.pytorch.kr/beginner/blitz/cifar10_tutorial.html
- https://wikidocs.net/44249

### N-gram 분석

- Kiwi를 기반으로 단어 분리
- 연대별 및 연도별로 N-gram 결과를 분류하여 제공
- 시각화는 `matplotlib.pyplot` 사용  
  참고: https://matplotlib.org/3.5.3/api/_as_gen/matplotlib.pyplot.html

---

## 2. 기술 통계량

- 연대별 출현에 따른 ‘빈도(비율)’ 기술 통계량 제공

![image](https://github.com/user-attachments/assets/752b1fd8-bf80-4b13-90e5-593cd6aa812f)

---

## 3. 저자
(추후 논문 심사 후 기재 예정)
