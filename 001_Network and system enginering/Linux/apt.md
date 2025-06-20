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
`apt` — это **пакетный менеджер** для систем на базе Debian (включая Ubuntu).
**`apt`** — это современный интерфейс к более низкоуровневым утилитам:  
`dpkg`, `apt-get`, `apt-cache` и другим.

---
### Basic syntax
| Команда                    | Что делает                                                     |
| -------------------------- | -------------------------------------------------------------- |
| `sudo apt update`          | обновляет **список доступных пакетов** из репозиториев         |
| `sudo apt upgrade`         | обновляет **установленные пакеты** до новых версий             |
| `sudo apt install <пакет>` | устанавливает новый пакет                                      |
| `sudo apt remove <пакет>`  | удаляет пакет (конфиги остаются)                               |
| `sudo apt purge <пакет>`   | удаляет пакет **вместе с конфигами**                           |
| `sudo apt autoremove`      | удаляет **неиспользуемые зависимости**                         |
| `apt list --installed`     | показывает список всех установленных пакетов                   |
| `apt search <имя>`         | ищет пакет по имени                                            |
| `apt show <пакет>`         | показывает инфу о пакете: версия, описание, зависимости и т.п. |

---
### Examples


---

