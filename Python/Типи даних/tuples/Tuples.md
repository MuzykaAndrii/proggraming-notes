**Кортежі** - незмінний (**immutable**) тип даних, можуть містити різні типи всередині.

- Не підтримують зміну чи видалення об'єктів всередині. ==Проте якщо якийсь елемент кортежу є змінюваним, то його зміна (мутація) не призведе до помилки==. (`append` до списку, який є елементом кортежу, не викличе помилку, але оператор `+` викличе, тому що результатом конкатенації є новий об'єкт.)
- 
- При додаванні (конкатенації) нового об'єкта до кортежу відбувається створення нового кортежу та вставка в нього копії першого кортежу та нового елементу.

- Кортеж може бути ключем словника або елементом множини, так як є незмінним типом даних та хешованим. Проте якщо в кортежі будуть міститись змінювані типи даних (`list`, `dict` і тд.) виникне помилка **TypeError: unhashable type**.

- Семантика використання Tuples відповідає збереженню в них різнотипних даних, на відміну від list - однотипних

Методи, яких немає в list:
```python
t = ('a', 'a', 'b')
t.count('a')  # >> 2
t.index('a')  # >> 0
```
- `count` – Число входжень елемента
- `index` – Позиція першого входження

[[Sequence (послідовність)]]