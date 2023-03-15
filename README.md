# AnnaLive2022.github.io
# Project_year1
# Проект: Агентство недвижимости
1. Постановка задачи
2. Знакомство с данными, базовый анализ
3. Предобработка и очистка данных
4. Разведывательный анализ данных (EDA) удаление выбросов
5. Отбор и преобразование признаков.
6. Обучение и сравнение различных моделей обучения
7. Прогнозирование для тестового набора данных(результат)

## 1. Постановка задачи
Представитель крупного агентства недвижимости обратился со следующей проблемой:
"Мои риелторы тратят катастрофически много времени на сортировку
объявлений и поиск выгодных предложений. Поэтому их скорость реакции и качество анализа не дотягивают до уровня конкурентов.
Это сказывается на наших финансовых показателях".
Задача — разработать модель, которая позволила бы обойти конкурентов (другие агентства недвижимости) по скорости и качеству совершения сделок. 
Файл с исходными данными вы можете скачать здесь:  https://drive.google.com/file/d/1LAHTcZvAIil8kai6RSEuqPPeJMjqHN-z/view?usp=sharing

## 2. Знакомство с данными, базовый анализ
- Выведем основную информацию о числе непустых значений в столбцах и их типах в таблице.
- Обратим внимание на информацию о числе непустых значений.
- Выведим основную статистическую информацию о столбцах.

## 3. Предобработка и очистка данных
- Проанализируем датасет на наличие дублирующих записей и удалим их
- Посмотрим пропущенные значения. Удалим признаки 'mls-id' и ''fireplace', т.к.ини имеют больше 90% пропусков.
- Преобразуем признак 'target'.Удалим строки с  пустыми значениями признака 'target'.Выделим числа, уберем запятые  прелбразуем в вещественное число (float)
- Преобразуем признак 'propertyType'.Заменяем некоторые значения и приводим к более однородному виду. Уменьшим число категорий, выберем топ 50  типов стилей домов остальнеые пометим как 'other style'.
- Преобразуем признак 'stories'. Заменим пропуски на 0.Заменим некоторые значения чтобы привести признак к более однородному виду.Выделим числа и переведем их в вещественное число (float)
- Преобразуем признак 'private pool'. Объеденим два поля 'private pool' и 'PrivatePool'.
- Преобразуем признак 'state'. Выделим 25 наиболее популярных значений. остальные пометим как 'other'
- Преобразуем признак 'city'. Выделим 100 наиболее популярных значений. остальные пометим как 'other'
- Преобразуем признак 'sqft'. Заменим пропуски на 0. Удалим разделитель запятую, выделим числа и преобразуем в вещественное число (float)
- Преобразуем признак 'baths'. Заменим пропуски на ноль. Приведем в однородному виду. Выделим числа и переведем их в целое число(integer)
- Преобразуем признак 'beds'. Заменим пропуски на ноль.Переведем акры в кв. футы. Создадим два признака:'count_beds' и 'sqft_beds',содержащий квадратные футы.
- Добавим новый признак 'sqft_sum', объеденив два признака 'sqft_beds' и 'sqft'

## 4. Разведывательный анализ данных (EDA)
- Исследуем на выбросы признак 'target'. Удаляем стоимость недвижимости меньше $100000 и больше $1500000
- Прологарифмируем признак target
- Исследуем на выбросы признак 'baths'. Заменим аномальные значения в признаке baths на 75 квартиль = 3.

## 5. Отбор и преобразование признаков
- Закодируем признак 'state' с помощью метода LabelEncode
- Закодируем признак city с помощью метода LabelEncode
- Оцениваем мультиколинеарность и взаимосвязь с целевым признаком

## 6. Обучение и сравнение различных моделей
- Все наши модели мы будем обучать на логарифмированной версии y_log
- Нормализуем предикторы в обучающей и тестовой выборках с помощью MinMaxScaler из библиотеки sklearn
- Построим модель линейной регрессии на обучающей выборке
- Построим модель полиномиальной регрессии 2-ой степени 
- Построим модель полиномиальной регрессии 2-ой степени с L2-регуляризацией (регуляризация по Тихонову)
- Построим модель дерева решений (DecisionTreeRegressor) на обучающей выборке
- Построим модель случайного леса на обучающей выборке
- Построим модель градиентного бустинга над деревьями решений (GradientBoostingRegressor)
- Построим столбчатую диаграмму коэффициентов значимости каждого из факторов

## 7. Прогнозирование для тестового набора данных (результат)
