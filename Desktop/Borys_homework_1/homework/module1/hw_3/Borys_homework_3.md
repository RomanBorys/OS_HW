## Завдання 1
ps aux
скрін 1.1

top
скрін 1.2

echo $$
скрін 1.3

Завдання 2

sleep 1000 &

jobs

fg %1

Ctrl + Z

kill %1

nohup sleep 1000 &

скрін 2

Завдання 3

nice -n 10 sleep 1000 &

ps aux | grep sleep

sudo renice -n 5 -p <PID>

ulimit -a

скрін 3

Завдання 4

df -h

free -h

скрін 4
