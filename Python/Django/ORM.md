## Створення об'єкту
`<Class name>(<Model fields via named args>)` - створення запису в бд через конструктор, після створення щоб зберегти запис, потрібно викликати до об'єкту метод `save()`

`<Model name>.objects.create(<Model fields via named args>)` - створення запису в бд через атрибут objects який називають диспетчером записів, та є підкласом Manager, створює об'єкт одразу, не потребує `save()`

`<Record object>.delete()` - видалення запису з бд

## Методи атрибута objects

`all()` - виведення всіх записів, повертає `Queryset`

`get(<field name>)` - відбір одного запису за критерієм, Exception якщо не знайдено

`order_by(<field name>)` - виведення всіх записів відсортованих по певному полю, щоб відсортувати у порядку зменшення потрібно додати знак мінус перед іменем поля

`filter(<field name>, )` - відбір записів за критерієм
`from django.db.models import Q` - дозволяє всередині `filter` формувати складні запити із застосуванням і, або, не і т.д  [Приклад](https://books.agiliq.com/projects/django-orm-cookbook/en/latest/query_relatedtool.html)

`<foreign_model>.<many-to-many_model>.add(another_model)` - просте додавання до таблиці багато до багатьох нового запису


[[Models]]