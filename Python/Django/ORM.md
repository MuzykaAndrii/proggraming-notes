## Ліниві querysets
```python
q = Entry.objects.filter(headline__startswith="What")
q = q.filter(pub_date__lte=datetime.date.today())
q = q.exclude(body_text__icontains="food")
print(q)
```
В цьому прикладі виконується тільки **один** запит до БД, у момент виконання коду `print(q)`замість тоьох разів.

## Створення об'єкту

```python
# 1 --------------------------------------------------
p = Product(name='Car', price='10_000')
p.save()
# 2 --------------------------------------------------
p = Product()
p.name = 'Car'
p.price = 10_000
p.save()
# 3 --------------------------------------------------
Product.objects.create(name='Car', price='10_000')
# 4 --------------------------------------------------
p.delete()
```

1. Створення запису в бд через конструктор, після створення щоб зберегти запис, потрібно викликати до об'єкту метод `save()`
2. Створення запису через порожній конструктор, та подальше наповнення об'єкта.
3. створення запису в бд через атрибут objects який називають диспетчером записів, та є підкласом Manager, створює об'єкт одразу, не потребує `save()`
4. Видалення запису з бд

`save(update_fields=None)`:
- `update_fields` - оновлює тільки конкретні поля

`<Model>.get_or_create(<filter_query>, defaults=...)` - Витягнути або створити запис в БД. Якщо запис не знайдено, буде створено новий із призначенням полів відносно `filter_query`.
- `defaults` - приймає словник із іншими полями для створення, в разі, якщо запис не знайдено
Повертає кортеж довжиною 2, першим елементом буде запис, а другим булеве значення, яке означатиме чи запис було знайдено, чи створено новий.

`<Model>.update_or_create(<filter_query>, defaults=...)` - те ж саме що і попередній, тільки редагує запис якщо знайдено.

## Методи атрибута objects

`all()` - виведення всіх записів, повертає `Queryset`

`get(<field name>)` - відбір одного запису за критерієм, Exception якщо не знайдено

`order_by(<fields...>)` - виведення всіх записів відсортованих по певному полю, щоб відсортувати у порядку зменшення потрібно додати знак мінус перед іменем поля. Якщо вказати `reverse()` то виведе в зворотньому порядку

`distinct(<fields...>)` - вибирає тільки записи з унікальними полями, якщо не вказати поля, буде враховувати усі наявні поля.

#### Фільтрація записів
`filter(<field name>, )` - відбір записів за критерієм

`from django.db.models import Q` - дозволяє всередині `filter` формувати складні запити із застосуванням і, або, не і т.д  [Приклад](https://books.agiliq.com/projects/django-orm-cookbook/en/latest/query_relatedtool.html)

`from django.db.models import F` - дозволяє зрівнювати у фільтрації одні значення поточного запису, із іншими його значеннями

`exclude(<exclude_query>)` - те ж саме, що і `filter`, тільки повертає всі записи, які не підходять під запит фільтрації.

`<foreign_model>.<many-to-many_model>.add(another_model)` - просте додавання до таблиці багато до багатьох нового запису

`<record>.get_next_by_<date_field_name>(<optional_filter>)` - отримати наступний доданий запис, відштовхуючись від поля `DateField` або `DateTimeField`.

`<record>.get_previous_by_<date_field_name>(<optional_filter>)` - те ж саме, що і вище, тільки повертає попередні записи.

### Множинні операції над записами

`<Model>.objects.bulk_create(<objects_sequence>, batch_size=None, ignore_conflicts=False)` - створити кілька записів через один SQL-запит.
- `<objects_sequence>` - послідовність об'єктів для створення
- `batch_size` - максимальна кількість об'єктів, яка може бути створена за раз, за замовчуванням - не обмежено
- `ignore_conflicts` - ігнорувати помилки, якщо якийсь із записів не проходить валідацію чи порушує правила додавання нового запису.
Повертає `QuerySet` із збереженими даними.

> [!important] `bulk_create` не викликає метод `save()`
> `bulk_create` створює записи засобами СУБД, тому якщо ви визначили якусь особливу логіку в методі `save()`, вона ігноруватиметься.

`<Model>.objects.bulk_update(<objects>, <update_fields>, batch_size, ignore_conflicts)` - те ж саме що і вище, тільки приймає ще і поля для оновлення. `save()` також не викликається.

`<Model>.objects.filter(...).update(<update_fileds>)` - оновлює поля моделей за певну кількість SQL-запитів

### Q-запити
Q-запит - дозволяє створювати комплексні запити з логічними операторами:  **і, або, не**
Ці запит можуть на льоту генеруватись для подальшого використання:
```python
user_query = Q(is_active=True)
value = params['value']

if 'name' in params:
	user_query.add(Q(name__icontains=value) | Q(surname__icontains=value), Q.OR)
if 'email' in params:
	user_query.add(Q(email__icontains=value), Q.OR)

User.objects.filter(user_query)
```

[[Models]]