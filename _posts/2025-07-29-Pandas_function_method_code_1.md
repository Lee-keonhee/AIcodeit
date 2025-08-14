---
layout: post
title:  "Pandas 핵심 함수와 메서드 code"
date:   2025-07-29 05:00:00 +0900
categories: [머신러닝, 인공지능, 데이터과학]
tags: [Python, Pandas, code]
---

------

### &nbsp;&nbsp; 1. 데이터 프레임 기본 정보확인
- `df.head(n=5)`:
```python

```
<br>
- `df.tail(n=5)`: 
데이터프레임의 하위 n개 행을 확인한다. 기본값은 5개이다.
<br>
- `df.info()`: 
데이터프레임의 컬럼별 정보 (데이터 타입, 결측치 여부, 메모리 사용량)를 요약해서 보여준다.
<br>
- `df.shape`: 
데이터프레임의 행과 열 개수를 **튜플** 형태로 반환한다.
<br>
- `df.columns`:
데이터프레임의 모든 컬럼 이름들을 반환한다.필요에 따라 '.tolist()'나 '.to_numpy'를 붙여 리스트나 numpy.array로 변환하는 경우가 많다.
<br>
- `df.index`: 
데이터프레임의 인덱스 정보를 반환한다.
<br>
- `df.dtypes`:
각 컬럼의 데이터 타입을 Series 형태로 반환한다.
<br>
- `df.describe()`: 
값의 개수(결측치 제외), 평균, 표준편차, 최소값, 1사분위수, 중앙값, 3사분위수, max값 반환한다.
<br>
- `df.sample(n=5)`:
무작위 샘플 n개 추출한다. 데이터프레임 형태로 반환한다.
<br>
- `df.nunique()`:
각 컬럼의 고유값 개수를 추출한다. Series형태로 반환한다.
<br>
- `Series.nunique()`:
해당 Series의 고유값 개수를 추출한다. int 형태로 반환한다.
<br>
- `Series.unique()`: 
해당 Series의 고유값을 추출한다. numpy.array형태로 반환한다. 
<br>
- `df.mode()` / `series.mode()`: 
데이터프레임의 각 컬럼 또는 Series에서 **최빈값(가장 자주 나타나는 값)**을 반환한다. 최빈값이 여러 개일 경우 모두 반환한다.

------

오늘은 Pandas `DataFrame`과 `Series`의 가장 기본적인 정보들을 한눈에 파악할 수 있는 메서드들을 살펴보았습니다. `.head()`, `.info()`, `.shape`처럼 단순해 보이는 기능들이지만, 데이터를 처음 마주했을 때 전체적인 그림을 그리는 데 필수적인 도구입니다. 이 외에도 `.columns`, `.index`, `.dtypes` 같은 속성들은 데이터의 구조를 이해하는 데 큰 도움이 될 것입니다.


더 많은 Pandas 함수와 메서드를 탐구하고 싶으시면, 아래 링크를 통해 확인할 수 있습니다.

*   [** Pandas 핵심 메서드: 데이터 선택 및 필터링 (Chapter 2)**](2025-07-21-Pandas_function_method_2.md)
*   [** Pandas 핵심 함수와 메서드 정리-1**](링크_투_Chapter1_모듈함수_포스트)