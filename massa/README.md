# Massa

## [Official site](https://massa.net)

Чтобы обезопасить себя от разрыва соединения между сервером и клиентом (mobaxterm, putty, etc...) рекомендую выполнять установку/обновление нод с использованием менеджера терминалов tmux. Tmux позволит выполнять команды "в окне", которое даст возможность сохранить выполнение процесса в случае разрыва соединения. [Команды по использованию tmux.](https://github.com/CrypComNods/manual_testnet_nodes/blob/main/tmux_commands.md)

Если команда rustup не обнаружена:

In my case I needed to add export PATH="$HOME/.cargo/bin:$PATH" to my .bash_profile file instead of my .profile file.

Устанавливал и настравивал по [инструкции](https://teletype.in/@letskynode/Massa#1qza)
