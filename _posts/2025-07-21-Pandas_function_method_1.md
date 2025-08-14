---
layout: post
title:  "Pandas 핵심 함수와 메서드 정리-1"
date:   2025-07-21 09:00:00 +0900
categories: [머신러닝, 인공지능, 데이터과학]
tags: [Python, Pandas]
---

------

## Pandas 자주 사용하는 함수

------

&nbsp;최근 정보의 저장과 인터넷의 발달로 인해 매우 많은 데이터가 발생하고 있습니다. 하지만 이러한 방대한 데이터를 의미있는 정보로 가공하고 분석하는 능력이 현대사회의 필수적인 능력으로 자리잡고 있습니다.

&nbsp;파이썬은 이러한 데이터 분석 및 처리 작업에 있어 가장 강력하고 폭넓게 활용되는 프로그래밍 언어 중 하나이며, 많은 사람들이 데이터 조작과 분석을 위한 핵심 라이브러리인 **Pandas(판다스)**를 사용하고 있습니다.

&nbsp;많은 사람들이 Pandas를 사용함에도 불구하고, 새로 데이터에 대해 공부하는 사람들은 Pandas가 제공하는 기능이 워낙 다양하기 때문에, 어떤 기능을 익히고 활용해야하는지 파악하기 어렵습니다.

&nbsp;오늘은 Pandas 라이브러리의 방대한 기능 중 실제 데이터 분석 및 전처리 과정에서 가장 빈번하게 활용되는 핵심 함수들을 엄선하여 소개하고자 합니다.


&nbsp;Pandas를 사용하기 위해서 pandas 라이브러리를 불러와야 한다.
```python
import pandas as pd
```

------

## Pandas 모듈 함수
---
#### &nbsp;&nbsp;&nbsp;&nbsp; 1. ***pd.read_csv(경로), pd.read_excel(경로)***
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;csv 및 excel 파일을 읽어서 Dataframe 형식으로 변환
```python
df = pd.read_csv(
    '파일경로',
    sep=';',                        # 구분자가 세미콜론
    encoding='utf-8',               # 한글 깨짐 방지
    header=0,                       # 첫 행이 열 이름
    index_col="id",                 # 'id' 열을 인덱스로
    usecols=["id", "name", "date"], # 사용할 컬럼만 따로 dataframe 생성
    parse_dates=["date"],           # 날짜 형식으f로 파싱 - 날짜 형식을 추론해서 자동 변경
    na_values=["-", "없음"]          # 결측값 처리
)  
```

------
------

#### &nbsp;&nbsp;&nbsp;&nbsp;2. ***pd.DataFrame({'컬럼1': [값1, 값2]]})***
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;직접 데이터를 넣어서 새로운 DataFrame을 생성

- 리스트를 이용하여 데이터프레임 생성

```python
df_from_list = pd.DataFrame([[1,2],[3,4]],columns=['A','B'], index=['row1', 'row2'])
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;생성된 데이터프레임

|      | A | B |
|------|---|---|
| row1 | 1 | 2 |
| row2 | 3 | 4 |

------
- 딕셔너리를 이용한 데이터프레임 생성

```python
df_from_dict = pd.DataFrame({'이름':['홍길동', '이순신'], '나이':[25,30]})
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;생성된 데이터프레임

|   | 이름  | 나이 |
|---|-----|----|
| 0 | 홍길동 | 25 |
| 1 | 이순신 | 30 |

------

- numpy 배열을 이용한 데이터프레임 생성

```python
import pandas as pd
import numpy as np
# 라이브러리 불러오기
arr = np.array([[1, 2], [3, 4]])
df_from_numpy = pd.DataFrame(arr,columns=['A','B'])
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;생성된 데이터프레임

|   | A | B |
|---|---|---|
| 0 | 1 | 2 |
| 1 | 3 | 4 |

------
------

#### &nbsp;&nbsp;&nbsp;&nbsp;3. pd.concat([df1, df2, df3])
&nbsp;&nbsp;&nbsp;&nbsp;여러 개의 DataFrame을 행이나 열을 기준으로 이어붙임

- 행 방향으로 합치기

```python
df1 = pd.DataFrame({'A': [1,2], 'B': [3,4]})
df2 = pd.DataFrame({'A': [5,6], 'B': [7,8]})
df_concat = pd.concat([df1, df2], axis=0, ignore_index=True)
# axis=0 이면 행 방향 합치기
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;생성된 데이터프레임

|   | A  |  B|
|---|----|---|
| 0 | 1  |  3|
| 1 | 2  | 4|
| 2 | 5  | 7|
| 3 | 6  | 8|

------

- 열 방향으로 합치기

```python
df3 = pd.DataFrame({'C': ['x', 'y', 'z']})
df_concat_col = pd.concat([df1, df3], axis=1)
# axis=1이면 열방향으로 합치기
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;생성된 데이터프레임

|  | A    | B | C|
|---|------|---|---|
|0 | 1    | 3 | x|
|1 | 2    | 4 | y|
|2 | NaN  | NaN | z |

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;이처럼 추가되는 값이 더 많을 경우, 데이터가 없는 부분은 자동으로 NaN으로 채워진다.

------
------

#### &nbsp;&nbsp;&nbsp;&nbsp;4. pd.merge(df1, df2, on='컬럼명')
&nbsp;&nbsp;&nbsp;&nbsp; 두 DataFrame을 특정 '키'를 기준으로 병합

```python
df1 = pd.DataFrame({
    'id': [1, 2, 3],
    'name': ['Alice', 'Bob', 'Charlie']
})
df2 = pd.DataFrame({
    'id': [2, 3, 4],
    'age': [25, 30, 35]
})
# inner join (교집합)
inner = pd.merge(df1, df2, on='id', how='inner')
# left join (왼쪽 기준)
left = pd.merge(df1, df2, on='id', how='left')
# right join (오른쪽 기준)
right = pd.merge(df1, df2, on='id', how='right')
# outer join (합집합)
outer = pd.merge(df1, df2, on='id', how='outer')
```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;생성된 데이터프레임


| **Inner Join** |   |   | **Left Join** |   |   |
|:--------------:|---|---|:-------------:|---|---|
| id | name   | age | id | name   | age |
|----|--------|-----|----|--------|-----|
| 2  | Bob    | 25  | 1  | Alice  | NaN |
| 3  | Charlie| 30  | 2  | Bob    | 25  |
|    |        |     | 3  | Charlie| 30  |



| **Right Join** |   |   | **Outer Join** |   |   |
|:--------------:|---|---|:--------------:|---|---|
|       id       | name   | age | id | name   | age |
|----------------|--------|-----|----|--------|-----|
|       2        | Bob    | 25  | 1  | Alice  | NaN |
|       3        | Charlie| 30  | 2  | Bob    | 25  |
|       4        | NaN    | 35  | 3  | Charlie| 30  |
|                |                |     | 4  | NaN    | 35  |

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;***Inner Join*** : id를 기준으로 두 Dataframe에 모두 공통으로 존재하는 데이터를 병합
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;***Left Join*** : 두 Dataframe 중 왼쪽(첫번째 Dataframe)의 id를 기준으로 병합
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;***Right Join*** : 두 Dataframe 중 오른쪽(두번째 Dataframe)의 id를 기준으로 병합
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;***Outer Join*** : 두 Dataframe에 존재하는 모든 id를 기준으로 병합.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;병합시 데이터가 없는 부분은 NaN으로 자동으로 채워진다.

------
------

#### &nbsp;&nbsp;&nbsp;&nbsp;5. pd.get_dummies(df['컬럼명'])
&nbsp;&nbsp;&nbsp;&nbsp; 범주형 데이터를 원-핫 인코딩(One-Hot Encoding)방식으로 숫자로 변경.

```python
data = {
    '도시': ['서울', '부산', '서울', '제주'],
    '날씨': ['맑음', '흐림', '맑음', '비']
}
df = pd.DataFrame(data)
df_encoded = pd.get_dummies(df, dtype=int) # 0/1로 깔끔하게!
df_encoded
```


|Input Data|      |      |
|----|------|------|
|   | 도시   | 날씨   |
|---| ---  | ---  |
|0  | 서울   | 맑음   |
|1  | 부산   | 흐림   |
|2  | 서울   | 맑음   |
|3  | 제주   | 비    |

| Output Data  |         |                  |           |           |           |         |
|--------------|---------|------------------|-----------|-----------|-----------|---------|
|              | 도시_부산| 도시_서울         | 도시_제주   | 날씨_맑음  | 날씨_비    | 날씨_흐림|
| ------------ | --------| ---------------- | --------- | -------   | --------- | ------- |
| 0            | 0       | 1                | 0         | 1         | 0         | 0       |
| 1            | 1       | 0                | 0         | 0         | 0         | 1       |
| 2            | 0       | 1                | 0         | 1         | 0         | 0       |
| 3            | 0       | 0                | 1         | 0         | 1         | 0       |

------
----

&nbsp;오늘은 Pandas 라이브러리 중에서 실제 데이터 분석과 전처리 과정에서 가장 빈번하게 활용되는 DataFrame 객체의 핵심 메서드들을 엄선하여 소개하였습니다.
다음 시간에는 이러한 메서드들을 보다 심도 있게 다루고, 실무에서 효과적으로 활용하는 방법을 자세히 살펴보겠습니다.