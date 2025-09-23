---
Category: Information
tags:
  - information
  - linux
  - open
---
---
###### External links
- 
---
## Description


---
## permission bits
### SUID
Set User ID — это специальный бит прав доступа в Linux/Unix, который заставляет программу выполняться **с правами владельца файла**, а не того пользователя, кто её запускает.

Вместо обычного `x` у владельца стоит `s` → это и есть **SUID**.

*По сути надо шоб программа могла юзать файлы, которые не может юзать юзер, хоть он может запустить программу.*
``
```bash
chmod u+s [файл]
sudo chmod 4755 [myfile]
```

### SGID
```bash
sudo chmod g+s myfile
sudo chmod 2555 myfile
```

Так же само, только х будет в бите исполнения группы.

---
## Notes


---
