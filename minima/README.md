# Minima

## [Official website](https://www.minima.global)

Чтобы обезопасить себя от разрыва соединения между сервером и клиентом (mobaxterm, putty, etc...) рекомендую выполнять установку/обновление нод с использованием менеджера терминалов tmux. Tmux позволит выполнять команды "в окне", которое даст возможность сохранить выполнение процесса в случае разрыва соединения. [Команды по использованию tmux.](https://github.com/CrypComNods/manual_testnet_nodes/blob/main/tmux_commands.md)

### Запуск ноды на сервере под управлением ubuntu:

Если на сервере есть старая верисия ноды - удаляем

Проверить можно командой:
```
systemctl list-units --type=service
```
Запускаем скрипт для удаления ноды:
```
sudo wget -O minima_remove.sh https://raw.githubusercontent.com/minima-global/Minima/master/scripts/minima_remove.sh && sudo chmod +x minima_remove.sh && sudo ./minima_remove.sh -p 9001 -x
```
Удаляем все связанные папки:
```
sudo rm -r /home/minima/
```
Удаляем пользователя:
```
sudo userdel minima
```
Добавляем пользователя:
```
sudo adduser minima
```
Предоставляем пользователю права админа:
```
sudo usermod -aG sudo minima
```
Переключаемся на пользователя:
```
su - minima
```
Если не установлен докер - устанавливаем:
```
sudo curl -fsSL https://get.docker.com/ -o get-docker.sh
sudo chmod +x ./get-docker.sh && ./get-docker.sh
```
Добавляем пользователя в группу докера:
```
sudo usermod -aG docker $USER
```
Выходим с пользователя минима, и заходиам обратно, для применеия изменеий:
```
exit
su - minima
```
Запускаем ноду (докер контейнер с параметрами) заменив пароль в команде на свой:
```
docker run -d -e minima_mdspassword=123 -e minima_server=true -v ~/minimadocker9001:/home/minima/data -p 9001-9004:9001-9004 --restart unless-stopped --name minima9001 minimaglobal/minima:latest
```
-d: запуск демона, для работы в фоне
-e minima_mdspassword=123 : пароль для доступа к ноде, который будет использоваться в веб морде
-e minima_server=true : установить режим сервера для доступа входящих подключений
-v ~/minimadocker9001:/home/minima/data : создать локальную директорию с именем minimadocker9001 в вашей домашней директории /home/minima/data directory in Docker. The minimadocker9001 folder is where the Minima database and is also where your backups will be stored.
-p 9001-9004:9001-9004 : порты для ноды в контейнере
--restart unless-stopped : рестарт контенера, если упадёт
--name minima9001 : установка именип контейнера minima9001
minimaglobal/minima:latest : specifies where to pull the Minima code from

Включаем автозапуск для докера:
```
sudo systemctl enable docker.service
sudo systemctl enable containerd.service
```
Запускаем ещё один контейнер для автообновления ноды:
```
docker run -d --restart unless-stopped --name watchtower -e WATCHTOWER_CLEANUP=true -e WATCHTOWER_TIMEOUT=60s -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower
```
Проверяем список запущенных контейнеров:
```
docker ps
```
переходим по адресу в браузере и вводим пароль, котрый задали при запуске контейнера ноды:
```
https://YourServerIP:9003/
```
Зайти в докер контейнер для ввода команд:
```
docker exec -it minima9001 minima
```
Чтобы посмотреть пароль ввести:
```
mds
```
Для запуска второй ноды, которая будет доступна на порту 8003, ввести команду:
```
docker run -d -e minima_mdspassword=123 -e minima_server=true -v ~/minimadocker8001:/home/minima/data -p 8001-8004:9001-9004 --restart unless-stopped --name minima8001 minimaglobal/minima:latest
```
Для проверки статуса ноды ввечти команду:
```
status
```
