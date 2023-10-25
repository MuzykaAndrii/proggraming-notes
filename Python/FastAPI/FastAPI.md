встановлення: `fastapi[all]`
бд: `sqlalchemy alembic psycopg2`
ініціалізація міграцій: `alembic init migrations`
створити міграцію: `alembic revision --autogenerate -m "Message of revision"`
виконати міграцію: `alembic upgrade <revision_hash>/head`
бібліотека для автентифікації: `fastapi-users`
прослойка для асинхронної postgres: `asyncpg`
