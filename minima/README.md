# Minima

## [Official website](https://www.minima.global)

Чтобы обезопасить себя от разрыва соединения между сервером и клиентом (mobaxterm, putty, etc...) рекомендую выполнять установку/обновление нод с использованием менеджера терминалов tmux. Tmux позволит выполнять команды "в окне", которое даст возможность сохранить выполнение процесса в случае разрыва соединения. [Команды по использованию tmux.](https://github.com/CrypComNods/manual_testnet_nodes/blob/main/tmux_commands.md)

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
