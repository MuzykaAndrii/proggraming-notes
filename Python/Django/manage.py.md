###### runserver
`manage.ру runserver` - запустити сервер джанго

###### startapp
`manage.ру startapp <app name>` - створити новий застосунок

###### shell
`manage.py shell` - інтерактивний сеанс (оболонка) для взаємодії з Django проектом

###### createsuperuser
`manage.py createsuperuser` - створити супер користувача

## migrations

###### makemigraions
`manage.py makemigrations <app name>` - створити міграції моделей з певного застосунку
- `--check` - виводить відомості про те, чи змінилися моделі після останнього формування міграцій, але не формує саму міграцію;
- `--merge` - використовується для усунення конфліктів між міграціями;

###### migrate
`manage.py migrate` - виконати міграції

###### squashmigrations
`manage.py squashmigrations <app name> [<start_migration_name>] <end_migration_name> [<result_magration_name>]` - злити міграції в одну
- `--no-optimize` - виконує злиття без оптимізації, використовується коли відбуваються помилки під час злиття міграцій

###### migrate zero
`manage.py migrate <app_name> zero` - видаляє всі міграції із вказаного застосунку, **видалити тільки певну міграцію неможливо**.

###### sqlmigrate
`manage.py sqlmigrate <app name> <migration id>` - переглянути SQL код міграцій в застосунку `<app name>` під номером `<migration id>`

[[Django]]