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
Process status
*Без ключей - только процессы текущего юзера и текущей сессии.*

*Существует 3 вида вывода и типа ключей: UNIX, BSD, GNU.*
Аааааа, гну запись - это через два дефиса --.

---
### Basic syntax
Некоторые поля:
- `USER`: The effective user (the one whose access we are using)
- `STAT`: Process status code

- #### BSD:

	`ps aux` - BSD style.
	
	*The `a` displays all processes running, including the ones being run by other users. The `u` shows more details about the processes. And finally, the `x` lists all processes that don't have a TTY associated with them. These programs will show a `?` in the TTY field; they are most common in daemon processes that launch as part of the system startup.*

	`f` - дерево

- #### UNIX:

	`-u [user]` - процессы юзера
	`-e или -А` - все процйессы в системе
	`-f` - с деталями (классика `ps -ef`)
	`-j` - job формат (группы процессов, сессии)
	`-H` - дерево (удобно `ps -ejH`)
	`-o [имя колонки]` - свой вывод 
	`--sort=[-or+][имя колонки]` - сорт
	


---
### Examples
```bash
ps -eo pid,comm,%cpu,%mem --sort=-%cpu | head
```

---

