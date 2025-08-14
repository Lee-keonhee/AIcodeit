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

----

### &nbsp;&nbsp; 4. 결측치, 중복치 처리
- `df.isnull()` / `df.isna()`: 
데이터프레임의 결측치를 True로 반환한다. '.sum()'를 활용하여 결측치 개수 확인할 수 있다.
<br>
- `df.fillna(value)`: 
결측치를 특정 value로 채운다.
<br>
- `df.dropna(axis)`: 
결측치가 있는 행(axis=0) 또는 열(axis=1)을 제거한다.
- `df.duplicated(subset=None, keep='first')`: 
중복된 행을 True/False로 표시한다. subset으로 특정 컬럼만 지정하여 중복을 검사할 수 있으며, keep으로 'first' (첫 번째만), 'last' (마지막만), 'False' (모두)를 표시할 수 있다.
<br>
- `df.drop_duplicates(subset=None, keep='first', inplace=False)`:
중복된 행을 삭제한다.

----

오늘은 Pandas `DataFrame`과 `Series`의 가장 기본적인 정보들을 한눈에 파악할 수 있는 메서드들을 살펴보았습니다. `.head()`, `.info()`, `.shape`처럼 단순해 보이는 기능들이지만, 데이터를 처음 마주했을 때 전체적인 그림을 그리는 데 필수적인 도구입니다. 이 외에도 `.columns`, `.index`, `.dtypes` 같은 속성들은 데이터의 구조를 이해하는 데 큰 도움이 될 것입니다.


더 많은 Pandas 함수와 메서드를 탐구하고 싶으시면, 아래 링크를 통해 확인할 수 있습니다.

*   [** Pandas 핵심 메서드: 데이터 조작 및 변형 (Chapter 2)**](2025-07-21-Pandas_function_method_3.md)
