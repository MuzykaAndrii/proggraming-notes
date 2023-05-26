```python
for current in iterable_obj:
	# do some stuff
else:
	# if not interrupted by break
```

>[!info] Блок **else** викликається тільки тоді, коли цикл не переривається командою **break**

Цикл **for-in** являє собою синтаксичний цукор із оператором циклу **while**, застосовуючи до **Iterable**-об'єкта метод **__iter__** (або функцію **iter()** ), щоб отримати від нього обєкт **Iterator**, та  викликає в останнього метод **__next__** (або функцію **next()**), який повертає об'єкти із послідовності по одному.
```python
# syntax sugar to for loop:
iterator = iter(iterable_obj):  # or iterator = iterable_obj.__iter__()
while True:
    try:
        current = next(iterator)  # or current = iterator.__next__()
    except StopIteration:
        break
    else:
	    # body of for-in loop
```

## Вихід з вкладених циклів
Перервати зовнішній цикл із внутрішнього можна через констукцію `else`:
```python
for i in range(5):
	for j in range(5):
		if j == 2 and i == 0:
			break
	else:  # execute when the inner loop finished without any break
		continue
	break
```

З допомогою `try ... except` та `raise`:
```python
try:
	for i in range(5):
		for j in range(5):
			if j == 2 and i == 0:
				raise StopIteration
except StopIteration:
	pass
```

З допомогою переносу циклів у функцію:
```python
def check_sth():
	for i in range(5):
		for j in range(5):
			if j == 2 and i == 0:
				return
```

Найкращий спосіб це унакати вкладених функцій з допомогою функції `product` з модуля `itertools`:
```python
from itertools import product

for i, j in product(range(5), range(5)):
	if j == 2 and i == 0:
		break
```

[[Цикли]]