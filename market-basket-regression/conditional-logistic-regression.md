# Conditional Logistic Regression

## Conditional Logistic Regression \(조건부 로지스틱 회귀\)

* 특정한 조건\(condition\)이 주어진 상황에서 로지스틱 회귀를 시행하는 것
* 특히 설명 변수들의 연관성을 고려해야 하는 경우, 독립 변수가 많은 경우에 사용하는 회귀 분석이다.
* 수리경제학자 맥파든\(McFadden 1973\)에 의해 고안되었으며, 수학적으로 복잡한 모델이다.

### 사례로 이해하기

* 보통 구매자가 상품을 구입할 때, 구매자의 속성과 상품의 속성이 동시에 작용하여 구매 결정이 내려지게 된다. 예를 들어, 아우디 자동차를 사는 사람은 부유층이라는 속성을 갖기만, 구입 대상으로 고려한 여러 개의 다른 차 중에서 아우디가 선택된 이유에는 자동차의 성격이 작용한다. 같은 속성을 갖는 구매자를 모아 놓는다면, 이들이 특정한 차를 구매하는 것은 차의 특성 때문일 것이라고 보는 것이다.
* 즉, 고객의 이전 상품들의 구매 정보를 이용하여 특정한 상품을 구매할 확률을 추정하는 것이다.

### 표기법

* $$U$$ : 고객 집합 \(Users\)
* $$I$$ : 상품 집합 \(Items\)
* $$Yui$$ : 고객 $$u$$가 다음 시점에 상품 $$i $$ 를 구매하면 1, 아니면 0. 
* $$Sui$$ : 고객 $$u$$의 이전 구매 자료로부터의 상품 i에 대한 구매 정보. 여기서 $$u ∈ U, i ∈ I$$ 
  * 구매 정보는 구매 여부\(0 또는 1\), 구매 횟수, 구매 비율 등을 말함.

## 모델 설명

### step 1 : 이전 구매 정보만 이용

* 로지스틱 회귀의 설명 변수로 $$Su$$만 사용하여 $$P(Yui = 1 | Su)$$를 예측

### step 2 : 이전 구매 정보 + 고객 정보를 이용

* step 1에 고객 정보를 추가하면 더 좋은 예측력을 가짐
  * $$Xu$$ : 고객 $$u$$에 대한 입력변수 \(성별, 나이, 소득, 거주 지역 등\)
* 로지스틱 회귀의 설명 변수로 $$Su, Xu$$를 사용하여 $$P(Yui = 1 | Su, Xu)$$를 예측
* 변수들 간의 상호작용\(interaction\)을 고려하기 위해 부스팅 모형을 사용할 수 있다.
* 그러나, 자료가 작은 경우 분산이 커지고, 상품마다 모델을 적합해야 하기 때문에 상품의 개수가 많은 경우 사용하기 어려운 문제점이 있다.

### step 3 : 이전 구매 정보 + 고객 정보 + 상품 정보를 이용

* step 2의 문제를 해결하기 위해 \(고객, 상품\) 쌍에 대해 모형화 하는 방법이 step 3이다.
* 이 때는 상품에 대한 정보도 추가한다.
  * $$Zi$$ : 상품 i에 대한 입력변수 \(제조사, 가격, 장르, 카테고리, 인기도 등\)
* 로지스틱 회귀의 설명 변수로 $$Su, Xu, Zi$$를 사용하여 $$P(Yui = 1 | Su, Xu, Zi)$$를 예측
* 상호 작용을 고려하여  $$Su * Zi$$와 $$Xu * Zi$$항을 추가한다.
* 상품이 더미 변수로 들어가기 때문에, 상품 마다 모델을 적합할 필요가 없다.
* 그래도 설명 변수가 너무 많다면, $$Zi$$의 profile을 보고 서로 비슷한 $$Zi$$끼리는 묶는다.
* step 2와 마찬가지로, 부스팅 모형을 사용하면 예측력을 높일 수 있다.


