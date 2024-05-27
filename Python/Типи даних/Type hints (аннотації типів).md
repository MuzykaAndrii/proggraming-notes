
### Придушення перевірки
Щоб придушити перевірку типів статичних аналізаторів типів використовують коментар:
```python
some.code()  # type: ignore
```

### Типи позиційинх та іменованих аргументів
Так можна позначити тип **кожного позиційного** та **кожного іменованого** аргументів:
```python
def call(self, *args: str, **kwargs: str) -> str:
	pass
```

### Обєднання типів
Щоб задати аннотацію типу, яка може набувати різних значень потрібно використовувати `Union` із вбудованого модуля `typing`. Набір допустимих типів задається у квадратних дужках після імені класу `Union`:
```python
from typing import Union

spam: Union[int, str, float] = 42
spam = 'hello'
spam = 3.14
```
Тут змінна `spam` може приймати кілька типів: `int`, `str` чи `float`

### Опціональні типи
Якщо потрібно вказати що змінна, чи тип, який повертає функція може повернути ще `None` замість `Union[str, None]` можна використати `Optional` з модуля `typing`. Ця анотація типу означає, що функція або метод може повернути `None` замість значення очікуваного типу:
```python
from typing import Optional

last_name: Optional[str] = None
last_name = 'Sweigart'
```

Щоб вказати, що змінна, параметр або значення, що повертається, може мати будь-який тип даних, використовуйте анотацію типу `Any` (також з модуля `typing`). Також як анотацію типу можна використовувати `object`, але в такому випадку все ж краще використовувати `Any`.

Щоб оголосити типи даних значень, що зберігаються у списку, використовуйте аннотацію типу `List` модуля `typing` в **Python <= 3.8**, або `list` в **Python 3.9+**, також з версії **3.10+** можна використовувати `list[int | float]`:
```python
from typing import List, Union
numbers: List[Union[int, float]] = [42, 3.14, 99.9, 86]  # python 3.8

numbers: list[Union[int, float]] = [42, 3.14, 99.9, 86]  # python 3.9

numbers: list[int | float] = [42, 3.14, 99.9, 86]  # python 3.10
```

### Аннотації розміру кортежу
```python
three_ints: tuple[int, int int]  # tuple with exactly three ints

ints_tuple: tuple[int, ...]  # tuple with any count of ints
```

### Аннотації для вбудованих типів
Аннотації типів `Callable`, `Iterator` і `Sequence` з модуля `typing` можуть бути використані для аннотацій об'єктів, що можуть викликатись, ітераторів та послідовностей.

```python
from typing import Callable, Sequence, Iterable, Mapping

Callablle[[int, int], float]  # callable that receive two ints, and return float

Iterable  # any object that can be iterated in for loop

Sequence  # any object that have indexes

Mapping  # any object that have keys
```

### Псевдоніми типів
Деколи є корисним вказати псевдонім для вбудованого чи власного типу даних задля покращення читаності коду:
```python
from typing import TypeAlias

Celsius: TypeAlias = float

def get_temperature() -> Celsius:
	...
```

[[Типи даних]]