# Оптимизация SQL

### Замена коррелированных подзапросов
<pre>
- Используйте оконные функции или LATERAL JOIN для уменьшения количества подзапросов.
</pre>
### Индексация
<pre>
- Создавайте составные индексы по ключевым полям, таким как item_id, update_date, order_date.
</pre>
### Партционирование
<pre>
- Разбивайте большие таблицы на разделы (partitions) по датам для уменьшения объема данных.
</pre>
### Денормализация и материализованные представления
<pre>
- Добавить в таблицу заказов колонку с ценой товара на момент заказа. В случае денормализации.
- Создать материализованное представление для хранения заранее вычисленных агрегатов. В случае с материализованными представлениями.
</pre>

# Оптимизация Pandas

### Предварительная подготовка данных
<pre>
1. Сортировка
    - Для `merge_asof`, данные должны быть отсортированы по столбцу с датами (например, `update_date` и `order_date`).

2. Уменьшение типов данных

3. Индексация
</pre>
### Оптимизация операций
<pre>
1. Векторизация
    - Использование векторизированных операций pandas с помощью NumPy вместо циклов.

2. Использование категориальных данных
</pre>
### Проблемы с памятью и масштабирование 
<pre>
1. Кэширование промежуточных результатов

2. Разделение на чанки
    - Если данные не помещаются в память, можно разбивать их на части с помощью numpy (`numpy.array_split`) или метода `cut`.
</pre>
### Переход на распределённые вычисления
<pre>
- Можно использовать Dask или PySpark, если данные не помещаются в память и нужна параллельная обработка данных.
</pre>
