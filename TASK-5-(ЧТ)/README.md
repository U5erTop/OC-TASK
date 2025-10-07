# Установка Ubuntu на виртуальную машину

## Оглавление
1. [Введение](#введение)
2. [Системные требования](#системные-требования)
3. [Подготовка](#подготовка)
4. [Установка VirtualBox](#установка-virtualbox)
5. [Создание виртуальной машины](#создание-виртуальной-машины)
6. [Установка Ubuntu](#установка-ubuntu)
7. [Первоначальная настройка](#первоначальная-настройка)
8. [Практические задания](#практические-задания)

## Введение

Ubuntu — это популярный дистрибутив Linux, основанный на Debian, который отличается стабильностью, регулярными обновлениями и большим сообществом пользователей. Установка на виртуальную машину позволяет изучать операционную систему без влияния на основную систему.

**Цели работы:**
- Изучить процесс установки операционной системы Ubuntu
- Освоить работу с виртуальными машинами и их настройкой
- Получить практические навыки работы в Ubuntu
- Изучить основные команды, snap-пакеты и возможности системы
- Освоить Docker и контейнеризацию приложений

## Системные требования

### Для хост-системы (компьютер):
- Процессор с поддержкой виртуализации (Intel VT-x или AMD-V)
- ОЗУ: минимум 4 ГБ (рекомендуется 8 ГБ и более)
- Свободное место на диске: минимум 35 ГБ
- Операционная система: Windows 10/11, macOS или Linux

### Для виртуальной машины Ubuntu:
- ОЗУ: 4-6 ГБ (рекомендуется 6 ГБ для комфортной работы)
- Жесткий диск: 25-35 ГБ
- Видеопамять: 128 МБ
- Процессор: 2-4 ядра

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
2. **Ubuntu ISO**: скачайте с https://ubuntu.com/download/desktop
   - Рекомендуется версия Ubuntu 24.04 LTS (64-bit)
   - Размер файла: ~4-5 ГБ

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
   - **Имя**: Ubuntu 24.04
   - **Папка машины**: оставьте по умолчанию или выберите другую
   - **Тип**: Linux
   - **Версия**: Ubuntu (64-bit)

### Шаг 2: Настройка параметров ВМ
1. **Объем памяти**: 
   - Минимум: 4096 МБ (4 ГБ)
   - Рекомендуется: 6144 МБ (6 ГБ)

2. **Жесткий диск**:
   - Выберите "Создать новый виртуальный жесткий диск"
   - Тип файла: VDI (VirtualBox Disk Image)
   - Формат хранения: Динамический виртуальный жесткий диск
   - Размер: 30-35 ГБ

### Шаг 3: Дополнительные настройки
1. Выберите созданную ВМ и нажмите **"Настроить"**
2. **Система**:
   - Процессор: 2-4 ядра (если доступно)
   - Включить PAE/NX
   - Включить аппаратную виртуализацию
3. **Дисплей**:
   - Видеопамять: 128 МБ
   - Включить 3D-ускорение
4. **Носители**:
   - Подключить ISO-образ Ubuntu к CD/DVD приводу
   - Контроллер IDE → Пустой → Выбрать файл диска → Выбрать ISO-образ

## Установка Ubuntu

### Шаг 1: Запуск виртуальной машины
1. Выберите ВМ "Ubuntu 24.04" и нажмите **"Запустить"**
2. ВМ загрузится с ISO-образа
3. Дождитесь загрузки установщика Ubuntu

### Шаг 2: Начальная настройка
1. **Выбор языка**: выберите "Русский" или "English"
2. **Обновления и другое ПО**:
   - Выберите "Обычная установка"
   - Установите галочку "Загружать обновления при установке Ubuntu"
   - Установите галочку "Установить стороннее программное обеспечение"

### Шаг 3: Процесс установки
1. **Тип установки**:
   - Выберите "Стереть диск и установить Ubuntu"
   - Нажмите "Установить сейчас"
   - Подтвердите "Продолжить"

2. **Часовой пояс**:
   - Выберите ваш регион на карте
   - Нажмите "Продолжить"

3. **Раскладка клавиатуры**:
   - Выберите "Russian" или оставьте "English (US)"
   - Протестируйте в поле ввода
   - Нажмите "Продолжить"

4. **Создание пользователя**:
   - Ваше имя: введите полное имя
   - Имя компьютера: ubuntu-vm
   - Имя пользователя: student
   - Пароль: создайте надежный пароль
   - Подтверждение пароля: повторите пароль
   - Выберите "Требовать пароль для входа в систему"
   - Нажмите "Продолжить"

### Шаг 4: Завершение установки
1. Дождитесь завершения копирования файлов (15-20 минут)
2. Нажмите "Перезагрузить"
3. Извлеките ISO-образ из виртуального привода
4. Нажмите Enter для перезагрузки

## Первоначальная настройка

### Шаг 1: Первый запуск
1. После загрузки войдите в систему
2. Пропустите подключение к Ubuntu One (если предлагается)
3. Пропустите или настройте Livepatch

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
2. В Ubuntu откроется окно с CD
3. Выберите "Запустить программное обеспечение" или откройте терминал:
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
3. В Ubuntu папка будет доступна в /media/sf_имя_папки

## Практические задания

### Блок 1: Основы системы и интерфейс (Задания 1-10)

**Задание 1:** Знакомство с Unity/GNOME
- Изучите док-панель и главное меню Activities
- Найдите и запустите приложения через поиск
- Настройте горячие клавиши (Super для открытия меню)
- Переключите между рабочими столами (Ctrl+Alt+Up/Down)
- Создайте новый рабочий стол

**Задание 2:** Настройка внешнего вида системы
- Откройте "Настройки" → "Внешний вид"
- Измените тему оформления (светлая/темная)
- Настройте обои рабочего стола
- Измените размер док-панели
- Настройте автоскрытие док-панели

**Задание 3:** Работа с файловым менеджером Nautilus
- Откройте файловый менеджер
- Создайте новую папку на рабочем столе
- Измените представление файлов (список/значки)
- Настройте закладки для быстрого доступа
- Изучите свойства файлов и папок

**Задание 4:** Первое знакомство с терминалом
```bash
# Открыть терминал (Ctrl+Alt+T)
# Узнать информацию о системе
lsb_release -a
hostnamectl

# Узнать имя пользователя и дату
whoami
date
id

# Создать новый терминал в новой вкладке
# Ctrl+Shift+T
```

**Задание 5:** Настройка сетевых подключений
- Откройте "Настройки" → "Сеть"
- Изучите настройки сетевого адаптера
- Проверьте IP-адрес через терминал:
```bash
ip addr show
ping -c 4 8.8.8.8
```

**Задание 6:** Управление учетными записями
- Откройте "Настройки" → "Пользователи"
- Измените фотографию профиля
- Измените пароль пользователя
- Изучите настройки автоматического входа

**Задание 7:** Работа с программным центром
- Откройте Ubuntu Software (Программы для Ubuntu)
- Найдите и установите простое приложение (например, Calculator)
- Просмотрите список установленных приложений
- Обновите приложения через Software Center

**Задание 8:** Настройка времени и языка
- Откройте "Настройки" → "Регион и язык"
- Добавьте русскую раскладку клавиатуры
- Настройте переключение раскладки (Alt+Shift)
- Измените формат времени и даты

**Задание 9:** Установка мультимедиа кодеков
```bash
# Установка дополнительных кодеков
sudo apt install ubuntu-restricted-extras

# Установка мультимедиа проигрывателя
sudo apt install vlc

# Проверка воспроизведения аудио/видео
vlc
```

**Задание 10:** Работа с системным монитором
- Откройте "Системный монитор" через меню
- Изучите вкладку "Процессы"
- Найдите процесс терминала
- Проверьте использование ресурсов (CPU, память, диск)
- Завершите ненужный процесс

### Блок 2: Командная строка и файловая система (Задания 11-20)

**Задание 11:** Навигация по файловой системе
```bash
# Определить текущую директорию
pwd

# Перейти в различные системные папки
cd /
ls -la
cd /home
cd /etc
cd /var/log

# Использовать автодополнение Tab
cd /u[Tab]
cd /usr/s[Tab]
```

**Задание 12:** Создание и управление файлами
```bash
# Создать рабочую папку в домашней директории
mkdir ~/ubuntu_practice
cd ~/ubuntu_practice

# Создать различные типы файлов
touch readme.txt
echo "Ubuntu 24.04 Practice" > info.txt
cat > description.txt << EOF
This is a practice file
Created during Ubuntu learning
Date: $(date)
EOF

# Просмотреть созданные файлы
ls -la
file *
```

**Задание 13:** Работа с текстовыми редакторами
```bash
# Редактирование в nano
nano practice_nano.txt
# Введите информацию о себе, сохраните (Ctrl+O), выйдите (Ctrl+X)

# Редактирование в vim
vim practice_vim.txt
# Нажмите 'i' для режима вставки
# Введите текст, нажмите Esc, затем :wq для сохранения

# Просмотр файлов
cat practice_nano.txt
less practice_vim.txt
```

**Задание 14:** Поиск файлов и содержимого
```bash
# Найти файлы по имени
find ~ -name "*.txt"
find /etc -name "*.conf" 2>/dev/null | head -10

# Поиск по содержимому
grep -r "Ubuntu" ~/ubuntu_practice/
grep -n "practice" *.txt

# Использование locate (после обновления базы)
sudo updatedb
locate firefox
```

**Задание 15:** Архивация и сжатие
```bash
# Создать тестовые файлы
echo "File 1 content" > file1.txt
echo "File 2 content" > file2.txt
echo "File 3 content" > file3.txt

# Создать tar архив
tar -cvf practice_archive.tar *.txt

# Создать сжатый архив
tar -czf practice_archive.tar.gz *.txt

# Создать zip архив
zip practice_files.zip *.txt

# Просмотреть содержимое архивов
tar -tvf practice_archive.tar
unzip -l practice_files.zip
```

**Задание 16:** Мониторинг системных процессов
```bash
# Просмотр процессов
ps aux
ps aux | grep firefox

# Интерактивный мониторинг
top
htop  # если установлен

# Информация о системе
lscpu
free -h
df -h
lsblk

# Информация о памяти
cat /proc/meminfo | head -10
```

**Задание 17:** Работа с переменными окружения
```bash
# Просмотр переменных окружения
env
echo $HOME
echo $USER
echo $PATH
echo $SHELL

# Создание собственных переменных
export PRACTICE_VAR="Ubuntu Learning"
echo $PRACTICE_VAR

# Добавление в PATH
export PATH=$PATH:~/ubuntu_practice
echo $PATH

# Постоянные переменные в .bashrc
echo 'export MY_UBUNTU_VAR="Persistent Variable"' >> ~/.bashrc
```

**Задание 18:** Управление правами доступа
```bash
# Создать файлы для тестирования прав
touch test_permissions.txt
mkdir test_directory

# Просмотреть текущие права
ls -la test_permissions.txt
ls -ld test_directory

# Изменить права различными способами
chmod 755 test_permissions.txt
chmod u+x,g+w,o-r test_permissions.txt
chmod 644 test_permissions.txt

# Изменить владельца (требует sudo)
sudo chown root:root test_permissions.txt
sudo chown student:student test_permissions.txt
```

**Задание 19:** Перенаправление и каналы
```bash
# Перенаправление вывода
ls -la > directory_listing.txt
date >> directory_listing.txt

# Перенаправление ошибок
ls /non_existent_directory 2> errors.txt
ls /non_existent_directory > output.txt 2>&1

# Использование каналов
ps aux | grep bash
ls -la | grep "txt"
cat /etc/passwd | cut -d: -f1 | sort
history | tail -20 | grep "ls"
```

**Задание 20:** Планирование задач с crontab
```bash
# Просмотреть текущие задачи cron
crontab -l

# Создать простой скрипт для автоматизации
cat > ~/backup_script.sh << 'EOF'
#!/bin/bash
DATE=$(date +%Y%m%d_%H%M%S)
tar -czf /tmp/home_backup_$DATE.tar.gz ~/ubuntu_practice/
echo "Backup created at $(date)" >> ~/backup_log.txt
EOF

chmod +x ~/backup_script.sh

# Настроить cron задачу
crontab -e
# Добавить строку: */5 * * * * /home/student/backup_script.sh
```

### Блок 3: Snap-пакеты и управление программным обеспечением (Задания 21-30)

**Задание 21:** Основы работы со snap-пакетами
```bash
# Проверить версию snap
snap version

# Просмотреть установленные snap-пакеты
snap list

# Найти доступные пакеты
snap find "text editor"
snap find code

# Получить информацию о пакете
snap info code
```

**Задание 22:** Установка приложений через snap
```bash
# Установить Visual Studio Code
sudo snap install code --classic

# Установить Discord
sudo snap install discord

# Установить медиаплеер
sudo snap install vlc

# Проверить установленные пакеты
snap list | grep -E "(code|discord|vlc)"
```

**Задание 23:** Управление snap-пакетами
```bash
# Обновить все snap-пакеты
sudo snap refresh

# Обновить конкретный пакет
sudo snap refresh code

# Посмотреть историю изменений
snap changes

# Временно отключить пакет
sudo snap disable discord
snap list | grep discord

# Включить обратно
sudo snap enable discord
```

**Задание 24:** Откат версий snap-пакетов
```bash
# Посмотреть все версии установленных пакетов
snap list --all

# Откатить пакет к предыдущей версии
sudo snap revert vlc

# Посмотреть информацию о версиях
snap info vlc

# Установить конкретную версию (если доступно)
# sudo snap install vlc --channel=stable
```

**Задание 25:** Работа с традиционными пакетами APT
```bash
# Обновить список пакетов
sudo apt update

# Найти пакеты
apt search "media player"
apt search git

# Установить пакеты
sudo apt install git curl wget tree

# Посмотреть информацию о пакете
apt show git

# Удалить пакет
sudo apt remove tree
sudo apt autoremove
```

**Задание 26:** Установка deb-пакетов
```bash
# Скачать deb-пакет (пример)
wget -O /tmp/google-chrome.deb https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

# Установить deb-пакет
sudo dpkg -i /tmp/google-chrome.deb

# Исправить зависимости, если есть проблемы
sudo apt install -f

# Проверить установку
dpkg -l | grep chrome
```

**Задание 27:** Управление репозиториями
```bash
# Просмотреть список репозиториев
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/

# Добавить новый репозиторий (пример с Node.js)
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install -y nodejs

# Проверить установку
node --version
npm --version
```

**Задание 28:** Работа с Flatpak (альтернатива Snap)
```bash
# Установить Flatpak
sudo apt install flatpak

# Добавить репозиторий Flathub
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

# Найти и установить приложение
flatpak search gimp
flatpak install flathub org.gimp.GIMP

# Запустить Flatpak приложение
flatpak run org.gimp.GIMP
```

**Задание 29:** Компиляция из исходного кода
```bash
# Установить необходимые инструменты для компиляции
sudo apt install build-essential cmake git

# Клонировать простой проект с GitHub
git clone https://github.com/htop-dev/htop.git
cd htop

# Подготовить к сборке
./autogen.sh
./configure

# Скомпилировать
make

# Установить (опционально)
sudo make install

# Проверить работу
htop --version
```

**Задание 30:** Анализ производительности пакетных менеджеров
```bash
# Сравнить время установки одинакового ПО разными способами
time sudo apt install firefox-esr
sudo apt remove firefox-esr

time sudo snap install firefox
sudo snap remove firefox

# Посмотреть размер установленных пакетов
snap list | awk '{print $1, $4}'
dpkg-query -W -f='${Installed-Size} ${Package}\n' | sort -n | tail -10

# Анализ использования дискового пространства
du -sh /snap/*
du -sh /var/lib/snapd/
```

### Блок 4: Docker и контейнеризация (Задания 31-40)

**Задание 31:** Установка и настройка Docker
```bash
# Обновить систему
sudo apt update

# Установить необходимые пакеты
sudo apt install apt-transport-https ca-certificates curl gnupg lsb-release

# Добавить GPG ключ Docker
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Добавить репозиторий Docker
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Установить Docker
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io

# Добавить пользователя в группу docker
sudo usermod -aG docker $USER
```

**Задание 32:** Основы работы с Docker
```bash
# После перезахода в систему проверить Docker
docker --version
docker info

# Запустить тестовый контейнер
docker run hello-world

# Посмотреть запущенные контейнеры
docker ps
docker ps -a

# Посмотреть образы
docker images
```

**Задание 33:** Работа с образами Ubuntu в Docker
```bash
# Скачать образ Ubuntu
docker pull ubuntu:latest
docker pull ubuntu:20.04

# Запустить интерактивный контейнер Ubuntu
docker run -it ubuntu:latest /bin/bash

# Внутри контейнера выполнить команды:
apt update
apt install nano htop
echo "Hello from Docker Ubuntu!" > /tmp/docker_test.txt
cat /tmp/docker_test.txt
exit

# Посмотреть остановленные контейнеры
docker ps -a
```

**Задание 34:** Создание и управление контейнерами
```bash
# Запустить контейнер с именем
docker run -it --name my-ubuntu ubuntu:latest

# В другом терминале посмотреть запущенные контейнеры
docker ps

# Выполнить команду в запущенном контейнере
docker exec -it my-ubuntu /bin/bash

# Остановить контейнер
docker stop my-ubuntu

# Запустить остановленный контейнер
docker start my-ubuntu
docker attach my-ubuntu
```

**Задание 35:** Создание собственного образа
```bash
# Создать Dockerfile
mkdir ~/docker-practice
cd ~/docker-practice

cat > Dockerfile << 'EOF'
FROM ubuntu:latest

# Обновить пакеты и установить необходимое ПО
RUN apt-get update && apt-get install -y \
    curl \
    vim \
    htop \
    git \
    && rm -rf /var/lib/apt/lists/*

# Создать рабочую директорию
WORKDIR /app

# Создать пользователя
RUN useradd -m -s /bin/bash dockeruser

# Переключиться на пользователя
USER dockeruser

# Команда по умолчанию
CMD ["/bin/bash"]
EOF

# Собрать образ
docker build -t my-ubuntu-custom .

# Запустить контейнер из собственного образа
docker run -it my-ubuntu-custom
```

**Задание 36:** Работа с томами Docker
```bash
# Создать именованный том
docker volume create my-data-volume

# Запустить контейнер с подключенным томом
docker run -it --name volume-test -v my-data-volume:/data ubuntu:latest

# Внутри контейнера создать файл в томе
echo "Persistent data in Docker volume" > /data/persistent.txt
cat /data/persistent.txt
exit

# Удалить контейнер
docker rm volume-test

# Создать новый контейнер с тем же томом
docker run -it --name volume-test2 -v my-data-volume:/data ubuntu:latest
cat /data/persistent.txt  # Файл должен сохраниться
```

**Задание 37:** Сетевое взаимодействие Docker
```bash
# Посмотреть сети Docker
docker network ls

# Создать пользовательскую сеть
docker network create my-network

# Запустить два контейнера в одной сети
docker run -it -d --name container1 --network my-network ubuntu:latest
docker run -it -d --name container2 --network my-network ubuntu:latest

# Проверить взаимодействие между контейнерами
docker exec -it container1 apt-get update && apt-get install -y iputils-ping
docker exec -it container1 ping container2

# Посмотреть информацию о сети
docker network inspect my-network
```

**Задание 38:** Docker Compose - управление многоконтейнерными приложениями
```bash
# Установить Docker Compose
sudo apt install docker-compose

# Создать файл docker-compose.yml
cat > docker-compose.yml << 'EOF'
version: '3.8'

services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
  
  database:
    image: postgres:13
    environment:
      POSTGRES_DB: testdb
      POSTGRES_USER: testuser
      POSTGRES_PASSWORD: testpass
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
EOF

# Создать простую HTML страницу
mkdir html
echo "<h1>Hello from Docker Compose!</h1>" > html/index.html

# Запустить службы
docker-compose up -d

# Проверить работу в браузере: http://localhost:8080
firefox http://localhost:8080

# Посмотреть логи
docker-compose logs

# Остановить службы
docker-compose down
```

**Задание 39:** Мониторинг Docker контейнеров
```bash
# Запустить контейнер с ограничениями ресурсов
docker run -it -d --name resource-test --memory="512m" --cpus="1.0" ubuntu:latest

# Посмотреть статистику использования ресурсов
docker stats resource-test

# Посмотреть детальную информацию о контейнере
docker inspect resource-test

# Посмотреть логи контейнера
docker logs resource-test

# Посмотреть процессы внутри контейнера
docker top resource-test
```

**Задание 40:** Очистка Docker системы
```bash
# Посмотреть использование диска Docker
docker system df

# Очистить неиспользуемые контейнеры
docker container prune

# Очистить неиспользуемые образы
docker image prune

# Очистить неиспользуемые тома
docker volume prune

# Очистить неиспользуемые сети
docker network prune

# Полная очистка системы (осторожно!)
docker system prune -a

# Посмотреть, сколько места освободилось
docker system df
```

### Блок 5: Системное администрирование и автоматизация (Задания 41-50)

**Задание 41:** Управление службами systemd
```bash
# Посмотреть статус всех служб
systemctl list-units --type=service

# Посмотреть статус конкретной службы
systemctl status ssh
systemctl status docker

# Управление службами
sudo systemctl start ssh
sudo systemctl stop ssh
sudo systemctl restart ssh
sudo systemctl reload ssh

# Автозапуск служб
sudo systemctl enable ssh
sudo systemctl disable ssh

# Посмотреть логи службы
journalctl -u ssh
journalctl -u docker --since "1 hour ago"
```

**Задание 42:** Настройка SSH-сервера
```bash
# Установить SSH-сервер (если не установлен)
sudo apt install openssh-server

# Настроить SSH
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup
sudo nano /etc/ssh/sshd_config

# Изменить настройки:
# Port 2222
# PermitRootLogin no
# PasswordAuthentication yes

# Перезапустить службу SSH
sudo systemctl restart ssh

# Проверить подключение
ssh student@localhost -p 2222

# Создать SSH ключи
ssh-keygen -t rsa -b 4096 -C "student@ubuntu-vm"
```

**Задание 43:** Мониторинг системы и логов
```bash
# Установить дополнительные утилиты мониторинга
sudo apt install htop iotop nethogs sysstat

# Мониторинг процессов в реальном времени
htop

# Мониторинг дисковой активности
sudo iotop

# Мониторинг сетевой активности
sudo nethogs

# Статистика системы
sar 1 5  # Статистика каждую секунду, 5 раз
iostat 1 5

# Анализ логов
sudo journalctl --since "1 hour ago"
sudo journalctl -p err
sudo tail -f /var/log/syslog
```

**Задание 44:** Управление пользователями и группами
```bash
# Создать нового пользователя
sudo useradd -m -s /bin/bash testuser
sudo passwd testuser

# Создать группу
sudo groupadd developers
sudo groupadd admins

# Добавить пользователя в группы
sudo usermod -aG developers testuser
sudo usermod -aG sudo testuser

# Посмотреть информацию о пользователе
id testuser
groups testuser

# Переключиться на пользователя
su - testuser

# Удалить пользователя
sudo userdel -r testuser
sudo groupdel developers
```

**Задание 45:** Настройка файрвола UFW
```bash
# Установить UFW (если не установлен)
sudo apt install ufw

# Посмотреть статус
sudo ufw status

# Включить файрвол
sudo ufw enable

# Разрешить SSH
sudo ufw allow ssh
sudo ufw allow 2222

# Разрешить HTTP и HTTPS
sudo ufw allow 80
sudo ufw allow 443

# Заблокировать порт
sudo ufw deny 23

# Разрешить доступ с определенного IP
sudo ufw allow from 192.168.1.100

# Посмотреть правила с номерами
sudo ufw status numbered

# Удалить правило
sudo ufw delete 3
```

**Задание 46:** Резервное копирование с rsync
```bash
# Создать тестовые данные для бэкапа
mkdir -p ~/important_data/documents
mkdir -p ~/important_data/projects

echo "Important document 1" > ~/important_data/documents/doc1.txt
echo "Important document 2" > ~/important_data/documents/doc2.txt
echo "Project file" > ~/important_data/projects/project1.txt

# Простое копирование с rsync
rsync -av ~/important_data/ ~/backup_local/

# Синхронизация с удалением лишних файлов
rsync -av --delete ~/important_data/ ~/backup_sync/

# Бэкап с исключениями
rsync -av --exclude='*.tmp' --exclude='cache/' ~/important_data/ ~/backup_filtered/

# Создать скрипт автоматического бэкапа
cat > ~/backup_script.sh << 'EOF'
#!/bin/bash
BACKUP_DATE=$(date +%Y%m%d_%H%M%S)
BACKUP_DIR="/tmp/backup_$BACKUP_DATE"

mkdir -p "$BACKUP_DIR"
rsync -av ~/important_data/ "$BACKUP_DIR/"
tar -czf "/tmp/backup_$BACKUP_DATE.tar.gz" -C /tmp "backup_$BACKUP_DATE"
rm -rf "$BACKUP_DIR"

echo "Backup completed: backup_$BACKUP_DATE.tar.gz"
EOF

chmod +x ~/backup_script.sh
~/backup_script.sh
```

**Задание 47:** Автоматизация задач с Bash скриптами
```bash
# Создать скрипт системной информации
cat > ~/system_report.sh << 'EOF'
#!/bin/bash

echo "=== SYSTEM REPORT ==="
echo "Generated on: $(date)"
echo ""

echo "=== SYSTEM INFO ==="
hostnamectl | grep -E "(Operating System|Kernel|Architecture)"
echo "Uptime: $(uptime -p)"
echo ""

echo "=== DISK USAGE ==="
df -h | grep -v "tmpfs"
echo ""

echo "=== MEMORY USAGE ==="
free -h
echo ""

echo "=== TOP 5 PROCESSES BY CPU ==="
ps aux --sort=-%cpu | head -6
echo ""

echo "=== NETWORK INTERFACES ==="
ip -4 addr show | grep -E "(inet|^[0-9])"
echo ""

echo "=== LAST 5 LOGINS ==="
last -5
EOF

chmod +x ~/system_report.sh
~/system_report.sh > ~/system_report_$(date +%Y%m%d).txt
```

**Задание 48:** Настройка веб-сервера Nginx
```bash
# Установить Nginx
sudo apt install nginx

# Запустить и включить автозапуск
sudo systemctl start nginx
sudo systemctl enable nginx

# Создать простой сайт
sudo mkdir -p /var/www/mysite
sudo chown $USER:$USER /var/www/mysite

cat > /var/www/mysite/index.html << 'EOF'
<!DOCTYPE html>
<html>
<head>
    <title>My Ubuntu Website</title>
</head>
<body>
    <h1>Welcome to My Ubuntu Server!</h1>
    <p>This site is running on Ubuntu with Nginx</p>
    <p>Server time: <script>document.write(new Date());</script></p>
</body>
</html>
EOF

# Создать конфигурацию сайта
sudo tee /etc/nginx/sites-available/mysite << 'EOF'
server {
    listen 8080;
    server_name localhost;
    
    root /var/www/mysite;
    index index.html;
    
    location / {
        try_files $uri $uri/ =404;
    }
}
EOF

# Активировать сайт
sudo ln -s /etc/nginx/sites-available/mysite /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx

# Проверить в браузере: http://localhost:8080
```

**Задание 49:** Мониторинг производительности и оптимизация
```bash
# Анализ времени загрузки системы
systemd-analyze
systemd-analyze blame
systemd-analyze critical-chain

# Оптимизация swap
cat /proc/sys/vm/swappiness
echo 'vm.swappiness=10' | sudo tee -a /etc/sysctl.conf

# Очистка системы
sudo apt autoremove
sudo apt autoclean
sudo journalctl --vacuum-time=7d

# Анализ использования дискового пространства
sudo du -sh /* 2>/dev/null | sort -hr | head -10
ncdu ~/  # если установлен

# Мониторинг температуры (если доступно)
sensors
```

**Задание 50:** Создание комплексной системы мониторинга
```bash
# Создать директорию для системы мониторинга
mkdir ~/monitoring_system
cd ~/monitoring_system

# Создать скрипт сбора метрик
cat > collect_metrics.sh << 'EOF'
#!/bin/bash

METRICS_DIR="$HOME/monitoring_system/metrics"
mkdir -p "$METRICS_DIR"
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

# Системные метрики
{
    echo "timestamp:$TIMESTAMP"
    echo "uptime:$(cat /proc/uptime | cut -d' ' -f1)"
    echo "load_avg:$(cat /proc/loadavg | cut -d' ' -f1-3)"
    echo "cpu_usage:$(top -bn1 | grep "Cpu(s)" | awk '{print $2}' | cut -d'%' -f1)"
    echo "memory_usage:$(free | awk 'FNR==2{printf "%.2f", $3/$2*100}')"
    echo "disk_usage:$(df -h / | awk 'FNR==2{print $5}' | sed 's/%//')"
    echo "network_rx:$(cat /proc/net/dev | grep 'eth0\|enp' | head -1 | awk '{print $2}')"
    echo "network_tx:$(cat /proc/net/dev | grep 'eth0\|enp' | head -1 | awk '{print $10}')"
} > "$METRICS_DIR/metrics_$TIMESTAMP.txt"
EOF

chmod +x collect_metrics.sh

# Создать веб-интерфейс для мониторинга
cat > index.html << 'EOF'
<!DOCTYPE html>
<html>
<head>
    <title>Ubuntu System Monitor</title>
    <meta http-equiv="refresh" content="10">
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; background: #f5f5f5; }
        .container { max-width: 1200px; margin: 0 auto; }
        .metric-card { background: white; margin: 10px; padding: 20px; border-radius: 8px; box-shadow: 0 2px 4px rgba(0,0,0,0.1); }
        .metric-value { font-size: 2em; font-weight: bold; color: #333; }
        .metric-label { color: #666; margin-bottom: 10px; }
        .warning { border-left: 5px solid #ff9800; }
        .critical { border-left: 5px solid #f44336; }
        .normal { border-left: 5px solid #4caf50; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Ubuntu System Monitor Dashboard</h1>
        <div id="metrics-container">
            <div class="metric-card normal">
                <div class="metric-label">System Uptime</div>
                <div class="metric-value" id="uptime">Loading...</div>
            </div>
            <div class="metric-card normal">
                <div class="metric-label">CPU Usage</div>
                <div class="metric-value" id="cpu">Loading...</div>
            </div>
            <div class="metric-card normal">
                <div class="metric-label">Memory Usage</div>
                <div class="metric-value" id="memory">Loading...</div>
            </div>
            <div class="metric-card normal">
                <div class="metric-label">Disk Usage</div>
                <div class="metric-value" id="disk">Loading...</div>
            </div>
        </div>
        <p><strong>Last Update:</strong> <span id="timestamp"></span></p>
    </div>

    <script>
        // Имитация загрузки данных (в реальном проекте здесь был бы AJAX)
        function updateMetrics() {
            document.getElementById('timestamp').textContent = new Date().toLocaleString();
            // В реальном проекте данные загружались бы с сервера
        }
        
        updateMetrics();
        setInterval(updateMetrics, 10000);
    </script>
</body>
</html>
EOF

# Создать задачу cron для регулярного сбора метрик
(crontab -l 2>/dev/null; echo "*/1 * * * * $HOME/monitoring_system/collect_metrics.sh") | crontab -

# Запустить простой веб-сервер для просмотра
python3 -m http.server 8000 &
echo "Monitoring dashboard available at: http://localhost:8000"

# Создать финальный отчет
cat > final_report.sh << 'EOF'
#!/bin/bash

echo "=== UBUNTU LEARNING COMPLETION REPORT ==="
echo "Generated on: $(date)"
echo "Student: $(whoami)"
echo "System: $(lsb_release -d | cut -f2)"
echo ""

echo "=== COMPLETED TASKS SUMMARY ==="
echo "✓ System installation and configuration"
echo "✓ File system navigation and management" 
echo "✓ User interface customization"
echo "✓ Command line proficiency"
echo "✓ Package management (APT, Snap, Flatpak)"
echo "✓ Docker containerization"
echo "✓ System administration"
echo "✓ Network configuration"
echo "✓ Monitoring and optimization"
echo "✓ Automation and scripting"
echo ""

echo "=== INSTALLED SOFTWARE ==="
echo "Snap packages:"
snap list | wc -l
echo "APT packages:"
dpkg -l | grep ^ii | wc -l
echo "Docker images:"
docker images | wc -l
echo ""

echo "=== SYSTEM HEALTH ==="
echo "Uptime: $(uptime -p)"
echo "Load: $(cat /proc/loadavg | cut -d' ' -f1)"
echo "Memory: $(free -h | awk 'FNR==2{printf "%s/%s (%.1f%%)", $3,$2,$3/$2*100}')"
echo "Disk: $(df -h / | awk 'FNR==2{printf "%s/%s (%s)", $3,$2,$5}')"
echo ""

echo "=== CONGRATULATIONS! ==="
echo "You have successfully completed the Ubuntu learning course!"
echo "You are now proficient in Ubuntu system administration."
EOF

chmod +x final_report.sh
./final_report.sh
```

## Заключение

После выполнения всех заданий студенты должны:

1. **Владеть основами Ubuntu**: интерфейс, настройки, файловая система
2. **Уметь работать в командной строке**: навигация, управление файлами, процессами
3. **Понимать управление пакетами**: APT, Snap, Flatpak, компиляция из исходников
4. **Знать основы Docker**: контейнеры, образы, тома, сети, Docker Compose
5. **Владеть системным администрированием**: пользователи, службы, мониторинг, автоматизация

### Критерии оценки:
- **Отлично (5)**: выполнено 90-100% заданий с пониманием принципов работы
- **Хорошо (4)**: выполнено 70-89% заданий
- **Удовлетворительно (3)**: выполнено 50-69% заданий
- **Неудовлетворительно (2)**: выполнено менее 50% заданий

### Дополнительные ресурсы:
- Официальная документация Ubuntu: https://help.ubuntu.com/
- Docker документация: https://docs.docker.com/
- Snap Store: https://snapcraft.io/
- Ubuntu Community: https://community.ubuntu.com/
- Ask Ubuntu: https://askubuntu.com/

**Успехов в изучении Ubuntu!**