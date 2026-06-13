Домашнє завдання №6
Код скрипта `backup.sh`

#!/bin/bash

if [ $# -ne 2 ]; then
    echo "Usage: ./backup.sh <log_dir> <backup_dir>"
    exit 1
fi

LOG_DIR="$1"
BACKUP_DIR="$2"
LOCK_FILE="/tmp/backup.lock"

if [ ! -d "$LOG_DIR" ] || [ ! -d "$BACKUP_DIR" ]; then
    echo "Usage: ./backup.sh <log_dir> <backup_dir>"
    exit 1
fi

if [ -f "$LOCK_FILE" ]; then
    echo "Backup already running"
    exit 1
fi

touch "$LOCK_FILE"

trap "rm -f $LOCK_FILE" EXIT

ARCHIVE_NAME="logs_backup_$(date +%F_%H-%M).tar.gz"
ARCHIVE_PATH="$BACKUP_DIR/$ARCHIVE_NAME"

tar -czf "$ARCHIVE_PATH" -C "$LOG_DIR" .

if [ $? -ne 0 ]; then
    echo "Backup failed"
    exit 2
fi

echo "Backup created: $ARCHIVE_PATH"

Опис роботи скрипта

Скрипт призначений для створення резервної копії лог-файлів. Він приймає два аргументи: каталог з логами та каталог для збереження архівів.

Перед початком роботи скрипт перевіряє правильність переданих аргументів і наявність необхідних каталогів. Для запобігання одночасному запуску використовується lock-файл `/tmp/backup.lock`.

Після успішної перевірки створюється архів формату `.tar.gz`, ім'я якого містить поточну дату та час. У разі помилки виводиться повідомлення `Backup failed`, а при успішному завершенні — повідомлення з повним шляхом до створеного архіву.
