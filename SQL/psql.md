Створення бд та юзера
```sql
CREATE DATABASE <dbname>;
CREATE USER <user> WITH ENCRYPTED PASSWORD '<pass>';
```

Видача привілегій (потрібно зайти через юзера postgres на ту бд, для якої хочемо дати привілеї):
```sql
GRANT ALL PRIVILEGES ON SCHEMA public TO <user>

GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO <user>;
GRANT ALL PRIVILEGES ON ALL SEQUENCES IN SCHEMA public TO <user>;
GRANT ALL PRIVILEGES ON ALL FUNCTIONS IN SCHEMA public TO <user>;
```

Логін на сервер
```bash
psql -h <server> -p <port> -U <username> <database>
```
