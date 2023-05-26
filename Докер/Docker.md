## [[Images (образи)|Образи]]
- `docker images` - список всіх образів
- `docker pull <image_name>:<tag>` - скачати образ з docker hub із версією tag
- `docker build <dockerfile_path>` - створити новий образ на основі інструкцій в dockerfile
	- `-f <filename>` якщо dockerfile названий по-іншому
	- `-t <image_name>:<image_tag>` - додавання ім'я та тегу до образу

## [[Containers (контейнери)|Контейнери]]
- `docker ps` - список запущених контейнерів
	- `a` - список усіх контейнерів
- `docker run <image_name>:<tag>` - створити і запустити новий контейнер із образу, шукає образ на локальній машині, якщо немає скачує з docker hub.
	- `-i` запускається в інтерактивному режимі
	- `-t` з терміналом.
	- `-d`, –detached в фоновому режимі
	- `—name <name>` присвоїти ім'я контейнеру, якщо не вказати присвоїться рандомне
	- `-p <external_port>:<internal_port>` - перекинути (опублікувати) порт контейнера на локальну машину (ports mapping)
	- `-v`, `–volumes <external_dir>:<internal_dir>` - перекинути папку з компютера в папку контейнера (volumes mapping)
	- `–rm` - автоматично видаляти контейнер коли він зупиняється
	- `-e <env_var_name>=<env_var_val>` - задати змінну оточення

- `docker rm <container_id/container_name>` - видалити контейнер за ім’ям або id.
- `docker stop <container_id/container_name>` - зупинити контейнер за ім’ям або id.
- `docker container prune` - видалити всі зупинені контейнери
- `docker container inspect <container_id/container_name>` - вивід даних про контейнер
- `docker exec <container_id/container_name> <process_name>` - запустити певний процес всередині запущеного контейнера, доступні аргументи `-it`
- `docker logs <container_id/container_name>` - вивід логів певного контейнера
	- `—follow` - перегляд в реальному часі

### [[Docker-compose]]
- `docker-compose up` - запустити всі контейнери
	- `-d` у фоновому режимі
	- `–build` перегенерувати образи контейнерів
- `docker-compose down` - зупиняє та видаляє усі контейнери, звязані з docker-compose