# Kaggle_Santander-Product-Recommendation

https://www.kaggle.com/c/santander-product-recommendation

Ready to make a downpayment on your first house? Or looking to leverage the equity in the home you have? To support needs for a range of financial decisions, Santander Bank offers a lending hand to their customers through personalized product recommendations.

![santander-banner-ts-660x](https://user-images.githubusercontent.com/49096513/89110008-444d2e80-d481-11ea-9c99-18331bad4c6c.png)

### EDA(Exploratory Data Analysis)
* fecha_dato: 2015-01-28 ~ 2015-06-28의 첫 6개월은 고객 데이터 개수가 같고 그 이후에 증가함
* indrel_1mes: 월초 기준 고객 등급을 의미하는 변수는 수치형(1,2,3,4)와 범주형(P)값이 섞여 있는 변수임. 그러나 막대그래프에서는 (1.0, 1)이 서로 다른 값인 것 처럼 표기가 되는 이것은 데이터 타입이 object이기 때문임. 전처리에서 모두 1로 통일할 것
* age, antiguedad: 수치형 변수인 나이 분포가 중간에 뚝 끊긴 양상을 보이는데 이는 object형태로 저장된 indrel_1mes변수와 같은 문제임
* fecha_alta: 1995년부터 2016년까지 폭 넓은 값을 가지는 날짜 데이터임. 1995년과 2016년의 빈도가 높은 것을 통해 장기고객과 신규고객의 비율이 높아보임
* ind_nuevo: 이진 변수(0,1)로 표기되는 방식이고 신규 고객 지표이다(6개월 이내 = 1). 대부분이 0이고 1은 가끔 존재
* indrel: 고객 등급 지표인데, 99는 해당달에 1등급이 해제되는 등급의 고객이다. 대부분은 1이고 소수가 99인 변수이다. -> 정수로 변환할 필요가 있음
* ult_fec_cli_it: 1등급 고객의 마지막 날짜이다. object형 변수이고 2015.07 ~ 2016.05
* tiprel_1mes: 월초 기준 고객 관계 유형 A: active I: inactive, P: former customer, R: potential 이고 object형 변수이고 A, I의 빈도가 높다
* indresi: 거주지표 은행이 위치한 국가와 동일한가 아닌가 s: yes n: no 이고 object 변수형 S의 빈도가 높음
* indext: 외국인 지표로 태어난 국가와 은행이 위치한 국가가 같으면 S 다르면 N 이고 object 데이터 타입이다.
* conyuemp: 배우자가 은행 직원이면 1 아니면 N 이고 N의 빈도가 높은 object 데이터 타입이다.
* canal_entrada: 고객 유입 채널이고 object 데이터 타입인데 알파벳 세글자로 암호화된 유입경로 변수이다.
* indfall: 고객의 사망여부로 S는 사망한 경우 N은 사망하지 않은 경우이다.
* tipodom: 주소 유형으로 모든 값이 1인데 변수로 무의미함.
* nomprov: 지방 이름이고 데이터 타입은 object로 스페인 지역이름을 나타낸다 cod_prov와 동일한 것으로 추측됨
* ind_actividad_cliente: 활성화 지표로 1은 active customer, 2는 inactive customer이다.
* renta: 가구 총 수입으로 float64인데 정수로 변환할 필요가 있다.
* segmento: 분류 01:VIP 02: 개인 03: 대졸 개인이 가장 높으나 대학생의 비율이 높은 것으로 미루어보아 대학가 주변으로 추정된다.

* 당좌예금(ind_cco_fin_ult1)은 8월에 가장 높은 값을 가지고 겨울에는 축소된다
* 단기예금(ind_deco_fin_ult1)은 2015-06-28에 높은 값을 가지고 다른 때는 매우 낮다
* 급여, 연금(ind_nomina_ult1, ind_nom_pens_ult1)은 당좌예금과 반대로 8월에 가장 낮고 겨울에 높은 값을 가진다.
* 신규 구매 빈도가 가장 높은 5개는 당좌예금 (ind_cco_fin_ult1), 신용카드(ind_tjcr_fin_ult1), 급여(ind_nomina_ult1), 연금(ind_nom_pens_ult1), 직불카드(ind_recibe_fin_ult1)
