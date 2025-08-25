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
## Group management tools
### groupadd
---
**Описание**: создаёт новую группу.  
**Синтаксис**:
`groupadd [опции] groupname`

**Популярные опции**:
- `-g GID` → указать конкретный group ID
- `-r` → создать системную группу (GID < 1000)


### groupdel
---
**Описание**: удаляет группу.  
**Синтаксис**:
`groupdel groupname`

⚠️ Нельзя удалить группу, если она является **основной** для пользователей. Сначала поменяй им группу через `usermod -g`.


### groupmod
---
**Описание**: изменяет параметры существующей группы.  
**Синтаксис**:
`groupmod [опции] groupname`

**Опции**:
- `-n newname oldname` → переименовать группу
- `-g GID groupname` → сменить GID


### gpasswd
---
**Описание**: управляет паролем группы и членством пользователей.  
**Синтаксис**:
`gpasswd [опции] groupname`

**Действия**:
- `gpasswd groupname` → установить/сменить пароль группы
- `gpasswd -a user group` → добавить юзера в группу
- `gpasswd -d user group` → удалить юзера из группы
    


### usermod -aG
---
**Описание**: добавляет пользователя в одну или несколько дополнительных групп.  
**Синтаксис**:

`usermod -aG group1,group2 user`

⚠️ Без `-a` (append) все старые группы будут **заменены**, что часто ломает доступ.

**Пример**:
`usermod -aG docker,sudo bogdan`



---
## Notes


---
