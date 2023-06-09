
| Dunder-метод | Оператор або вбудована функція |
|-------------------------|-------------------------------|
| `__lt__()`              | `<`                           |
| `__gt__()`              | `>`                           |
| `__le__()`              | `<=`                          |
| `__ge__()`              | `>=`                          |
| `__eq__()`              | `==`                          |
| `__ne__()`              | `!=`                          |

> [!important] Сортування об'єктів
> Dunder-методи порівняння не тільки реалізують шість операторів порівняння Python для об'єктів, а й дають змогу функції Python sort() сортувати об'єкти ваших класів. 

В модулі `operator` наявні такі ж операції порівнювання, тільки у вигляді функцій, це дозволяє передавати їх як параметри в інші функції чи методи, тим самим використовуючи [[Парадигми програмування.canvas|декларативний]] підхід до розробки:
```python
import operator

operator.eq(42, 42)  # True
operator.ne('cat', 'dog')  # True
operator.gt(10, 20)  # False
operator.ge(10, 10)  # True
operator.lt(10, 20)  # True
operator.le(10, 20)  # True
```

> [!info] Поведінка операторів порівняння в разі їх часткової відсутності
> Якщо в об'єкта реалізований метод `__lt__` і не реалізований `__gt__`, python при порівнянні `>` виконає метод `__lt__` та поверне обернене його значення.

[[Dunders]]