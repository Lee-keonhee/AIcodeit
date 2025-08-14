---
layout: post
title:  "결정 트리(Decision tree)와 랜덤 포레스트 코드 구현"
date:   2025-07-22 09:00:00 +0900
categories: [머신러닝, 인공지능, 데이터과학]
tags: [머신러닝기초]
---

## 결정 트리(Decision Tree)

```python
from sklearn.tree import DecisionTreeClassifier
tree = DecisionTreeClassifier(max_depth='트리 깊이 제한(int)',
                              min_samples_split='노드를 분할하는데 필요한 최소 샘플수(int)',
                              min_samples_leaf='리프노드의 최소 샘플 수(int)')
```

---

## 랜덤 포레스트(random forest)


```python
from sklearn.ensemble import RandomForestClassifier, RandomForestRegressor
tree = RandomForestClassifier(n_estimators='생성할 트리의 수(int)',
                              min_samples_split='노드를 분할하는데 필요한 최소 샘플수(int)',
                              min_samples_leaf='리프노드의 최소 샘플 수(int)',
                              max_depth='트리 깊이 제한(int)',
                              criterion='평가방법(gini, entropy)',
                              n_jobs=-1,
                              )
```

---
## 스태킹(Stacking)
```python
from sklearn.ensemble import StackingClassifier, RandomForestClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.datasets import make_classification
from sklearn.model_selection import train_test_split

X, y = make_classification(n_samples=1000, random_state=42, n_classes=2) # 클래스 2개, 샘플 1000개
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=42)

estimators = [
    ('rf', RandomForestClassifier(n_estimators=100, random_state=42)),
    ('log_reg', LogisticRegression(solver='liblinear', random_state=42)) # 다른 모델 추가 가능
]

stk_clf = StackingClassifier(
    estimators=estimators,
    final_estimator=LogisticRegression(solver='liblinear', random_state=42), # 메타 모델
    cv=5 # 교차 검증 폴드 수
)

stk_clf.fit(X_train, y_train)
accuracy = stk_clf.score(X_test, y_test)
print(f"스태킹 모델의 정확도: {accuracy:.4f}")
```