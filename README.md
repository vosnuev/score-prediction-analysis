# 성적예측 분석

학생 성적 예측을 위해 `StudentPerformanceFactors` 데이터를 분석한 프로젝트다.
이 저장소는 이전 성적과 여러 학습·환경 요인이 최종 시험 성적(`Exam_Score`)에 어떤 영향을 주는지 확인하는 것을 목표로 한다.

## 프로젝트 목적

- 데이터 구조를 파악하고 주요 변수의 분포를 확인한다.
- `Previous_Scores`와 `Exam_Score`의 관계를 살펴본다.
- 성적에 영향을 주는 핵심 요인을 찾는다.
- 분석 결과를 바탕으로 성적 향상에 필요한 시사점을 정리한다.

## 데이터 정보

- 출처: Kaggle - Student Performance Factors
- 링크: https://www.kaggle.com/datasets/lainguyn123/student-performance-factors/data
- 데이터 크기: 6,607행, 20개 컬럼

## 주요 분석 질문

- 이전 성적이 최종 성적에 얼마나 영향을 주는가?
- 공부 시간과 출석률은 성적과 어떤 관계가 있는가?
- 성적 변화에 가장 큰 영향을 주는 변수는 무엇인가?
- 동기, 가정환경, 학교 환경 같은 변수는 어느 정도 설명력을 가지는가?

## 파일 구성

```text
.
├── analysis.ipynb
├── StudentPerformanceFactors.csv
└── README.md
```

## 분석 흐름

1. 데이터 불러오기 및 기본 구조 확인
2. 결측치, 이상치, 변수 타입 점검
3. 수치형 변수와 범주형 변수의 분포 확인
4. `Previous_Scores`와 `Exam_Score` 관계 분석
5. `Hours_Studied`, `Attendance` 등 핵심 변수와 성적의 상관관계 분석
6. 시각화 결과를 바탕으로 최종 인사이트 정리

## 분석 요약

- `Attendance`와 `Hours_Studied`는 성적을 설명하는 핵심 변수로 나타났다.
- `Previous_Scores`는 참고할 만한 변수지만, 최종 성적을 단독으로 설명하는 힘은 제한적이었다.
- `Motivation_Level` 같은 일부 변수는 최종 성적과의 상관관계가 크지 않았다.
- 성적 향상은 단순한 한 변수보다 학습 습관과 참여도 같은 복합 요인과 더 깊게 연결되어 있다.

## 사용 방법

```bash
git clone https://github.com/vosnuev/-.git
cd -
```

이후 `analysis.ipynb`를 열어 분석을 확인하면 된다.

## 메모

- 이 README는 GitHub 저장소 첫 화면에 표시될 프로젝트 소개용 문서다.
- 분석 결과가 더 정리되면 결론과 시각화 링크를 추가로 보강할 수 있다.
