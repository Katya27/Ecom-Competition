# Ecom-Competition
**Задача**

Необходимо разработка модели, которая понимает привычки и нужды пользователя, и сможет предсказать, что пользователь захочет заказать в следующий раз.

Такая модель, будучи разработанной, может принести значительную ценность для клиента - сэкономить время при сборке корзины, помочь ничего не забыть в заказе, убрать необходимость планировать закупки и следить за заканчивающимися запасами продуктов.

**Данные**

В качестве тренировочных данных представляется датасет с историей заказов 20000 пользователей вплоть до даты отсечки, которая разделяет тренировочные и тестовые данные по времени.

train.csv:

user_id - уникальный id пользователя;
order_completed_at - дата заказа;
cart - список уникальных категорий (category_id), из которых состоял заказ.

В качестве прогноза необходимо для каждой пары пользователь-категория из примера сабмита вернуть 1, если категория будет присутствовать в следующем заказе пользователя, или 0 в ином случае. Список категорий для каждого пользователя примере сабмита - это все категории, которые он когда-либо заказывал.

sample_submission.csv:

Пример сабмита. В тест входят не все пользователи из тренировочных данных, так как некоторые из них так ничего и не заказали после даты отсечки.

id - идентификатор строки - состоит из user_id и category_id, разделенных точкой с запятой: f'{user_id};{category_id}'.

Из-за особенностей проверяющей системы Kaggle InClass, использовать колонки user_id, category_id в качестве индекса отдельно невозможно

target - 1 или 0 - будет ли данная категория присутствовать в следующем заказе пользователя

**Использованные библиотеки**

- pandas
- seaborn
- os
- numpy
- sklearn
- matplotlib
- xgboost
- lightgbm

**Проделанная работа**

- данные изучены, предобработаны и разделены на тренировочные и тестовые выборки;
- сформированы новые входные признаки;
- разработаны и обучены модели на кросс-валидации;
- выполнено предсказание на лучшей модели;

**Результаты**

В результате кросс-валидации была выбрана модель XGBClassifier. Значение метрики на Kaggle при пороге классификации 0.5 равно 0.49364 ( метрика на кросс-валидации 0.507, а на отдельной валидационной выборке 0.506). Этот результат удовлетворяет поставленной задаче.
