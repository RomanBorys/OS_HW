# Домашнє завдання 2
## Завдання 1
```bash
cd /
ls

cd /etc
ls

cd /home
ls

## Завдання 2

mkdir lab2
cd lab2

> file.txt
cp file.txt file_copy.txt
mv file_copy.txt file_renamed.txt

ln file.txt hard_link.txt
ln -s file.txt soft_link.txt

find ~ -name "file.txt"

## Завдання 3

ls -l file.txt
chmod 444 file.txt
chmod u+w file.txt
umask
umask 022

## Завдання 4

sudo adduser hw
sudo usermod -aG sudo hw
cat /etc/passwd | grep hw
