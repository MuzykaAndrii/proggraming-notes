---
tags: getter, setter, deleter, property
---

`@property` - декоратор, дія якого **аналогічна із getter'ам** із інших мов програмування. Дозволяє визначати специфічну поведінку атрибуту при його поверненні. Такий атрибут називається **властивістю**. `property` не обов'язково повинно зв'язуватись із певним атрибутом, воно може повертати якесь обчислене значення із комплексу атрибутів.

`@<property_name>.setter` - декоратор, дія якого **аналогічна setter'ам** із інших мов програмування. Дозволяє визначити специфічну поведінку при присвоєнні до властивості `property_name`, тобто визначає поведінку оператора присвоєння `=`. Найчастіше використовується для **перевірки типу або формату даних** перед присвоєнням.

`@<property_name>.deleter` - визначає поведінку при видаленні властивості із використанням ключового слова `del`.

```python
class Wallet:
	def __init__(self, amount):
		self._amount = amount

	@property
	def amount(self):
		return self._amount

	@amount.setter
	def amount(self, value):
		raise CantAssignAmountError

	@amount.deleter
	def amount(self):
		self._amount = 0
```
`getter`, `setter` та `deleter` працюють із резервним атрибутом  `_amount` напряму, а самі надають доступ до цього атрибуту ззовні через властивість `amount`, якщо вказати імена атрибуту та властивості однаковими - метод `getter` буде рекурсивно викликати самого себе.

Використання `setter` прямо в конструкторі класу:
```python
class Wallet:
    def __init__(self, amount):
        self.amount = amount
    
    @property
    def amount(self):
        return self._amount
    
    @amount.setter
    def amount(self, money):
	    # some validation here ...
        self._amount = money


w = Wallet(50)
print(w.amount)  # >> 50
```
При такому підході уникається дублювання валідації в конструкторі та в `setter`.

[[Атрибути об'єкта, атрибути класу]]