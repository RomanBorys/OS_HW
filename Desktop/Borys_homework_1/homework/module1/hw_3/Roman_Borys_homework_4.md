

Завдання 1

```bash

sudo apt update

Встановлення пакета tree
sudo apt install tree -y

Перевірка версії пакета
tree --version

Видалення пакета
sudo apt remove tree -y

Завдання 2

Перевірка статусу сервісу
systemctl status cron

Зупинка сервісу
sudo systemctl stop cron

Перевірка статусу після зупинки
systemctl status cron

Запуск сервісу
sudo systemctl start cron

Додавання в автозавантаження
sudo systemctl enable cron

Завдання 3
Перегляд syslog
cd /var/log
tail -n 10 syslog

Перегляд помилок через journalctl
journalctl -p err

Логи сервісу cron
journalctl -u cron

Завдання 4
Створення скрипта
nano ~/myscript.sh

#!/bin/bash
while true
do
  date >> /home/roman/dates.log
  sleep 1
done

Надання прав
chmod +x ~/myscript.sh

Створення systemd сервісу
sudo nano /etc/systemd/system/myscript.service

[Unit]
Description=My Script Service
After=network.target

[Service]
ExecStart=/home/roman/myscript.sh
Restart=always
User=roman

[Install]
WantedBy=multi-user.target

Активація сервісу
sudo systemctl daemon-reload
sudo systemctl enable myscript.service
sudo systemctl start myscript.service

Перевірка статусу
systemctl status myscript.service

Перевірка лог-файлу
tail -f ~/dates.log
