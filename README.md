# 👨‍💻 Mr. Robot Themed Penetration Testing Lab

Этот проект представляет собой лабораторию для практики тестирования на проникновение в стиле сериала "Мистер Робот". Лаборатория включает сценарии для исследования уязвимостей, брутфорсинга директорий и перебора учетных данных, а также авторизации по SSH с использованием ключей.

## Структура проекта

Проект состоит из нескольких этапов, которые позволяют погрузиться в атмосферу тестирования безопасности с использованием намеков в стиле "Мистера Робота". На каждом этапе пользователи получают задания и подсказки для продвижения к следующему шагу.

### Основные этапы

1. **Перебор директорий и robots.txt**  
   Используется `dirsearch` для поиска скрытых директорий. В `robots.txt` хранится сообщение с намеками для пользователя.

2. **Сканирование портов с помощью Nmap**  
   Используется для обнаружения открытых портов (FTP, SSH, SMB) и нахождения целевых сервисов.

3. **FTP-доступ с анонимной авторизацией**  
   Пользователь получает доступ к FTP и находит учетные данные для SMB.

4. **SMB-доступ**  
   С помощью найденных учетных данных пользователь подключается к SMB-шее и получает SSH-ключ для авторизации.

5. **Авторизация по SSH с использованием ключей**  
   SSH-ключ используется для входа на сервер под пользователем `mrrobot`.

---

## Установка

1. Скачать образ машины по ссылке
```bash
   https://cloud.mail.ru/public/feNE/NUiDvkto4
```
2. Убедитесь, что у вас установлены необходимые инструменты:
    Nmap: для сканирования портов.
    Dirsearch: для перебора директорий.
    Hydra или Medusa: для брутфорсинга паролей.
    Samba и vsftpd: для настройки SMB и FTP-серверов.
    OpenSSH: для настройки SSH.
3. Следуйте инструкциям ниже, чтобы настроить среду.
## 🕵️‍♂️ Прохождение

### Шаг 1: Перебор директорий
Запустите dirsearch, чтобы найти скрытые директории и прочитать robots.txt для получения подсказок.

```bash
dirsearch -u http://yourserverip -e txt
```
### Шаг 2: Сканирование портов
С помощью Nmap определите открытые порты, такие как SSH, FTP, и SMB.

```bash
nmap -sS -p- yourserverip
```
### Шаг 3: Подключение через FTP
Подключитесь к FTP-серверу с анонимным доступом и найдите учетные данные для SMB.

```bash
ftp yourserverip
```
### Шаг 4: Доступ к SMB-шее
С использованием найденных учетных данных подключитесь к SMB-шее, чтобы получить SSH-ключ.

```bash
  smbclient //yourserverip/SHARE_NAME -U username
```
### Шаг 5: Авторизация по SSH
Примените найденный SSH-ключ для авторизации на сервере под пользователем mrrobot.

```bash
ssh -i path/to/key mrrobot@yourserverip
```

### Зависимости
  Nmap,
  Dirsearch,
  Hydra или Medusa,
  vsftpd и samba,
  OpenSSH

### Безопасность
  Проект предназначен исключительно для учебных целей и тестирования в изолированной среде. Убедитесь, что все настройки безопасности восстановлены после завершения практики.
