# 분류 예측 평가 방법

## Cross-Entropy Loss

* 크로스 엔트로피란 이분류 문제에서 $$y$$와 $$ŷ$$의 차이\(거리\)를 측정하는 척도다.
* 크로스 엔트로피가 작을수록 예측력이 좋은된 것이다. 

### 이해를 돕기 위한 설명

* 우도의 곱이 최대인 모델\(예측 모델\)을 찾는 것은 로그우도의 기대값이 최대인 모델을 찾는 것과 같다. 그리고 로그우도의 기대값이 최대인 모델을 찾는 것은, 학습데이터의 분포\(distribution\)와 모델이 예측한 결과의 분포 사이의 차이, 즉 크로스 엔트로피를 최소화하는 것과 같다. 다시 말해, 크로스 엔트로피는 파라메터 θ하에서의 음의 로그우도의 기대값이라고 해석할 수 있다.

##  Precision & Recall

* Precision : 추천한 모든 상품들 중에서 실제 평가가 좋은 상품의 비율
* 즉, 내가 추천한 것 중에서 hit한 것의 비율
* $$Precision = tp/tp+fp = || / |my recommendation  s  |$$ 
* Recall : 실제 평가가 좋은 상품들 중에서 추천된 상품의 비율
* 즉, 전체 true인 것 중에 내가 추천한 것의 비율
* $$Recall = tp/tp+fn$$ 
* Precision과 Recall은 서로 trade-off 관계

## F1 score

* F1 score는 Precision과 Recall의 조화평
* $$F1=2⋅precision⋅recall/ (precision+recall)$$ 

## ROC curve & AUC

* ROC curve는 클래스 판별 기준값의 변화에 따른 1-Precision과 Recall의 변화를 시각화한 것이다. 
* Recall이 크고 1-Precision이 작은 모형이 좋은 모형이며, 그래프에서는 곡선이 왼쪽 위 모서리에 가까울수록 모델 성능이 좋다고 본다.
* AUC는 ROC curve 아래의 면적을 말한다. 
* 1-Precision 대비 Recall 값이 클수록 AUC가 1에 가까운 값이며, 넓이가 클수록 좋은 성능의 모델이다.

