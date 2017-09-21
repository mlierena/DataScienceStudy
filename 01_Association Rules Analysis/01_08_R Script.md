# 연관 규칙을 사용한 장바구니 분석

## 예제: 연관 규칙과 자주 구매하는 식료품 식별

* 1단계: 데이터 수집
* 2단계 : 데이터 준비와 탐구

### 데이터 준비: 거래 데이터를 위한 희소 매트릭스 생성
* 거래 데이터 

```R
groceries <- read.transactions("groceries.csv", sep=",")
```