# Установка Astra Linux на виртуальную машину

## Оглавление
1. [Введение](#введение)
2. [Системные требования](#системные-требования)
3. [Подготовка](#подготовка)
4. [Установка VirtualBox](#установка-virtualbox)
5. [Создание виртуальной машины](#создание-виртуальной-машины)
6. [Установка Astra Linux](#установка-astra-linux)
7. [Первоначальная настройка](#первоначальная-настройка)
8. [Практические задания](#практические-задания)

## Введение

Astra Linux — это российская операционная система специального назначения, основанная на Debian GNU/Linux, которая предназначена для защиты государственной тайны и конфиденциальной информации. Система имеет сертификаты соответствия требованиям безопасности информации ФСТЭК России и обеспечивает высокий уровень защиты данных.

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
2. **Astra Linux ISO**: получите образ операционной системы:
   - Astra Linux Special Edition (для максимальной защиты)
   - Astra Linux Common Edition (для ознакомления)
   - Рекомендуется версия 1.7 или 1.8
   - Размер файла: ~4-6 ГБ

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
   - **Имя**: Astra Linux SE
   - **Папка машины**: оставьте по умолчанию или выберите другую
   - **Тип**: Linux
   - **Версия**: Debian (64-bit)

### Шаг 2: Настройка параметров ВМ
1. **Объем памяти**: 
   - Минимум: 4096 МБ (4 ГБ)
   - Рекомендуется: 6144 МБ (6 ГБ)

2. **Жесткий диск**:
   - Выберите "Создать новый виртуальный жесткий диск"
   - Тип файла: VDI (VirtualBox Disk Image)
   - Формат хранения: Динамический виртуальный жесткий диск
   - Размер: 35-40 ГБ

### Шаг 3: Дополнительные настройки
1. Выберите созданную ВМ и нажмите **"Настроить"**
2. **Система**:
   - Процессор: 2-4 ядра (рекомендуется 4)
   - Включить PAE/NX
   - Включить аппаратную виртуализацию
3. **Дисплей**:
   - Видеопамять: 128 МБ
   - Включить 3D-ускорение
4. **Носители**:
   - Подключить ISO-образ Astra Linux к CD/DVD приводу
   - Контроллер IDE → Пустой → Выбрать файл диска → Выбрать ISO-образ

## Установка Astra Linux

### Шаг 1: Запуск виртуальной машины
1. Выберите ВМ "Astra Linux SE" и нажмите **"Запустить"**
2. ВМ загрузится с ISO-образа
3. Выберите способ установки (рекомендуется "Графическая установка")

### Шаг 2: Базовые настройки установки
1. **Выбор языка**: выберите "Русский"
2. **Выбор страны**: выберите "Российская Федерация"
3. **Раскладка клавиатуры**: выберите "Русская"
4. **Настройка сети**: 
   - Имя компьютера: astra-vm
   - Домен: оставьте пустым

### Шаг 3: Настройка пользователей
1. **Учетная запись администратора**:
   - Полное имя: Администратор системы
   - Имя пользователя: admin
   - Пароль: создайте надежный пароль (минимум 8 символов, цифры и буквы)
   - Подтверждение пароля

### Шаг 4: Разметка дисков
1. Выберите "Авто - использовать весь диск"
2. Выберите единственный диск
3. Подтвердите схему разметки
4. Применить изменения к дискам

### Шаг 5: Выбор компонентов системы
1. **Обязательные компоненты**:
   - Графический интерфейс Fly
   - Средства работы с Интернет
   - Консольные утилиты
2. **Дополнительные компоненты** (по желанию):
   - Офисные приложения
   - Средства разработки

### Шаг 6: Выбор уровня защищенности
**Важный этап!** Выберите уровень защищенности:
- **"Орел" (базовый)**: для обучения и тестирования
- **"Воронеж" (усиленный)**: для конфиденциальной информации
- **"Смоленск" (максимальный)**: для государственной тайны

Для обучения рекомендуется выбрать **"Орел"**.

### Шаг 7: Завершение установки
1. Дождитесь завершения копирования файлов (20-30 минут)
2. Нажмите "Продолжить" для перезагрузки
3. Извлеките ISO-образ из виртуального привода

## Первоначальная настройка

### Шаг 1: Первый запуск системы
1. После загрузки войдите в систему под созданным пользователем
2. Ознакомьтесь с рабочим столом Fly
3. Откройте "Справку" для изучения интерфейса

### Шаг 2: Обновление системы
Откройте терминал и выполните:
```bash
# Обновление списка пакетов
sudo apt update

# Обновление системы
sudo apt upgrade -y

# Перезагрузка
sudo reboot
```

### Шаг 3: Настройка сети и времени
```bash
# Проверка сетевого соединения
ping -c 4 ya.ru

# Синхронизация времени
sudo ntpdate pool.ntp.org

# Установка часового пояса
sudo dpkg-reconfigure tzdata
```

### Шаг 4: Проверка состояния КСЗ
```bash
# Проверка статуса подсистемы безопасности
sudo parsec-ls

# Проверка уровня защищенности
cat /etc/parsec.conf | grep level

# Просмотр текущих настроек безопасности
sudo fly-admin-smc --help
```

## Практические задания

### Блок 1: Знакомство с системой и интерфейсом Fly (Задания 1-10)

**Задание 1:** Изучение рабочего стола Fly
- Исследуйте главное меню (кнопка "Пуск")
- Найдите и запустите "Панель управления"
- Изучите раздел "Безопасность"
- Откройте "Терминал" и "Файловый менеджер"
- Настройте панель задач по своему усмотрению

**Задание 2:** Работа с системной информацией
```bash
# Узнать версию Astra Linux
cat /etc/astra_version

# Информация о системе
hostnamectl
uname -a

# Информация об уровне защищенности
sudo cat /etc/parsec.conf

# Статус КСЗ ПАРСЕК
sudo systemctl status parsec
```

**Задание 3:** Настройка пользовательского окружения
- Откройте "Пуск" → "Параметры" → "Рабочий стол"
- Измените обои рабочего стола
- Настройте хранитель экрана
- Измените тему оформления
- Настройте автоматический вход (НЕ рекомендуется в реальных условиях)

**Задание 4:** Работа с справочной системой
- Откройте "Пуск" → "Справка и поддержка"
- Изучите раздел "Безопасность"
- Найдите информацию о КСЗ ПАРСЕК
- Изучите руководство по мандатному управлению доступом
- Найдите контактную информацию технической поддержки

**Задание 5:** Основы командной строки Astra Linux
```bash
# Проверить текущего пользователя
whoami
id

# Проверить группы безопасности
groups
cat /etc/group | grep parsec

# Просмотреть системные службы
systemctl list-units --type=service | grep parsec

# Проверить логи безопасности
sudo journalctl -u parsec -n 10
```

**Задание 6:** Работа с файловым менеджером
- Откройте файловый менеджер
- Перейдите в каталог `/etc/parsec/`
- Изучите структуру конфигурационных файлов
- Просмотрите права доступа к файлам (не изменяйте!)
- Создайте тестовую папку в домашнем каталоге

**Задание 7:** Настройка сетевых параметров
- Откройте "Пуск" → "Параметры" → "Сеть"
- Проверьте настройки сетевого адаптера
- Настройте DNS-серверы (8.8.8.8, 1.1.1.1)
- Проверьте подключение к интернету
- Изучите настройки брандмауэра

**Задание 8:** Управление приложениями
```bash
# Просмотр установленных пакетов
dpkg -l | grep astra

# Поиск доступных программ
apt search editor

# Установка простого приложения
sudo apt install mc

# Запуск Midnight Commander
mc
```

**Задание 9:** Изучение журналов системы
```bash
# Системные логи
sudo tail -f /var/log/syslog

# Логи аутентификации
sudo tail -f /var/log/auth.log

# Логи безопасности ПАРСЕК
sudo tail -f /var/log/parsec.log

# Анализ загрузки системы
journalctl -b
```

**Задание 10:** Настройка языка и локализации
- Откройте "Пуск" → "Параметры" → "Язык и регион"
- Добавьте английскую раскладку клавиатуры
- Настройте переключение языков (Ctrl+Shift)
- Измените формат даты и времени
- Проверьте настройки кодировки

### Блок 2: Основы безопасности и КСЗ ПАРСЕК (Задания 11-20)

**Задание 11:** Изучение архитектуры КСЗ ПАРСЕК
```bash
# Просмотр компонентов ПАРСЕК
sudo dpkg -l | grep parsec

# Статус модулей безопасности
sudo lsmod | grep parsec

# Проверка целостности системы
sudo /usr/lib/parsec/tests/run.sh

# Просмотр конфигурации
sudo cat /etc/parsec.conf
```

**Задание 12:** Работа с графическим инструментом управления
- Откройте "Пуск" → "Панель управления" → "Безопасность" → "Политика безопасности"
- Изучите интерфейс fly-admin-smc
- Просмотрите разделы: "Пользователи", "Группы", "Мандатные атрибуты"
- Изучите настройки аудита
- **НЕ ИЗМЕНЯЙТЕ настройки без понимания последствий!**

**Задание 13:** Управление пользователями и группами безопасности
```bash
# Создание тестового пользователя
sudo useradd -m testuser
sudo passwd testuser

# Просмотр групп безопасности
cat /etc/group | grep astra

# Добавление в группу администраторов
sudo usermod -aG astra-admin testuser

# Проверка принадлежности к группам
id testuser

# Удаление тестового пользователя
sudo userdel -r testuser
```

**Задание 14:** Настройка аудита и протоколирования
```bash
# Проверка состояния аудита
sudo auditctl -s

# Просмотр правил аудита
sudo auditctl -l

# Анализ логов аудита
sudo ausearch -m LOGIN

# Настройка аудита файлов (пример)
sudo auditctl -w /etc/passwd -p wa -k passwd_changes

# Просмотр событий аудита
sudo tail -f /var/log/audit/audit.log
```

**Задание 15:** Проверка целостности системы
```bash
# Запуск проверки целостности
sudo /usr/lib/parsec/tests/run.sh -v

# Проверка подписей системных файлов
sudo find /usr/bin -name "*.signed" | head -10

# Верификация цифровых подписей
sudo parsec-integrity-check /usr/bin/ls

# Создание отчета о целостности
sudo fly-admin-int-check
```

**Задание 16:** Работа с мандатными атрибутами
```bash
# Просмотр уровней конфиденциальности
sudo pdp-ls-levels

# Просмотр категорий безопасности
sudo pdp-ls-categories

# Установка метки безопасности для файла
echo "Тестовые данные" > test_file.txt
sudo pdp-label test_file.txt 1:0

# Проверка метки файла
sudo pdp-ls test_file.txt
```

**Задание 17:** Настройка замкнутой программной среды (ЗПС)
- Откройте fly-admin-smc → "Замкнутая программная среда"
- Изучите текущий режим работы ЗПС
- Просмотрите список доверенных ключей
- Изучите настройки проверки цифровых подписей
- **Внимание**: изменение настроек ЗПС может заблокировать систему!

**Задание 18:** Мониторинг событий безопасности
```bash
# Мониторинг попыток аутентификации
sudo tail -f /var/log/auth.log

# Анализ нарушений безопасности
sudo grep DENIED /var/log/parsec.log

# Мониторинг доступа к файлам
sudo inotifywait -m /etc/passwd

# Статистика событий безопасности
sudo journalctl -u parsec --since "1 hour ago" | wc -l
```

**Задание 19:** Управление сертификатами и ключами
```bash
# Просмотр системных сертификатов
ls -la /etc/ssl/certs/ | head -10

# Проверка ключей ЗПС
sudo ls -la /etc/digsig/keys/

# Информация о сертификате
openssl x509 -in /etc/ssl/certs/ca-certificates.crt -text | head -20

# Генерация тестового ключа (не для production!)
openssl genrsa -out test_key.pem 2048
```

**Задание 20:** Резервное копирование конфигурации безопасности
```bash
# Создание резервной копии конфигурации ПАРСЕК
sudo tar -czf parsec_config_backup.tar.gz /etc/parsec/

# Создание списка установленных пакетов безопасности
dpkg -l | grep -E "(parsec|astra|fly)" > installed_security_packages.txt

# Экспорт настроек пользователей
sudo getent passwd > users_backup.txt
sudo getent group > groups_backup.txt

# Создание снимка системы
sudo rsync -av /etc/ ~/system_config_backup/
```

### Блок 3: Мандатное управление доступом (МРД) (Задания 21-30)

**Задание 21:** Основы мандатного контроля доступа
```bash
# Проверка текущего мандатного уровня пользователя
pdp-uselev

# Просмотр всех уровней конфиденциальности
sudo pdp-ls-levels

# Создание файла с меткой безопасности
echo "Секретная информация" > secret_file.txt
sudo pdp-label secret_file.txt 2:1,2

# Проверка метки файла
pdp-ls secret_file.txt
```

**Задание 22:** Работа с уровнями конфиденциальности
- Откройте fly-admin-smc → "Мандатные атрибуты" → "Уровни конфиденциальности"
- Изучите существующие уровни (0-3 по умолчанию)
- Просмотрите описания уровней
- Изучите принципы модели Bell-LaPadula
- Понимайте: "no read up, no write down"

**Задание 23:** Создание пользователей с мандатными атрибутами
```bash
# Создание пользователя с мандатными правами
sudo useradd -m user_level1
sudo passwd user_level1

# Установка мандатного уровня пользователю
sudo pdp-useradd user_level1 1:1 3:1,2,3

# Проверка мандатных атрибутов пользователя
sudo pdp-userlist user_level1

# Тестирование доступа
su - user_level1
pdp-uselev
```

**Задание 24:** Работа с категориями безопасности
```bash
# Просмотр категорий безопасности
sudo pdp-ls-categories

# Создание файлов с разными категориями
echo "Информация категории А" > file_cat_a.txt
sudo pdp-label file_cat_a.txt 1:1

echo "Информация категории Б" > file_cat_b.txt  
sudo pdp-label file_cat_b.txt 1:2

echo "Информация категорий А и Б" > file_cat_ab.txt
sudo pdp-label file_cat_ab.txt 1:1,2

# Проверка доступа к файлам с разными метками
pdp-ls file_cat_*.txt
```

**Задание 25:** Тестирование правил мандатного доступа
```bash
# Создание пользователей с разными уровнями доступа
sudo useradd -m user_low
sudo useradd -m user_high
sudo passwd user_low
sudo passwd user_high

# Назначение мандатных уровней
sudo pdp-useradd user_low 0:0 1:1
sudo pdp-useradd user_high 2:1,2 3:1,2,3

# Создание файлов с разными уровнями секретности
echo "Открытая информация" > open_info.txt
sudo pdp-label open_info.txt 0:0

echo "Секретная информация" > secret_info.txt
sudo pdp-label secret_info.txt 2:1,2

# Тестирование доступа от разных пользователей
sudo -u user_low cat open_info.txt
sudo -u user_low cat secret_info.txt # Должен быть запрещен доступ
```

**Задание 26:** Настройка мандатного контроля для каталогов
```bash
# Создание каталогов с мандатными метками
mkdir public_dir
mkdir secret_dir
mkdir top_secret_dir

# Установка меток на каталоги
sudo pdp-label public_dir 0:0
sudo pdp-label secret_dir 2:1
sudo pdp-label top_secret_dir 3:1,2,3

# Проверка меток каталогов
pdp-ls -d */

# Создание файлов в каталогах и проверка наследования меток
echo "Публичный файл" > public_dir/file1.txt
echo "Секретный файл" > secret_dir/file2.txt
pdp-ls public_dir/file1.txt secret_dir/file2.txt
```

**Задание 27:** Мандатное управление процессами
```bash
# Просмотр мандатных атрибутов процессов
ps -eo pid,comm,label

# Запуск процесса с определенным мандатным уровнем
sudo -u user_high bash -c "sleep 60 &"
ps -eo pid,comm,label | grep sleep

# Анализ мандатных ограничений для процессов
sudo pdp-ps

# Проверка возможности межпроцессного взаимодействия
# (процессы разных уровней не могут взаимодействовать)
```

**Задание 28:** Работа с мандатной файловой системой
```bash
# Создание тестовой структуры каталогов
mkdir -p /tmp/test_mac/{level0,level1,level2,level3}

# Установка мандатных меток на каталоги
for i in {0..3}; do
    sudo pdp-label /tmp/test_mac/level$i $i:$i
done

# Проверка меток
pdp-ls -d /tmp/test_mac/level*

# Тестирование записи файлов пользователями разных уровней
sudo -u user_low echo "Low level data" > /tmp/test_mac/level0/data.txt
sudo -u user_high echo "High level data" > /tmp/test_mac/level2/data.txt

# Проверка возможности чтения
sudo -u user_low cat /tmp/test_mac/level2/data.txt # Должно быть запрещено
```

**Задание 29:** Администрирование мандатных политик
- Откройте fly-admin-smc → "Мандатные атрибуты"
- Изучите настройки "Политика мандатного контроля"
- Просмотрите параметры "Строгость контроля"
- Изучите настройки наследования меток
- Проанализируйте исключения из мандатных правил

**Задание 30:** Аудит мандатного контроля доступа
```bash
# Включение аудита мандатного контроля
sudo auditctl -a always,exit -F arch=b64 -S open -F key=mac_access

# Генерация событий нарушения мандатного доступа
sudo -u user_low cat secret_info.txt 2>/dev/null

# Анализ событий аудита
sudo ausearch -k mac_access

# Создание отчета по нарушениям МРД
sudo grep "MAC" /var/log/audit/audit.log | tail -10

# Статистика по мандатному контролю
sudo grep -c "avc.*denied" /var/log/audit/audit.log
```

### Блок 4: Замкнутая программная среда (ЗПС) (Задания 31-40)

**Задание 31:** Изучение принципов ЗПС
```bash
# Проверка состояния ЗПС
cat /proc/digsig/status

# Просмотр настроек ЗПС
sudo cat /etc/digsig/digsig_initramfs.conf

# Проверка загруженного модуля цифровых подписей
lsmod | grep digsig

# Просмотр доверенных ключей
sudo ls -la /etc/digsig/keys/
```

**Задание 32:** Управление ЗПС через графический интерфейс
- Откройте fly-admin-smc → "Замкнутая программная среда"
- Изучите текущий режим работы (штатный/отладочный/проверки)
- Просмотрите список доверенных ключей
- Изучите настройки контроля библиотек
- Изучите параметры проверки подписей

**Задание 33:** Проверка цифровых подписей файлов
```bash
# Проверка подписи системного файла
sudo digsig-verif /bin/ls

# Массовая проверка подписей в каталоге
sudo find /usr/bin -type f -exec digsig-verif {} \; 2>/dev/null | head -10

# Поиск неподписанных исполняемых файлов
sudo find /usr/local/bin -type f -executable ! -name "*.signed" 2>/dev/null

# Статистика подписанных файлов
sudo find /usr/bin -type f | wc -l
sudo find /usr/bin -type f -exec file {} \; | grep "signed" | wc -l
```

**Задание 34:** Работа с ключами цифровых подписей
```bash
# Просмотр информации о ключах
sudo gpg --homedir /etc/digsig/keys --list-keys

# Проверка целостности ключевого хранилища
sudo ls -la /etc/digsig/keys/

# Создание тестового ключа (только для обучения!)
gpg --gen-key # НЕ ВЫПОЛНЯТЬ в production!

# Экспорт публичного ключа
gpg --export --armor > test_public_key.asc
```

**Задание 35:** Тестирование режимов работы ЗПС
```bash
# Создание простой программы для тестирования
cat << 'EOF' > test_program.c
#include <stdio.h>
int main() {
    printf("Test program running\n");
    return 0;
}
EOF

# Компиляция программы
gcc -o test_program test_program.c

# Попытка запуска неподписанной программы
./test_program

# Анализ логов ЗПС при попытке запуска
sudo journalctl -u digsig | tail -5
```

**Задание 36:** Настройка исключений в ЗПС
- Откройте fly-admin-smc → "Замкнутая программная среда" → "Исключения"
- Изучите возможность создания исключений для каталогов
- Просмотрите системные исключения
- Изучите правила для интерпретаторов скриптов
- **Внимание**: неправильные исключения снижают безопасность!

**Задание 37:** Мониторинг событий ЗПС
```bash
# Мониторинг событий проверки подписей в реальном времени
sudo tail -f /var/log/kern.log | grep digsig

# Поиск нарушений ЗПС в логах
sudo grep "digsig" /var/log/syslog

# Анализ статистики проверки подписей
sudo dmesg | grep digsig | tail -10

# Создание отчета о работе ЗПС
sudo journalctl -u digsig --since "1 day ago" > zps_report.log
```

**Задание 38:** Работа с подписанными пакетами
```bash
# Проверка подписей установленных пакетов
sudo apt-key list

# Проверка целостности пакетов
sudo debsums -c

# Поиск пакетов с нарушенной целостностью
sudo debsums -l | head -10

# Переустановка пакета с восстановлением подписей
sudo apt-get install --reinstall coreutils
```

**Задание 39:** Резервное копирование настроек ЗПС
```bash
# Создание резервной копии конфигурации ЗПС
sudo tar -czf zps_config_backup.tar.gz /etc/digsig/

# Сохранение списка доверенных ключей
sudo cp -r /etc/digsig/keys/ ~/zps_keys_backup/

# Экспорт настроек модуля
sudo cat /sys/module/digsig_verif/parameters/* > zps_parameters.txt

# Создание скрипта восстановления
cat << 'EOF' > restore_zps.sh
#!/bin/bash
echo "Восстановление настроек ЗПС..."
sudo tar -xzf zps_config_backup.tar.gz -C /
sudo update-initramfs -u -k all
echo "Требуется перезагрузка системы"
EOF
```

**Задание 40:** Анализ производительности ЗПС
```bash
# Измерение времени запуска подписанных программ
time /bin/ls > /dev/null

# Статистика работы модуля digsig
sudo cat /proc/digsig/stats

# Анализ влияния ЗПС на производительность системы
sudo iostat 1 5

# Мониторинг использования ресурсов модулем ЗПС
sudo ps aux | grep digsig
sudo lsof | grep digsig
```

### Блок 5: Расширенное администрирование безопасности (Задания 41-50)

**Задание 41:** Настройка комплексной политики безопасности
- Откройте astra-systemsettings (в версии 1.8) или fly-admin-smc
- Создайте комплексную политику безопасности для учебной среды:
  - Настройте аудит всех критических операций
  - Установите мандатные ограничения для пользователей
  - Настройте ЗПС в режиме строгого контроля
  - Создайте группы пользователей с разными уровнями доступа

**Задание 42:** Управление сетевой безопасностью
```bash
# Настройка сетевого экрана
sudo ufw enable
sudo ufw default deny incoming
sudo ufw default allow outgoing

# Настройка правил для служб безопасности
sudo ufw allow 22/tcp comment 'SSH'
sudo ufw allow from 192.168.1.0/24 to any port 389 comment 'LDAP'

# Мониторинг сетевых соединений
sudo netstat -tupln | grep :22
sudo ss -tulpn

# Анализ сетевого трафика
sudo tcpdump -i any -n host 192.168.1.1
```

**Задание 43:** Интеграция с внешними системами аутентификации
```bash
# Настройка подключения к LDAP (симуляция)
sudo apt install libpam-ldap nscd

# Конфигурация PAM для LDAP
sudo nano /etc/pam.d/common-auth

# Проверка интеграции с Active Directory (концептуально)
sudo realm discover domain.local

# Настройка Kerberos для единого входа
sudo nano /etc/krb5.conf

# Тестирование аутентификации
getent passwd
getent group
```

**Задание 44:** Создание собственных правил аудита
```bash
# Создание правил аудита для критических файлов
sudo auditctl -w /etc/passwd -p wa -k passwd_changes
sudo auditctl -w /etc/shadow -p wa -k shadow_changes
sudo auditctl -w /etc/sudoers -p wa -k sudoers_changes

# Аудит выполнения критических команд
sudo auditctl -a always,exit -F arch=b64 -S execve -F key=exec_commands

# Аудит сетевых соединений
sudo auditctl -a always,exit -F arch=b64 -S socket -F key=network_activity

# Создание отчета по аудиту
sudo aureport --summary
sudo aureport --executable --summary
```

**Задание 45:** Настройка системы резервного копирования
```bash
# Создание скрипта резервного копирования критических данных
cat << 'EOF' > backup_security.sh
#!/bin/bash
BACKUP_DATE=$(date +%Y%m%d_%H%M%S)
BACKUP_DIR="/opt/security_backup_$BACKUP_DATE"

echo "Создание резервной копии системы безопасности..."
sudo mkdir -p "$BACKUP_DIR"

# Конфигурация ПАРСЕК
sudo cp -r /etc/parsec/ "$BACKUP_DIR/"

# Настройки ЗПС
sudo cp -r /etc/digsig/ "$BACKUP_DIR/"

# Пользователи и группы
sudo cp /etc/passwd /etc/group /etc/shadow "$BACKUP_DIR/"

# Правила аудита
sudo cp /etc/audit/rules.d/* "$BACKUP_DIR/"

# Создание архива
sudo tar -czf "/opt/security_backup_$BACKUP_DATE.tar.gz" -C /opt "security_backup_$BACKUP_DATE"
sudo rm -rf "$BACKUP_DIR"

echo "Резервная копия создана: security_backup_$BACKUP_DATE.tar.gz"
EOF

chmod +x backup_security.sh
./backup_security.sh
```

**Задание 46:** Мониторинг и реагирование на инциденты
```bash
# Создание системы мониторинга безопасности
cat << 'EOF' > security_monitor.sh
#!/bin/bash

# Проверка неудачных попыток входа
FAILED_LOGINS=$(sudo grep "Failed password" /var/log/auth.log | wc -l)
if [ $FAILED_LOGINS -gt 10 ]; then
    echo "ВНИМАНИЕ: Обнаружено $FAILED_LOGINS неудачных попыток входа"
fi

# Проверка нарушений мандатного контроля
MAC_VIOLATIONS=$(sudo grep "avc.*denied" /var/log/audit/audit.log | wc -l)
if [ $MAC_VIOLATIONS -gt 0 ]; then
    echo "ВНИМАНИЕ: Обнаружено $MAC_VIOLATIONS нарушений мандатного контроля"
fi

# Проверка состояния ЗПС
ZPS_ERRORS=$(sudo grep "digsig.*error" /var/log/kern.log | wc -l)
if [ $ZPS_ERRORS -gt 0 ]; then
    echo "ВНИМАНИЕ: Обнаружено $ZPS_ERRORS ошибок ЗПС"
fi

# Проверка целостности критических файлов
sudo debsums -s | head -5

echo "Мониторинг безопасности завершен: $(date)"
EOF

chmod +x security_monitor.sh
./security_monitor.sh
```

**Задание 47:** Настройка отказоустойчивости системы безопасности
```bash
# Создание точки восстановления системы
sudo rsync -av /etc/ /backup/etc_$(date +%Y%m%d)/

# Настройка автоматического восстановления служб
sudo systemctl enable parsec
sudo systemctl enable auditd

# Создание скрипта проверки состояния безопасности
cat << 'EOF' > check_security_services.sh
#!/bin/bash

# Проверка состояния ПАРСЕК
if ! systemctl is-active --quiet parsec; then
    echo "КРИТИЧНО: Служба PARSEC не активна"
    sudo systemctl start parsec
fi

# Проверка состояния аудита
if ! systemctl is-active --quiet auditd; then
    echo "КРИТИЧНО: Служба аудита не активна"
    sudo systemctl start auditd
fi

# Проверка ЗПС
if ! lsmod | grep -q digsig; then
    echo "КРИТИЧНО: Модуль ЗПС не загружен"
fi

echo "Проверка служб безопасности завершена"
EOF

chmod +x check_security_services.sh
# Добавление в cron для регулярной проверки
echo "*/5 * * * * /home/admin/check_security_services.sh" | sudo crontab -
```

**Задание 48:** Создание отчетов о соответствии требованиям безопасности
```bash
# Создание скрипта генерации отчета соответствия
cat << 'EOF' > compliance_report.sh
#!/bin/bash

REPORT_FILE="compliance_report_$(date +%Y%m%d).html"

cat << HTML > $REPORT_FILE
<!DOCTYPE html>
<html>
<head>
    <title>Отчет о соответствии требованиям ИБ</title>
    <meta charset="utf-8">
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; }
        .header { background: #f0f0f0; padding: 10px; }
        .section { margin: 10px 0; padding: 10px; border: 1px solid #ccc; }
        .ok { background: #d4edda; }
        .warning { background: #fff3cd; }
        .error { background: #f8d7da; }
    </style>
</head>
<body>
    <div class="header">
        <h1>Отчет о соответствии требованиям информационной безопасности</h1>
        <p>Дата создания: $(date)</p>
        <p>Система: Astra Linux $(cat /etc/astra_version)</p>
    </div>
    
    <div class="section ok">
        <h2>Состояние КСЗ ПАРСЕК</h2>
        <p>Статус: $(systemctl is-active parsec)</p>
        <p>Версия: $(dpkg -l | grep parsec | head -1 | awk '{print $3}')</p>
    </div>
    
    <div class="section ok">
        <h2>Замкнутая программная среда</h2>
        <p>Модуль загружен: $(lsmod | grep digsig | wc -l > 0 && echo "Да" || echo "Нет")</p>
        <p>Режим работы: $(cat /etc/digsig/digsig_initramfs.conf | grep DIGSIG_ELF_MODE)</p>
    </div>
    
    <div class="section ok">
        <h2>Мандатный контроль доступа</h2>
        <p>Уровни конфиденциальности: $(sudo pdp-ls-levels | wc -l)</p>
        <p>Активных пользователей с МРД: $(sudo pdp-userlist | wc -l)</p>
    </div>
    
    <div class="section ok">
        <h2>Аудит и протоколирование</h2>
        <p>Служба аудита: $(systemctl is-active auditd)</p>
        <p>События за последний час: $(sudo ausearch -ts recent | wc -l)</p>
    </div>
</body>
</html>
HTML

echo "Отчет создан: $REPORT_FILE"
firefox $REPORT_FILE 2>/dev/null &
EOF

chmod +x compliance_report.sh
./compliance_report.sh
```

**Задание 49:** Настройка централизованного управления безопасностью
```bash
# Настройка удаленного сбора логов (rsyslog)
sudo nano /etc/rsyslog.conf
# Добавить: *.* @192.168.1.100:514

# Настройка централизованного аудита
sudo nano /etc/audisp/plugins.d/remote.conf

# Создание центрального хранилища политик безопасности
sudo mkdir -p /opt/security_policies
sudo chmod 750 /opt/security_policies

# Скрипт синхронизации политик безопасности
cat << 'EOF' > sync_security_policies.sh
#!/bin/bash

POLICY_SERVER="192.168.1.100"
POLICY_PATH="/opt/security_policies"

echo "Синхронизация политик безопасности с сервером $POLICY_SERVER"

# Загрузка политик аудита
rsync -av root@$POLICY_SERVER:$POLICY_PATH/audit/ /etc/audit/rules.d/

# Загрузка мандатных политик
rsync -av root@$POLICY_SERVER:$POLICY_PATH/mac/ /etc/parsec/

# Перезагрузка служб
sudo systemctl reload auditd
sudo systemctl restart parsec

echo "Синхронизация завершена"
EOF

chmod +x sync_security_policies.sh
```

**Задание 50:** Итоговый проект - создание защищенной рабочей среды
```bash
# Создание комплексного скрипта настройки защищенной среды
cat << 'EOF' > setup_secure_environment.sh
#!/bin/bash

echo "=== НАСТРОЙКА ЗАЩИЩЕННОЙ СРЕДЫ ASTRA LINUX ==="
echo "Начало настройки: $(date)"

# 1. Обновление системы
echo "1. Обновление системы..."
sudo apt update && sudo apt upgrade -y

# 2. Настройка КСЗ ПАРСЕК
echo "2. Настройка КСЗ ПАРСЕК..."
sudo systemctl enable parsec
sudo systemctl start parsec

# 3. Настройка ЗПС в строгом режиме
echo "3. Настройка ЗПС..."
sudo sed -i 's/DIGSIG_ELF_MODE=.*/DIGSIG_ELF_MODE=1/' /etc/digsig/digsig_initramfs.conf
sudo update-initramfs -u -k all

# 4. Настройка аудита
echo "4. Настройка системы аудита..."
sudo systemctl enable auditd
sudo auditctl -w /etc/passwd -p wa -k passwd_changes
sudo auditctl -w /etc/shadow -p wa -k shadow_changes

# 5. Создание пользователей с мандатными атрибутами
echo "5. Создание пользователей..."
sudo useradd -m user_public
sudo useradd -m user_secret
sudo passwd user_public
sudo passwd user_secret

sudo pdp-useradd user_public 0:0 1:1
sudo pdp-useradd user_secret 1:1 2:1,2

# 6. Создание структуры каталогов с мандатными метками
echo "6. Создание защищенных каталогов..."
sudo mkdir -p /opt/secure_data/{public,secret,top_secret}
sudo pdp-label /opt/secure_data/public 0:0
sudo pdp-label /opt/secure_data/secret 1:1
sudo pdp-label /opt/secure_data/top_secret 2:1,2

# 7. Настройка сетевой безопасности
echo "7. Настройка сетевой безопасности..."
sudo ufw --force enable
sudo ufw default deny incoming
sudo ufw allow ssh

# 8. Создание системы мониторинга
echo "8. Настройка мониторинга..."
cat << 'MONITOR' > /opt/security_monitor.sh
#!/bin/bash
# Скрипт мониторинга безопасности
LOGFILE="/var/log/security_monitor.log"
echo "$(date): Проверка безопасности" >> $LOGFILE

# Проверка служб
systemctl is-active parsec >> $LOGFILE
systemctl is-active auditd >> $LOGFILE

# Проверка нарушений
grep "avc.*denied" /var/log/audit/audit.log | tail -5 >> $LOGFILE

# Проверка неудачных входов
grep "Failed password" /var/log/auth.log | tail -5 >> $LOGFILE
MONITOR

chmod +x /opt/security_monitor.sh
echo "*/10 * * * * /opt/security_monitor.sh" | sudo crontab -

# 9. Создание документации
echo "9. Создание документации..."
cat << 'DOC' > /opt/security_documentation.md
# Документация защищенной среды Astra Linux

## Созданные пользователи:
- user_public: мандатный уровень 0 (открытая информация)
- user_secret: мандатный уровень 1 (конфиденциальная информация)

## Защищенные каталоги:
- /opt/secure_data/public: уровень 0
- /opt/secure_data/secret: уровень 1  
- /opt/secure_data/top_secret: уровень 2

## Активные службы безопасности:
- parsec: КСЗ ПАРСЕК
- auditd: система аудита
- ufw: сетевой экран

## Мониторинг:
- /opt/security_monitor.sh: скрипт мониторинга (запуск каждые 10 минут)
- /var/log/security_monitor.log: лог мониторинга

## Команды для проверки:
- sudo systemctl status parsec
- sudo pdp-ls-levels
- sudo ausearch -m AVC -ts recent
- sudo ufw status
DOC

echo "=== НАСТРОЙКА ЗАВЕРШЕНА ==="
echo "Защищенная среда Astra Linux настроена успешно!"
echo "Рекомендуется перезагрузка системы для применения всех настроек"
echo "Документация сохранена в /opt/security_documentation.md"
echo "Завершение: $(date)"
EOF

chmod +x setup_secure_environment.sh
./setup_secure_environment.sh
```
