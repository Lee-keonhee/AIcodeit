---
layout: post
title:  "Pandas 핵심 함수와 메서드 정리-2"
date:   2025-07-28 09:00:00 +0900
categories: [머신러닝, 인공지능, 데이터과학]
tags: [Python, Pandas]
---

------

## Pandas 자주 사용하는 메서드

------

지난 시간에는 pd.read_csv()와 같이 Pandas의 데이터 구조화 함수들을 다루었다. 이제는 데이터프레임과 시리즈 객체에 직접 적용하는 다양한 핵심 메서드들을 살펴볼 차례입니다. 이 메서드들은 데이터의 효율적인 조작, 변형 및 분석을 위한 필수적인 도구입니다. 본 글을 통해 실제 데이터 처리 과정에서 유용한 Pandas 메서드들을 소개한다.


---
### &nbsp;&nbsp; 1. 데이터 프레임 기본 정보확인
- `df.head(n=5)`:
데이터프레임의 상위 n개 행을 확인한다. 기본값은 5개이다.
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

### &nbsp;&nbsp; 2. 데이터 선택 및 필터링
- `df['컬럼명']` / `df[['컬럼1', '컬럼2']]`: 
해당 컬럼(들)을 선택한다. 1개일 경우, Series, 2개 이상일 경우, 데이터프레임으로 반환한다. 이때 하나의 컬럼명을 리스트 df[['컬럼명']] 형태로 선택하면 1개 컬럼이더라도 데이터프레임으로 반환된다.
<br>
- `df.loc[행인덱스, 열인덱스]`: 
라벨(이름) 기반으로 데이터를 선택한다.
<br>
- `df.iloc[행위치, 열위치]`: 
정수 위치 기반으로 데이터를 선택한다.
<br>
- `df[조건]`: 
불리언 인덱싱으로 특정 조건에 맞는 행을 필터링한다. df[조건]형식으로 조건에 맞는 데이터 추려냄. 여러 조건일경우 df[(조건1)&(조건2)] 이런 방식으로 사용한다.

------

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

*   [** Pandas 핵심 함수와 메서드 정리-1**]({{site.baseurl}}/2025/07/Pandas_function_method_1/)
*   [** Pandas 핵심 메서드: 데이터프레임 기본 정보확인 코드 예제**]({{site.baseurl}}/2025/07/Pandas_function_method_code_1/)
*   [** Pandas 핵심 메서드: 데이터 선택 및 필터링 코드 예제**]({{site.baseurl}}/2025/07/Pandas_function_method_code_2/)
*   [** Pandas 핵심 메서드: 데이터 조작 및 변형 코드 예제**]({{site.baseurl}}/2025/07/Pandas_function_method_code_3/)
*   [** Pandas 핵심 메서드: 결측치, 중복치 처리 예제**]({{site.baseurl}}/2025/07/Pandas_function_method_code_4/)
