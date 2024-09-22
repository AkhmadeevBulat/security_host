# Домашнее задание к занятию "Защита хоста"

---

## Ахмадеев Булат Наилевич

---

## Задание 1

### Листинг команд:

```
# Установка eCryptfs
sudo apt update
sudo apt install ecryptfs-utils

# Создание нового пользователя
sudo adduser cryptouser

# Зашифровал домашний каталог пользователя
sudo ecryptfs-migrate-home -u cryptouser

# Перезагрузил систему
sudo reboot
```

Вывод под пользователем administrator:

![alt text](<images/Снимок экрана 2024-09-23 в 01.43.18.png>)

Вывод под пользователем root:

![alt text](<images/Снимок экрана 2024-09-23 в 01.44.56.png>)

Вывод под пользователем cryptouser:

![alt text](<images/Снимок экрана 2024-09-23 в 01.49.22.png>)

![alt text](<images/Снимок экрана 2024-09-23 в 01.53.17.png>)

---

## Задание 2

### Листинг команд:

```
# Установка LUKS
sudo apt update
sudo apt install cryptsetup

# Создание раздела на 100 МБ
dd if=/dev/zero of=/cryptodisk.img bs=1M count=100

# Зашифровал файл-образ с помощью LUKS
sudo cryptsetup luksFormat /cryptodisk.img

# Открыл зашифрованный раздел
sudo cryptsetup luksOpen /cryptodisk.img cryptodisk

# Создал файловую систему на зашифрованном разделе
sudo mkfs.ext4 /dev/mapper/cryptodisk

# Смонтировал зашифрованный раздел
sudo mkdir /mnt/cryptodisk
sudo mount /dev/mapper/cryptodisk /mnt/cryptodisk
```

### Создание раздела на 100 МБ:

![alt text](<images/Снимок экрана 2024-09-23 в 01.58.08.png>)

### Зашифровал файл-образ с помощью LUKS

![alt text](<images/Снимок экрана 2024-09-23 в 02.00.46.png>)

### Открыл зашифрованный раздел и создал файловую систему на зашифрованном разделе

![alt text](<images/Снимок экрана 2024-09-23 в 02.02.30.png>)

### Смонтировал зашифрованный раздел

![alt text](<images/Снимок экрана 2024-09-23 в 02.03.50.png>)
