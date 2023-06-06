###### verbose_name
`verbose_name` - людино-зрозумілий формат, відображається в `templates`
`verbose_name_plural` - людино-зрозумілий формат в множині

###### ordering
`ordering`- параметри сортування записів моделі за замовчуванням. Задаються у вигляді списку імен полів.

###### unique_together
`unique_together` - послідовність імен полів, представлених у вигляді рядків, які мають зберігати унікальні в межах таблиці комбінації значень. У разі спроби занести в них уже наявну в таблиці комбінацію значень буде порушено виняток `ValidationError`. Можна вказувати декілька послідовностей на валідацію унікальності.

###### get_latest_by
`get_latest_by` - ім'я поля типу `DateField` або `DateTimeField`, яке буде взято в розрахунок при отриманні найпізнішого або найбільш раннього запису за допомогою методу `latest()` або `earliest()` відповідно, викликаного без параметрів. Може приймати декілька полів.

###### index_together
`index_together` - індексація по сукупності індексів в БД, також можливий такий [[Дронов В.А. - Django 3.0. Практика создания веб-сайтов на Python (Профессиональное программирование) - 2021.pdf#page=103|варіант]]

###### constraints
`constraints` - умови для занесення запису до БД, використовує список чи кортеж із екземплярами класів кожна з яких задає одну певну умову:
- `models.CheckConstraint` - умова, пов'язана із значеннями полів.
- `UniqueConstraint` - набір полів, які мають зберігати комбінації значень, унікальні в межах таблиці.
Якщо хоча б одна умова виконана не буде, повернеться помилка `IntegrityError` із модуля `django.db`.
```python
class ShopItem(models.Model):
	...
	class Meta:
		constraints = (
			models.CheckConstraint(
				check=models.Q(price__gte=0) & models.Q(price__lte=1_000_000),
				name='shop_item_price_constraint',
			),
			models.UniqueConstraint(
				fileds=('title', 'price', 'owner'),
				name='shopitem_title_and_price_uniquness',
				condition=models.Q(price__lt=10_000),
			),
		)
```
Параметр `condition` задає умову спрацювання `UniqueConstraint`.
Умови, що задаються в параметрі constraints, **обробляються на рівні СУБД** (а не Django), для чого в базі даних створюються відповідні правила.


[[Models]]