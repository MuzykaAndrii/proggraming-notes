
## Файли конфігурації

**pytest.ini** :
```ini
[pytest]
pythonpath = . src   # path to codebase
```

**pyproject.toml** :
```toml
[tool.pytest.ini_options]
pythonpath = [".", "src"]   # path to codebase
asyncio_mode = "auto"   # async mode
python_files = ["*_test.py", "test_*.py"]   # finding test files rules
```
## Conftest
`conftest.py` - головний конфігураціонний файл для pytest. Тут описуються всі фікстури та налаштування. Файлів conftest може бути декілька для сепарації налаштувань та фікстур для різних папок з тестами.

## Параметризація
```python
import pytest

@pytest.mark.parametrize(
	"x, y, result",
	(
		(1, 2, 0.5),
		(5, -1, -5),
	)
)
def test_divide(x, y, res):
	...
```


## Обробка виключень
```python
from contextlib import nullcontext as does_not_raise
import pytest

@pytest.mark.parametrize(
	"x, y, res, expected",
	[
		(4, 2, 2, does_not_raise()),
		(5, 0, _, pytest.raises(ZeroDivisionError)),
	]
)
def test_division(x, y, res, expected):
	with expected:
		...
```

## Fixtures
Фікстури - функціональність для винесення часто використовуваних даних, або для підготовки середовища тестування.

```python
import pytest

@pytest.fixture
def users():     # data fixture
	return users

@pytest.fixture
def clear_users():   # environment preparation fixture
	UserService.delete_all()

def test_users_count(clear_users, users):  # using fixture
	assert users.count == 3

@pytest.mark.usefixtures("clear_users")  # auto use fixture in every test method
class TestUsers:
	def test_users(self, users):
		...
```

`@pytest.fixture(autouse=True)` - Автоматичне виконання фікстури при запуску pytest. Корисне для підготовки середовища.

### Області видомості фікстур
- **function** - фікстура виконуватиметься для кожної функції окремо
- **class** - один раз для кожного класу
- **module** - один раз для одного файлу
- **package** - один раз для однієї папки
- **session** - один раз за весь сеанс тестування

```python
@pytest.fixture(scope='session', autouse=True)  # once per session, run auto
def setup_db():
	Base.metadata.create_all()
	yield  # run all tests here
	Base.metadate.drop_all()
```


## Команди

```bash
pytest -x           # stop after first failure
pytest --maxfail=2  # stop after two failures
pytest -x --pdb     # drop to PDB on first failure, then end test session
```

### Підміна змінних оточення для тестування
[Бібліотека pytest-dotenv](https://pypi.org/project/pytest-dotenv/)
[Гайд](https://www.youtube.com/watch?v=zc138SwDsG0&list=PLeLN0qH0-mCVdHgdjlnKTl4jKuJgCK-4b&index=9)

## Робота з кастомними CLI параметрами
[Гайд](https://www.youtube.com/watch?v=jsrxqoVasyw&list=PLeLN0qH0-mCVdHgdjlnKTl4jKuJgCK-4b&index=11)