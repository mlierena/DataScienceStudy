# 연관성 분석 (Association Rules Analysis)

## 연관규칙의 정의와 적용사례

### Market Basket Analysis 

* 주어진 `트랜잭션 집합` 으로부터, `<어떤 아이템(들)이 나타날지를 다른 아이템(들)의 발생으로부터 예측하는 규칙>`을 찾는 작업이다.

- 장바구니에 담겨있는 상품을 분석하는 것과 비슷해서 장바구니 분석이라고도 한다.

- 슈퍼마켓에서 바코드로 스캔된 데이터를 트랜잭션 데이터로 사용하여 관리자는 어떤 그룹의 아이템들이 함께 구매가 되었는지 알아내고 이를 상품진열 등에 이용하기도 하며 카탈로그 디자인이나 구매패턴을 분석하여 고객을 세분화함.

#### Market-Basket transactions

| TID | Items 
| :--- | :---
| 1 | A, B1, C, D, B2
| 2 | E, F, G
| 3 | B1, B2
| 4 | E, F, A |

#### Example

> 예를들어, 슈퍼마켓 데이터베이스에 10,000건의 거래기록이 있다고 가정하고, 그 중에 200건이 상품A와 B를 포함하며, 이중 상품C를 80건 포함하고 있다면, 연관규칙은?
>> "만약 A와 B를 동시에 구매했다면 C도 동시에 구매한다"라는 연관규칙은 0.8% (80/10,000)의 지지도와 40% (80/200)의 신뢰도를 가진다."

>
>

### 의료 진단

- 연관규칙을 적용하면 환자를 진단할 때, `객관적`으로 진단 할 수 있음.
- 증상에 대한 의료기록을 바탕으로 연관규칙을 적용 새로운 데이터 셋을 추가.

> Serban has proposed a technique based on relational association rules and supervised lerning method. It helps to identify the probability of illness in a certain disease. This interface can be simply extended by adding new symptoms type for the `given` disease, and by defining new relations `between` these symptoms.

---
</br></br></br>


# 연관규칙이란?
</br></br></br>

---

| TID | Items 
| :--- | :---
| 1 | Bread, Milk
| 2 | Bread, Diaper, Beer, Eggs
| 3 | Milk, Diaper, Beer, Coke
| 4 | Bread, Milk, Diaper, Beer
| 4 | Bread, Milk, Diaper, Coke |

</br></br></br>


---

## 항목집합: Item Set

#### 한 개 이상의 항목들의 집합 - {Milk, Bread, Diaper}
* k-항목집합 (k-Item Set) - k개의 항목을 가지는 집합
</br></br></br>

---

## 지지도 카운트 (Support Count): **n**

#### 항목집합이 (트랜잭션 DB)에 나타나는 횟수

###### n{Eggs} = 1,
###### n{Milk, Bread, Diaper} = 2
</br></br></br>

---

## 연관규칙이란? Association Rules

#### X와 Y가 항목집합이라 할 때, X -> Y 형태로 나타나는 함축 표현 (implication expression)
</br></br></br>

---

## 연관규칙의 평가척도인 지지도와 신뢰도

#### 지지도 (Support)
* X와 Y를 함께 포함하는 트랜잭션의 비율
* 규칙이 얼마나 중요한가 혹은 유용한가 낮은 지지도의 규칙은 우연성에 기인할 수 있음

</br></br></br>

#### 신뢰도 (Confidence)
* X를 포함한 트랜잭션 중에 Y가 나타나는 비율
* 규칙이 얼마나 믿을 만 한가? 가정과 결론이 얼마나 관련이 있는지를 나타냄

</br></br></br>

--- 

## 임계치 (minsup)

* Item Set의 Transaction의 임계값을 설정
- 임계치 (minsup) 설정 임계치는 0과 1사이의 값으로 설정한다.

</br></br></br>

---

## 연관규칙 마이닝 (Association Rules Mining, ARM)

#### 연관규칙 마이닝 
* 트랜잭션 집합이 있을 때 다음 조건을 만족하는 모든 규칙을 찾는 것

>  support >= minsup 
>> (support = 지지도, minsup = 주어진 최소지지도)
>
>

>  confidence >= minconf
>> (confidence = 신뢰도, minconf = 주어진 최소신뢰도)
>
>

#### Brute-force approach

* 가능한 모든 연관규칙을 제시
* 각 규칙의 지지도와 신뢰도 계산
* 임계치를 만족하지 못하는 규칙을 제거
- 트랜잭션 수가 많아지면 엄청나게 계산이 복잡해짐







---
</br></br></br>




# Example

---

| TID | Items 
| :--- | :---
| 1 | Bread, Milk
| 2 | Bread, Diaper, Beer, Eggs
| 3 | Milk, Diaper, Beer, Coke
| 4 | Bread, Milk, Diaper, Beer
| 4 | Bread, Milk, Diaper, Coke |

</br></br></br>

---

## Example of Rules

```R

{Milk, Diaper} -> {Beer} (s=0.4, c=0.67)
{Milk, Beer} -> {Diaper} (s=0.4, c=1.0)
{Diaper, Beer} -> {Milk} (s=0.4, c=0.67)
{Beer} -> {Milk, Diaper} (s=0.4, c=0.67)
{Diaper} -> {Milk, Beer} (s=0.4, c=0.5)
{Milk} -> {Diaper, Beer} (s=0.4, c=0.5)
```

</br></br>

---

### Observations

* 모든 규칙은 `{Milk, Diaper, Beer}` 의 동일한 항목집합에서 비롯됨
* 동일한 항목집합에서 나온 규칙들은 지지도는 동일하나 신뢰도는 다를 수 있음
* 지지도와 신뢰도를 분리하여 규칙을 마이닝할 필요가 있음

</br></br>

---


## 빈발항목 후보선정 (Candidate frequent item set)

#### Brute-force approach

* 모든 항목집합이 후보가 됨
* 트랜잭션 데이터를 스캔하면서 각 후보에 대한 지지도를 카운트함
* 카운트를 위해 모든 후보에 대해 트랜잭션을 매치함
* 결국 복잡도는 2^n 이 됨


</br></br>

---

## 후보개수 줄이기

#### Apriori 알고리즘

* 어떤 항목이 빈발한다면 그 항목의 부분집합도 빈발함
* `{Milk, Bread, Diaper}` 가 빈발 항목집합이면, 이의 부분집합인 `{Milk, Bread}`, `{Bread, Diaper}` 등도 빈발 항목집합임

</br></br>

---

## 연관분석의 장점

* 결과가 명확함
* 대용량 자료의 분석의 시작으로 적합
* 계산이 용이하고 변구 개수가 많은 경우 쉽게 사용

</br>

## 연관분석의 단점

* Item 수에 따라 계산량이 급등
* 연속형 변수 사용 불가
* Transaction이 적은 Item은 분석이 안됨









