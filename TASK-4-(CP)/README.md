# Установка Linux Mint на виртуальную машину

## Оглавление
1. [Введение](#введение)
2. [Системные требования](#системные-требования)
3. [Подготовка](#подготовка)
4. [Установка VirtualBox](#установка-virtualbox)
5. [Создание виртуальной машины](#создание-виртуальной-машины)
6. [Установка Linux Mint](#установка-linux-mint)
7. [Первоначальная настройка](#первоначальная-настройка)
8. [Практические задания](#практические-задания)

## Введение

Linux Mint — это популярный дистрибутив Linux, основанный на Ubuntu, который отличается простотой использования и стабильностью. Установка на виртуальную машину позволяет изучать операционную систему без риска для основной системы.

**Цели работы:**
- Изучить процесс установки операционной системы Linux
- Освоить работу с виртуальными машинами
- Получить практические навыки работы в Linux Mint
- Изучить основные команды и возможности системы

## Системные требования

### Для хост-системы (компьютер):
- Процессор с поддержкой виртуализации (Intel VT-x или AMD-V)
- ОЗУ: минимум 4 ГБ (рекомендуется 8 ГБ и более)
- Свободное место на диске: минимум 30 ГБ
- Операционная система: Windows 10/11, macOS или Linux

### Для виртуальной машины Linux Mint:
- ОЗУ: 2-4 ГБ (рекомендуется 4 ГБ)
- Жесткий диск: 20-30 ГБ
- Видеопамять: 128 МБ
- Процессор: 1-2 ядра

## Подготовка

### Шаг 1: Включение виртуализации в BIOS/UEFI
1. Перезагрузите компьютер и войдите в BIOS/UEFI (обычно клавиши F2, F12, Del во время загрузки)
2. Найдите раздел "CPU Configuration" или "Advanced"
3. Включите опции:
   - Intel VT-x (для процессоров Intel)
   - AMD-V (для процессоров AMD)
   - Virtualization Technology
4. Сохраните изменения и выйдите

### Шаг 2: Загрузка необходимых файлов
1. **VirtualBox**: скачайте с официального сайта https://www.virtualbox.org/
2. **Linux Mint ISO**: скачайте с https://linuxmint.com/download.php
   - Рекомендуется версия Cinnamon (64-bit)
   - Размер файла: ~2-3 ГБ

## Установка VirtualBox

### Windows:
1. Запустите скачанный установочный файл VirtualBox
2. Следуйте инструкциям мастера установки
3. Примите условия лицензии
4. Оставьте компоненты по умолчанию
5. При запросе установки драйверов согласитесь
6. Завершите установку и перезагрузите компьютер

### Linux (Ubuntu/Debian):
```bash
# Обновление системы
sudo apt update && sudo apt upgrade -y

# Установка VirtualBox
sudo apt install -y virtualbox virtualbox-ext-pack virtualbox-guest-utils

# Добавление пользователя в группу vboxusers
sudo usermod -aG vboxusers $USER
```

## Создание виртуальной машины

### Шаг 1: Запуск VirtualBox и создание новой ВМ
1. Запустите Oracle VM VirtualBox
2. Нажмите кнопку **"Создать"** (New)
3. Заполните параметры:
   - **Имя**: Linux Mint
   - **Папка машины**: оставьте по умолчанию или выберите другую
   - **Тип**: Linux
   - **Версия**: Ubuntu (64-bit)

### Шаг 2: Настройка параметров ВМ
1. **Объем памяти**: 
   - Минимум: 2048 МБ (2 ГБ)
   - Рекомендуется: 4096 МБ (4 ГБ)

2. **Жесткий диск**:
   - Выберите "Создать новый виртуальный жесткий диск"
   - Тип файла: VDI (VirtualBox Disk Image)
   - Формат хранения: Динамический виртуальный жесткий диск
   - Размер: 25-30 ГБ

### Шаг 3: Дополнительные настройки
1. Выберите созданную ВМ и нажмите **"Настроить"**
2. **Система**:
   - Процессор: 2 ядра (если доступно)
   - Включить PAE/NX
   - Включить аппаратную виртуализацию
3. **Дисплей**:
   - Видеопамять: 128 МБ
   - Включить 3D-ускорение
4. **Носители**:
   - Подключить ISO-образ Linux Mint к CD/DVD приводу
   - Контроллер IDE → Пустой → Выбрать файл диска → Выбрать ISO-образ

## Установка Linux Mint

### Шаг 1: Запуск виртуальной машины
1. Выберите ВМ "Linux Mint" и нажмите **"Запустить"**
2. ВМ загрузится с ISO-образа
3. Дождитесь загрузки Live-системы Linux Mint

### Шаг 2: Запуск установки
1. На рабочем столе найдите значок **"Install Linux Mint"**
2. Двойной клик для запуска установщика

### Шаг 3: Процесс установки
1. **Выбор языка**: выберите "Русский" и нажмите "Продолжить"

2. **Раскладка клавиатуры**: 
   - Выберите "Russian"
   - Протестируйте в поле ввода
   - Нажмите "Продолжить"

3. **Мультимедиа кодеки**:
   - Установите флажок "Установить стороннее ПО"
   - Нажмите "Продолжить"

4. **Тип установки**:
   - Выберите "Стереть диск и установить Linux Mint"
   - Нажмите "Установить сейчас"
   - Подтвердите "Продолжить"

5. **Часовой пояс**:
   - Выберите ваш регион на карте
   - Нажмите "Продолжить"

6. **Информация о пользователе**:
   - Ваше имя: введите полное имя
   - Имя компьютера: mint-vm
   - Имя пользователя: student
   - Пароль: создайте надежный пароль
   - Подтверждение пароля: повторите пароль
   - Выберите "Входить в систему автоматически" (для удобства)
   - Нажмите "Продолжить"

### Шаг 4: Завершение установки
1. Дождитесь завершения копирования файлов (10-15 минут)
2. Нажмите "Перезагрузить"
3. Извлеките ISO-образ из виртуального привода
4. Нажмите Enter для перезагрузки

## Первоначальная настройка

### Шаг 1: Первый запуск
1. После загрузки появится экран приветствия
2. Просмотрите информационные слайды
3. Снимите флажок "Показывать это окно при запуске"

### Шаг 2: Обновление системы
Откройте терминал (Ctrl+Alt+T) и выполните:
```bash
# Обновление списка пакетов
sudo apt update

# Обновление системы
sudo apt upgrade -y

# Перезагрузка (если требуется)
sudo reboot
```

### Шаг 3: Установка дополнений гостевой ОС (Guest Additions)
1. В меню VirtualBox: Устройства → Подключить образ диска Дополнений гостевой ОС
2. В Linux Mint откроется окно с CD
3. Откройте терминал в папке с CD:
```bash
# Переход в папку CD
cd /media/student/VBox_GAs_*

# Установка дополнений
sudo ./VBoxLinuxAdditions.run

# Перезагрузка
sudo reboot
```

### Шаг 4: Настройка общих папок (опционально)
1. В VirtualBox: Устройства → Общие папки → Настроить общие папки
2. Добавьте папку с хост-системы
3. В Linux Mint папка будет доступна в /media/sf_имя_папки

## Практические задания

### Блок 1: Знакомство с системой (Задания 1-10)

**Задание 1:** Изучение рабочего стола
- Изучите панель задач и главное меню
- Найдите и запустите файловый менеджер
- Откройте системный монитор и изучите процессы
- Переключите раскладку клавиатуры (Shift+Alt)
- Сделайте скриншот рабочего стола

**Задание 2:** Работа с терминалом
- Откройте терминал (Ctrl+Alt+T)
- Изучите приглашение командной строки
- Выполните команду `whoami` и `date`
- Откройте второй терминал в новой вкладке (Ctrl+Shift+T)
- Закройте терминал командой `exit`

**Задание 3:** Навигация по файловой системе
```bash
# Узнать текущую директорию
pwd

# Перейти в домашнюю папку
cd ~

# Показать содержимое папки
ls -la

# Перейти в корневую директорию
cd /

# Изучить структуру файловой системы
ls -l
```

**Задание 4:** Работа с файлами и папками
```bash
# Создать папку
mkdir ~/test_folder

# Перейти в созданную папку
cd ~/test_folder

# Создать пустой файл
touch test_file.txt

# Создать файл с содержимым
echo "Hello, Linux Mint!" > hello.txt

# Просмотреть содержимое файла
cat hello.txt

# Скопировать файл
cp hello.txt hello_copy.txt

# Переименовать файл
mv hello_copy.txt greeting.txt
```

**Задание 5:** Изучение справочной системы
```bash
# Просмотр руководства по команде
man ls
man cp
man mkdir

# Краткая справка по команде
ls --help
cp --help

# Поиск команд по ключевому слову
apropos file
```

**Задание 6:** Работа с текстовыми редакторами
```bash
# Создать файл в редакторе nano
nano my_notes.txt

# В редакторе введите информацию о себе:
# - Имя, фамилия
# - Группа
# - Дата выполнения задания

# Сохранить: Ctrl+O, Enter
# Выйти: Ctrl+X
```

**Задание 7:** Поиск файлов
```bash
# Поиск файлов по имени
find ~ -name "*.txt"

# Поиск в текущей папке
find . -type f -name "test*"

# Поиск папок
find ~ -type d -name "*test*"

# Поиск файлов по содержимому
grep -r "Hello" ~/test_folder/
```

**Задание 8:** Архивация и разархивация
```bash
# Создать несколько тестовых файлов
echo "File 1" > file1.txt
echo "File 2" > file2.txt
echo "File 3" > file3.txt

# Создать архив tar
tar -czf my_archive.tar.gz *.txt

# Просмотреть содержимое архива
tar -tzf my_archive.tar.gz

# Разархивировать в новую папку
mkdir extracted
tar -xzf my_archive.tar.gz -C extracted/
```

**Задание 9:** Мониторинг системы
```bash
# Информация о системе
uname -a
lsb_release -a

# Информация о процессоре
lscpu

# Информация о памяти
free -h

# Информация о дисках
df -h

# Запущенные процессы
ps aux

# Процессы в реальном времени
top
# (для выхода нажмите q)
```

**Задание 10:** Управление процессами
```bash
# Запустить процесс в фоне
sleep 100 &

# Посмотреть фоновые задачи
jobs

# Найти процесс по имени
pgrep sleep

# Завершить процесс по PID
kill $(pgrep sleep)

# Запустить калькулятор и найти его процесс
gnome-calculator &
ps aux | grep calculator
```

### Блок 2: Управление файлами и правами доступа (Задания 11-20)

**Задание 11:** Изучение прав доступа
```bash
# Создать тестовые файлы
touch test1.txt test2.txt test3.txt

# Просмотреть права доступа
ls -l test*.txt

# Изучить значение каждого символа в правах доступа
# Объяснить что означает: -rw-rw-r--
```

**Задание 12:** Изменение прав доступа (chmod)
```bash
# Установить права только для владельца (чтение и запись)
chmod 600 test1.txt

# Установить права для всех (чтение, запись, выполнение)
chmod 777 test2.txt

# Установить права с помощью символьной записи
chmod u+x test3.txt  # добавить выполнение владельцу
chmod g-w test3.txt  # убрать запись группе
chmod o=r test3.txt  # только чтение остальным

# Проверить результат
ls -l test*.txt
```

**Задание 13:** Работа с владельцами файлов
```bash
# Создать файл от имени текущего пользователя
touch owner_test.txt

# Посмотреть владельца файла
ls -l owner_test.txt

# Попробовать изменить владельца (будет ошибка)
# chown root owner_test.txt

# Изучить информацию о текущем пользователе
id
whoami
groups
```

**Задание 14:** Создание и управление ссылками
```bash
# Создать файл с содержимым
echo "Original file content" > original.txt

# Создать жесткую ссылку
ln original.txt hard_link.txt

# Создать символическую ссылку
ln -s original.txt soft_link.txt

# Изучить различия
ls -li original.txt hard_link.txt soft_link.txt

# Удалить оригинальный файл и проверить ссылки
rm original.txt
cat hard_link.txt
cat soft_link.txt
```

**Задание 15:** Работа с переменными окружения
```bash
# Просмотреть все переменные окружения
env

# Просмотреть конкретные переменные
echo $HOME
echo $USER
echo $PATH

# Создать собственную переменную
export MY_VAR="Hello World"
echo $MY_VAR

# Добавить папку в PATH
export PATH=$PATH:~/test_folder
echo $PATH
```

**Задание 16:** Перенаправление ввода-вывода
```bash
# Перенаправить вывод в файл
ls -la > file_list.txt

# Добавить к существующему файлу
date >> file_list.txt

# Использовать файл как ввод
sort < file_list.txt

# Перенаправить ошибки
ls /nonexistent 2> errors.txt

# Перенаправить вывод и ошибки
ls /nonexistent > output.txt 2> errors.txt
```

**Задание 17:** Использование каналов (pipes)
```bash
# Показать первые строки списка процессов
ps aux | head

# Найти процесс по имени
ps aux | grep bash

# Подсчитать количество файлов в папке
ls -1 | wc -l

# Сортировка и уникальные значения
cat /etc/passwd | cut -d: -f3 | sort -n | uniq
```

**Задание 18:** Планирование задач (cron)
```bash
# Посмотреть текущие задачи cron
crontab -l

# Редактировать задачи cron
crontab -e

# Добавить задачу (выполнять каждую минуту)
# * * * * * echo "$(date): Cron task executed" >> ~/cron_log.txt

# Сохранить и выйти
# Подождать несколько минут и проверить лог
tail ~/cron_log.txt
```

**Задание 19:** Работа с сетью
```bash
# Информация о сетевых интерфейсах
ip addr show
ifconfig

# Проверить соединение
ping -c 4 google.com

# Информация о сетевых соединениях
netstat -tuln

# DNS информация
nslookup google.com

# Загрузить файл из интернета
wget https://www.google.com/robots.txt
```

**Задание 20:** Установка и удаление программ
```bash
# Обновить список пакетов
sudo apt update

# Найти пакет
apt search htop

# Установить пакет
sudo apt install htop

# Запустить установленную программу
htop

# Удалить пакет
sudo apt remove htop

# Очистить кэш пакетов
sudo apt autoremove
sudo apt autoclean
```

### Блок 3: Системное администрирование (Задания 21-30)

**Задание 21:** Управление службами (systemd)
```bash
# Список всех служб
systemctl list-units --type=service

# Статус конкретной службы
systemctl status networking

# Запустить службу
sudo systemctl start bluetooth

# Остановить службу
sudo systemctl stop bluetooth

# Включить автозапуск службы
sudo systemctl enable bluetooth

# Отключить автозапуск
sudo systemctl disable bluetooth
```

**Задание 22:** Мониторинг системных ресурсов
```bash
# Использование диска
du -sh ~/
du -sh /* 2>/dev/null

# Мониторинг в реальном времени
iostat 1
vmstat 1

# Информация о загруженных модулях ядра
lsmod

# Информация об оборудовании
lshw -short
lspci
lsusb
```

**Задание 23:** Работа с логами
```bash
# Системные логи
sudo journalctl

# Логи загрузки
sudo journalctl -b

# Логи за последний час
sudo journalctl --since "1 hour ago"

# Логи конкретной службы
sudo journalctl -u networking

# Следить за логами в реальном времени
sudo journalctl -f
```

**Задание 24:** Управление пользователями и группами
```bash
# Создать нового пользователя
sudo useradd -m testuser

# Установить пароль пользователю
sudo passwd testuser

# Создать группу
sudo groupadd testgroup

# Добавить пользователя в группу
sudo usermod -aG testgroup testuser

# Информация о пользователе
id testuser

# Удалить пользователя
sudo userdel -r testuser

# Удалить группу
sudo groupdel testgroup
```

**Задание 25:** Настройка сетевых параметров
```bash
# Текущая сетевая конфигурация
ip route show
ip addr show

# Настройка статического IP (пример)
# sudo ip addr add 192.168.1.100/24 dev eth0
# sudo ip route add default via 192.168.1.1

# Настройка DNS
cat /etc/resolv.conf

# Тестирование сетевого соединения
traceroute google.com
mtr google.com
```

**Задание 26:** Резервное копирование
```bash
# Создать тестовые данные
mkdir ~/backup_test
echo "Important data 1" > ~/backup_test/file1.txt
echo "Important data 2" > ~/backup_test/file2.txt

# Простое копирование
cp -r ~/backup_test ~/backup_copy

# Создать архив с датой
tar -czf ~/backup_$(date +%Y%m%d_%H%M%S).tar.gz ~/backup_test

# Синхронизация с rsync
rsync -av ~/backup_test/ ~/backup_sync/

# Проверить бэкапы
ls -la ~/backup*
```

**Задание 27:** Автоматизация с помощью скриптов
```bash
# Создать простой bash-скрипт
cat << 'EOF' > ~/system_info.sh
#!/bin/bash

echo "=== System Information ==="
echo "Date: $(date)"
echo "Uptime: $(uptime)"
echo "Disk usage:"
df -h /
echo "Memory usage:"
free -h
echo "Load average: $(cat /proc/loadavg)"
EOF

# Сделать скрипт исполняемым
chmod +x ~/system_info.sh

# Запустить скрипт
~/system_info.sh
```

**Задание 28:** Работа с брандмауэром (UFW)
```bash
# Статус брандмауэра
sudo ufw status

# Включить брандмауэр
sudo ufw enable

# Разрешить SSH
sudo ufw allow ssh

# Разрешить HTTP
sudo ufw allow 80

# Заблокировать порт
sudo ufw deny 23

# Список правил
sudo ufw status numbered

# Удалить правило
sudo ufw delete 3
```

**Задание 29:** Мониторинг безопасности
```bash
# Последние входы в систему
last

# Неудачные попытки входа
sudo lastb

# Открытые порты
sudo netstat -tulpn

# Активные соединения
sudo ss -tulpn

# Проверка целостности файлов
sudo find /etc -type f -exec ls -l {} \; > /tmp/etc_files.txt
```

**Задание 30:** Обновление и патчи системы
```bash
# Проверить доступные обновления
apt list --upgradable

# Обновить систему
sudo apt update && sudo apt upgrade

# Обновить только пакеты безопасности
sudo apt list --upgradable | grep -i security

# Настроить автоматические обновления
sudo apt install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
```

### Блок 4: Продвинутые задачи (Задания 31-40)

**Задание 31:** Настройка SSH-сервера
```bash
# Установить SSH-сервер
sudo apt install openssh-server

# Проверить статус службы
sudo systemctl status ssh

# Настроить SSH (отредактировать конфигурацию)
sudo nano /etc/ssh/sshd_config

# Изменить порт SSH на 2222
# Port 2222

# Перезапустить службу
sudo systemctl restart ssh

# Подключиться к локальному SSH
ssh student@localhost -p 2222
```

**Задание 32:** Работа с контейнерами (Docker)
```bash
# Установить Docker (если доступен)
sudo apt install docker.io

# Добавить пользователя в группу docker
sudo usermod -aG docker $USER

# После перезахода в систему:
# Запустить тестовый контейнер
docker run hello-world

# Просмотреть образы
docker images

# Просмотреть контейнеры
docker ps -a
```

**Задание 33:** Настройка веб-сервера Apache
```bash
# Установить Apache
sudo apt install apache2

# Запустить службу
sudo systemctl start apache2
sudo systemctl enable apache2

# Создать простую веб-страницу
echo "<h1>Hello from Linux Mint!</h1>" | sudo tee /var/www/html/index.html

# Проверить в браузере: http://localhost
firefox http://localhost

# Просмотреть логи Apache
sudo tail -f /var/log/apache2/access.log
```

**Задание 34:** Работа с базой данных MySQL/MariaDB
```bash
# Установить MariaDB
sudo apt install mariadb-server

# Запустить безопасную установку
sudo mysql_secure_installation

# Подключиться к базе данных
sudo mysql

# В MySQL консоли:
CREATE DATABASE testdb;
USE testdb;
CREATE TABLE users (id INT PRIMARY KEY, name VARCHAR(50));
INSERT INTO users VALUES (1, 'Test User');
SELECT * FROM users;
EXIT;
```

**Задание 35:** Мониторинг производительности
```bash
# Установить дополнительные утилиты мониторинга
sudo apt install sysstat iotop nethogs

# Мониторинг производительности процессора
sar 1 5

# Мониторинг дисковой активности
iotop

# Мониторинг сетевой активности по процессам
sudo nethogs

# Создать нагрузку на систему для тестирования
stress --cpu 2 --timeout 30s
```

**Задание 36:** Настройка файлового сервера (Samba)
```bash
# Установить Samba
sudo apt install samba

# Создать папку для общего доступа
mkdir ~/shared_folder
chmod 755 ~/shared_folder

# Настроить Samba
sudo nano /etc/samba/smb.conf

# Добавить в конец файла:
[shared]
    path = /home/student/shared_folder
    browseable = yes
    read only = no
    guest ok = yes

# Создать пользователя Samba
sudo smbpasswd -a student

# Перезапустить службу
sudo systemctl restart smbd
```

**Задание 37:** Работа с LVM (Logical Volume Manager)
```bash
# Посмотреть текущую конфигурацию дисков
lsblk
sudo fdisk -l

# Информация о LVM (если используется)
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay

# Создать файл как диск для тестирования
sudo dd if=/dev/zero of=/tmp/test_disk.img bs=1M count=100

# Подключить как loop device
sudo losetup /dev/loop0 /tmp/test_disk.img

# Создать физический том
sudo pvcreate /dev/loop0
```

**Задание 38:** Автоматизация с Ansible (базовое знакомство)
```bash
# Установить Ansible
sudo apt install ansible

# Создать инвентарь
echo "localhost ansible_connection=local" > ~/inventory

# Создать простой playbook
cat << 'EOF' > ~/test_playbook.yml
---
- hosts: localhost
  tasks:
    - name: Create test directory
      file:
        path: /tmp/ansible_test
        state: directory
    
    - name: Create test file
      copy:
        content: "Hello from Ansible!"
        dest: /tmp/ansible_test/hello.txt
EOF

# Запустить playbook
ansible-playbook -i ~/inventory ~/test_playbook.yml
```

**Задание 39:** Настройка VPN (OpenVPN)
```bash
# Установить OpenVPN
sudo apt install openvpn

# Создать структуру папок для конфигурации
sudo mkdir -p /etc/openvpn/server
sudo mkdir -p /etc/openvpn/client

# Изучить примеры конфигурации
ls /usr/share/doc/openvpn/examples/

# Создать простую конфигурацию клиента
cat << 'EOF' > ~/client.ovpn
client
dev tun
proto udp
remote your-server.com 1194
ca ca.crt
cert client.crt
key client.key
EOF
```

**Задание 40:** Финальный проект - мониторинг системы
```bash
# Создать комплексный скрипт мониторинга
cat << 'EOF' > ~/monitor.sh
#!/bin/bash

LOG_FILE="/var/log/system_monitor.log"
DATE=$(date '+%Y-%m-%d %H:%M:%S')

# Функция логирования
log_info() {
    echo "[$DATE] $1" | sudo tee -a $LOG_FILE
}

# Проверка использования диска
DISK_USAGE=$(df -h / | awk 'NR==2 {print $5}' | sed 's/%//')
if [ $DISK_USAGE -gt 80 ]; then
    log_info "WARNING: Disk usage is ${DISK_USAGE}%"
fi

# Проверка использования памяти
MEM_USAGE=$(free | awk 'FNR==2{printf "%.0f", $3/$2*100}')
if [ $MEM_USAGE -gt 80 ]; then
    log_info "WARNING: Memory usage is ${MEM_USAGE}%"
fi

# Проверка загрузки системы
LOAD=$(uptime | awk -F'load average:' '{print $2}' | awk '{print $1}' | sed 's/,//')
LOAD_INT=$(echo "$LOAD * 100" | bc | cut -d. -f1)
if [ $LOAD_INT -gt 200 ]; then
    log_info "WARNING: High system load: $LOAD"
fi

# Проверка активных соединений
CONNECTIONS=$(netstat -tuln | wc -l)
log_info "INFO: Active connections: $CONNECTIONS"

# Проверка свободного места в /tmp
TMP_USAGE=$(df -h /tmp | awk 'NR==2 {print $5}' | sed 's/%//')
log_info "INFO: /tmp usage: ${TMP_USAGE}%"

log_info "System check completed"
EOF

# Сделать скрипт исполняемым
chmod +x ~/monitor.sh

# Запустить скрипт
~/monitor.sh

# Добавить в cron для запуска каждые 5 минут
echo "*/5 * * * * /home/student/monitor.sh" | crontab -
```

### Блок 5: Дополнительные задания (41-50)

**Задание 41:** Работа с Git
```bash
# Установить Git (если не установлен)
sudo apt install git

# Настроить Git
git config --global user.name "Student Name"
git config --global user.email "student@example.com"

# Создать репозиторий
mkdir ~/git_project
cd ~/git_project
git init

# Создать файл и добавить его
echo "# My Linux Project" > README.md
git add README.md
git commit -m "Initial commit"

# Просмотреть историю
git log --oneline
```

**Задание 42:** Работа с разделами диска (fdisk)
```bash
# Просмотреть существующие разделы
sudo fdisk -l

# Информация о файловых системах
lsblk -f

# Создать файл-образ диска для тестирования
sudo dd if=/dev/zero of=/tmp/test_disk.img bs=1M count=200

# Подключить как loop device
sudo losetup /dev/loop1 /tmp/test_disk.img

# Создать разделы с fdisk
sudo fdisk /dev/loop1
# В fdisk: n (новый раздел), p (первичный), принять настройки по умолчанию, w (записать)
```

**Задание 43:** Настройка системы печати (CUPS)
```bash
# Установить CUPS
sudo apt install cups

# Запустить службу печати
sudo systemctl start cups
sudo systemctl enable cups

# Добавить пользователя в группу lpadmin
sudo usermod -aG lpadmin student

# Открыть веб-интерфейс CUPS
firefox http://localhost:631

# Команды управления принтерами
lpstat -p
lpoptions -d
```

**Задание 44:** Работа с системой инициализации
```bash
# Изучить загрузочные цели (targets)
systemctl list-units --type=target

# Посмотреть текущую цель по умолчанию
systemctl get-default

# Изменить цель по умолчанию (пример)
sudo systemctl set-default multi-user.target

# Вернуть графическую цель
sudo systemctl set-default graphical.target

# Создать собственную службу
cat << 'EOF' | sudo tee /etc/systemd/system/hello.service
[Unit]
Description=Hello Service
After=network.target

[Service]
Type=oneshot
ExecStart=/bin/echo "Hello from systemd service"
RemainAfterExit=true

[Install]
WantedBy=multi-user.target
EOF

# Перезагрузить systemd и запустить службу
sudo systemctl daemon-reload
sudo systemctl enable hello.service
sudo systemctl start hello.service
sudo systemctl status hello.service
```

**Задание 45:** Оптимизация производительности
```bash
# Анализ времени загрузки
systemd-analyze
systemd-analyze blame
systemd-analyze critical-chain

# Настройка swappiness
cat /proc/sys/vm/swappiness
echo 'vm.swappiness=10' | sudo tee -a /etc/sysctl.conf

# Очистка кэшей
sudo sync
sudo sysctl vm.drop_caches=3

# Проверка температуры процессора (если доступно)
sensors

# Управление частотой процессора
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
sudo apt install cpufrequtils
cpufreq-info
```

**Задание 46:** Работа с шифрованием
```bash
# Создать зашифрованный архив
echo "Secret data" > secret.txt
gpg --symmetric --cipher-algo AES256 secret.txt

# Расшифровать файл
gpg secret.txt.gpg

# Создать зашифрованную папку с encfs (если доступно)
sudo apt install encfs
mkdir ~/encrypted_folder
mkdir ~/decrypted_view
encfs ~/encrypted_folder ~/decrypted_view

# Работа с зашифрованной папкой
echo "Encrypted file content" > ~/decrypted_view/test.txt
ls ~/encrypted_folder/
ls ~/decrypted_view/

# Размонтировать
fusermount -u ~/decrypted_view
```

**Задание 47:** Настройка многопользовательского окружения
```bash
# Создать несколько тестовых пользователей
sudo useradd -m alice
sudo useradd -m bob
sudo passwd alice
sudo passwd bob

# Создать общую группу
sudo groupadd shared_group
sudo usermod -aG shared_group alice
sudo usermod -aG shared_group bob
sudo usermod -aG shared_group student

# Создать общую папку с правильными правами
sudo mkdir /opt/shared
sudo chown root:shared_group /opt/shared
sudo chmod 2775 /opt/shared

# Тест: создать файлы от разных пользователей
sudo -u alice touch /opt/shared/alice_file.txt
sudo -u bob touch /opt/shared/bob_file.txt
ls -la /opt/shared/
```

**Задание 48:** Автоматизированное развертывание
```bash
# Создать скрипт автоматической настройки новой системы
cat << 'EOF' > ~/setup_system.sh
#!/bin/bash

echo "=== System Setup Script ==="

# Обновление системы
echo "Updating system..."
sudo apt update && sudo apt upgrade -y

# Установка основных пакетов
echo "Installing essential packages..."
sudo apt install -y \
    curl wget git vim htop tree \
    build-essential software-properties-common \
    apt-transport-https ca-certificates gnupg lsb-release

# Настройка Git
echo "Configuring Git..."
git config --global init.defaultBranch main
git config --global pull.rebase false

# Создание рабочих директорий
echo "Creating work directories..."
mkdir -p ~/Projects ~/Scripts ~/Downloads

# Настройка bashrc
echo "Configuring shell..."
cat << 'BASHRC' >> ~/.bashrc

# Custom aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
alias ..='cd ..'
alias ...='cd ../..'
alias h='history'
alias c='clear'

# Custom functions
function mkcd() {
    mkdir -p "$1" && cd "$1"
}

BASHRC

echo "Setup completed! Please restart your terminal."
EOF

# Запустить скрипт
chmod +x ~/setup_system.sh
~/setup_system.sh
```

**Задание 49:** Диагностика и восстановление
```bash
# Создать точку восстановления с rsync
mkdir ~/system_backup
sudo rsync -av /etc/ ~/system_backup/etc_backup/

# Проверка целостности файловой системы
sudo fsck -n /dev/sda1  # Замените на актуальный раздел

# Восстановление загрузчика (симуляция)
# sudo grub-install /dev/sda
# sudo update-grub

# Анализ логов для поиска проблем
sudo journalctl -p err
sudo journalctl -p crit
sudo dmesg | grep -i error

# Проверка оборудования
sudo memtest86+  # Тест памяти (при перезагрузке)
sudo badblocks -sv /dev/sda  # Проверка плохих блоков (осторожно!)

# Мониторинг системы в реальном времени
watch -n 1 'cat /proc/meminfo | head -10'
watch -n 1 'df -h'
```

**Задание 50:** Итоговый проект - создание системы мониторинга
```bash
# Создать веб-интерфейс для мониторинга системы
mkdir ~/monitoring_project
cd ~/monitoring_project

# Создать HTML страницу
cat << 'EOF' > index.html
<!DOCTYPE html>
<html>
<head>
    <title>Linux Mint System Monitor</title>
    <meta http-equiv="refresh" content="30">
    <style>
        body { font-family: Arial, sans-serif; margin: 40px; }
        .metric { background: #f0f0f0; padding: 10px; margin: 10px 0; border-radius: 5px; }
        .warning { background: #ffcccc; }
        .ok { background: #ccffcc; }
    </style>
</head>
<body>
    <h1>System Monitor Dashboard</h1>
    <div id="content">Loading...</div>
    
    <script>
        function loadSystemInfo() {
            fetch('system_info.json')
                .then(response => response.json())
                .then(data => {
                    document.getElementById('content').innerHTML = `
                        <div class="metric">
                            <h3>Uptime</h3>
                            <p>${data.uptime}</p>
                        </div>
                        <div class="metric ${data.disk_usage > 80 ? 'warning' : 'ok'}">
                            <h3>Disk Usage</h3>
                            <p>${data.disk_usage}%</p>
                        </div>
                        <div class="metric ${data.memory_usage > 80 ? 'warning' : 'ok'}">
                            <h3>Memory Usage</h3>
                            <p>${data.memory_usage}%</p>
                        </div>
                        <div class="metric">
                            <h3>Load Average</h3>
                            <p>${data.load_average}</p>
                        </div>
                        <div class="metric">
                            <h3>Last Update</h3>
                            <p>${data.timestamp}</p>
                        </div>
                    `;
                });
        }
        
        loadSystemInfo();
        setInterval(loadSystemInfo, 30000);
    </script>
</body>
</html>
EOF

# Создать скрипт сбора данных
cat << 'EOF' > collect_data.sh
#!/bin/bash

# Сбор системной информации в JSON формате
UPTIME=$(uptime -p)
DISK_USAGE=$(df -h / | awk 'NR==2 {print $5}' | sed 's/%//')
MEMORY_USAGE=$(free | awk 'FNR==2{printf "%.0f", $3/$2*100}')
LOAD_AVERAGE=$(uptime | awk -F'load average:' '{print $2}' | xargs)
TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')

cat << JSON > system_info.json
{
    "uptime": "$UPTIME",
    "disk_usage": $DISK_USAGE,
    "memory_usage": $MEMORY_USAGE,
    "load_average": "$LOAD_AVERAGE",
    "timestamp": "$TIMESTAMP"
}
JSON
EOF

chmod +x collect_data.sh

# Создать cron задачу для обновления данных каждую минуту
echo "* * * * * cd /home/student/monitoring_project && ./collect_data.sh" | crontab -

# Запустить веб-сервер Python
python3 -m http.server 8000

# Открыть в браузере http://localhost:8000
```

## Заключение

После выполнения всех заданий студенты должны:

1. **Понимать основы Linux**: файловая система, права доступа, процессы
2. **Владеть командной строкой**: основные команды, перенаправление, каналы
3. **Уметь администрировать систему**: пользователи, службы, сеть
4. **Знать инструменты мониторинга**: процессы, ресурсы, логи
5. **Иметь опыт автоматизации**: скрипты, cron, systemd

### Критерии оценки:
- **Отлично (5)**: выполнено 90-100% заданий с правильной документацией
- **Хорошо (4)**: выполнено 70-89% заданий
- **Удовлетворительно (3)**: выполнено 50-69% заданий
- **Неудовлетворительно (2)**: выполнено менее 50% заданий

### Дополнительные ресурсы:
- Официальная документация Linux Mint: https://linuxmint.com/documentation.php
- Руководство по командам Linux: https://man7.org/linux/man-pages/
- Учебник по bash: https://www.gnu.org/software/bash/manual/
- Форум Linux Mint: https://forums.linuxmint.com/

**Удачи в изучении Linux Mint!**