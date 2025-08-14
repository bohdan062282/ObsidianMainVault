---
Category: Command
tags:
  - command
  - linux
  - open
---
###### External Links

---
### Description

---
### Basic syntax
- `-type f` — искать только файлы, `-type d` — только директории.
- `-mtime` — по времени модификации (`-n` — меньше n дней, `+n` — больше).

---
### Examples
```bash
find / -name file.txt        # поиск файла file.txt по всей системе
find . -name "*.log"         # все .log в текущей папке и ниже
find /var/log -type f -size +10M   # файлы больше 10 MB
find /etc -type d -name "nginx"    # директория с именем nginx
find /tmp -mtime -1          # изменённые за последние сутки
```


---

