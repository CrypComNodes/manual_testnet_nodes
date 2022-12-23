# Source

## [Official website](https://www.sourceprotocol.io)

## [Explorer](https://explorer.nodestake.top/source-testnet/staking/sourcevaloper1aptxr5aure9q479wvefhh5hgarh3x32c4mchph)

Чтобы обезопасить себя от разрыва соединения между сервером и клиентом (mobaxterm, putty, etc...) рекомендую выполнять установку/обновление нод с использованием менеджера терминалов tmux. Tmux позволит выполнять команды "в окне", которое даст возможность сохранить выполнение процесса в случае разрыва соединения. [Команды по использованию tmux.](https://github.com/CrypComNods/manual_testnet_nodes/blob/main/tmux_commands.md)


Баланс кошелькаЖ
```
sourced query bank balances $SOURCE_WALLET_ADDRESS
```
Делегировать на себя:
```
sourced tx staking delegate sourcevaloper1aptxr5aure9q479wvefhh5hgarh3x32c4mchph $SOURCE_WALLET_ADDRESS --chain-id=sourcechain-testnet --gas=auto
```
Информация о валидаторе:
```
sourced q staking validator $(sourced keys show $SOURCE_WALLET_ADDRESS --bech val -a)
```
