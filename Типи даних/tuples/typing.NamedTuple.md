`NamedTuple` з пакета `typing` - аналог namedtuple з collections, який з'явився у версії 3.6 та має більш людино зрозумілий синтаксис і додана підтримка підказок при написанні коду.
```python
from typing import NamedTuple

class Car(NamedTuple):
	color: str
	weight: float
	transmission: bool
	
car1 = Car('red', 1980, True)
```
Варто зазначити, що перевірки вказаних типів не відбуватимуться, хіба що буде використаний модуль на кшталт **mypy**

[[Tuples]]
