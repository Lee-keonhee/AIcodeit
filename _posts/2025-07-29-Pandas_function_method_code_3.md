---
layout: post
title:  "Pandas 핵심 함수와 메서드 code"
date:   2025-07-29 05:00:00 +0900
categories: [머신러닝, 인공지능, 데이터과학]
tags: [Python, Pandas, code]
---

------

## Pandas 자주 사용하는 메서드

------

지난 시간에는 pd.read_csv()와 같이 Pandas의 데이터 구조화 함수들을 다루었다. 이제는 데이터프레임과 시리즈 객체에 직접 적용하는 다양한 핵심 메서드들을 살펴볼 차례입니다. 이 메서드들은 데이터의 효율적인 조작, 변형 및 분석을 위한 필수적인 도구입니다. 본 글을 통해 실제 데이터 처리 과정에서 유용한 Pandas 메서드들을 소개한다.


---

### &nbsp;&nbsp; 3. 데이터 조작 및 변형
- `df.drop(labels, axis)`: 
특정 행(axis=0) 또는 열(axis=1)을 삭제한다. 원본을 변경하려면 inplace=True를 추가한다. 즉, 따로 변수에 저장하지 않아도 업데이트된다.
<br>
- `df.rename(columns={'원래이름': '새이름'})`: 
컬럼 또는 인덱스 이름을 변경한다.
<br>
- `df.replace(to_replace, value)`: 
특정 값을 다른 값으로 대체한다. 단일 값, 리스트, 딕셔너리 등 다양한 형태로 사용 가능하다.
<br>
- `df.set_index(keys, inplace=False)`: 
특정 컬럼(들)을 새로운 인덱스로 설정한다. inplace=True로 원본 변경 가능하다.
<br>
- `df.reset_index(level=None, drop=False, inplace=False)`: 
현재 인덱스를 컬럼으로 변환하고, 새로운 기본(0부터 시작하는) 정수 인덱스를 생성한다. drop=True로 기존 인덱스를 제거할 수 있다.
<br>
- `df.sort_values(by='컬럼명', ascending=True)`: 
특정 컬럼의 값을 기준으로 데이터프레임을 정렬한다. ascending=False로 내림차순 정렬할 수 있다.
<br>
- `df.value_counts()` (Series 메서드): 
Series 내 고유값들의 빈도수를 계산하여 Series로 반환한다.
<br>
- `df.astype(dtype)`:
데이터프레임 전체 또는 특정 Series의 데이터 타입을 변경한다. `df.astype({'컬럼1': int, '컬럼2': float})` 와 같이 적용 가능하다.
<br>
- `df.groupby('기준_컬럼').agg(집계함수)`: 
특정 컬럼을 기준으로 데이터를 그룹화한 후, 각 그룹에 집계 함수(sum, mean, count 등)를 적용한다.
<br>
- `df.mean()`, `df.sum()`, `df.min()`, `df.max()`, `df.std()`, `df.median()`: 
숫자형 컬럼에 대한 평균, 합계, 최솟값, 최댓값, 표준편차, 중앙값 등을 계산한다.
<br>
- `df.pivot_table(values=None, index=None, columns=None, aggfunc='mean')`: 
데이터프레임을 특정 컬럼들을 기준으로 재구성하여 요약 테이블(피벗 테이블)을 생성한다.
<br>
- `series.map(arg)`: 
Series의 각 값에 함수나 딕셔너리를 매핑하여 새로운 Series를 생성한다. Series에만 적용 가능하다.
<br>
- `df.apply(any_fn, axis=0)`:
각 열(axis=0) 또는 행(axis=1)을 **Series 형태로** 함수의 인자로 넘겨 함수를 적용한다. 그 결과로 새로운 DataFrame이나 Series를 반환한다.
<br>
- `Series.apply(any_fn)`:
Series의 각 **개별 요소(값)**에 함수를 적용한다.


오늘은 Pandas `DataFrame`과 `Series`의 가장 기본적인 정보들을 한눈에 파악할 수 있는 메서드들을 살펴보았습니다. `.head()`, `.info()`, `.shape`처럼 단순해 보이는 기능들이지만, 데이터를 처음 마주했을 때 전체적인 그림을 그리는 데 필수적인 도구입니다. 이 외에도 `.columns`, `.index`, `.dtypes` 같은 속성들은 데이터의 구조를 이해하는 데 큰 도움이 될 것입니다.


더 많은 Pandas 함수와 메서드를 탐구하고 싶으시면, 아래 링크를 통해 확인할 수 있습니다.

*   [** Pandas 핵심 메서드: 데이터 선택 및 필터링 (Chapter 2)**](2025-07-21-Pandas_function_method_2.md)
*   [** Pandas 핵심 메서드: 결측치, 중복치 처리 (Chapter 2)**](2025-07-21-Pandas_function_method_4.md)
