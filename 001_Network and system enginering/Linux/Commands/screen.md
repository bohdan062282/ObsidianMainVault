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
Терминальный мультиплексор

---
### Basic syntax
```bash
screen -S name    # создать
Ctrl+A D          # отсоединиться
screen -ls        # список
screen -r name    # вернуться (-d если принудительно надо)
exit              # закрыть

#принудительно задолбашить
screen -XS 2299264.a quit #(-X -отправить команду, -S -имя)
```


---
### Examples


---

