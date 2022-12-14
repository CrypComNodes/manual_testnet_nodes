# Starknet

## [Official site](https://starknet.io)

Чтобы обезопасить себя от разрыва соединения между сервером и клиентом (tmux, putty, etc...) рекомендую выполнять установку нод с использованием менеджера терминалов tmux. Tmux позваолит выполнять команды "в окне", котрое даст возможность сохранить выполнение в случае разрыва. [Команды по использованию tmux.](https://github.com/CrypComNods/manual_testnet_nodes/blob/main/tmux_commands.md)


### Обновление StarkNet v0.4.3:
```
cd ~/pathfinder
```
```
rustup update
```
```
git fetch
```
```
git checkout v0.4.3
```
```
cargo build --release --bin pathfinder
```
```
mv ~/pathfinder/target/release/pathfinder /usr/local/bin/
```
```
cd py
```
```
source .venv/bin/activate
```
```
PIP_REQUIRE_VIRTUALENV=true pip install -e .[dev]
```
```
pip install --upgrade pip
```
```
systemctl restart starknetd
```
Проверить версию после обновления 
```
pathfinder -V
```
должно быть: `Pathfinder v0.4.3`
