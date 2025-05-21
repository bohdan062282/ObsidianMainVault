- Ну базовое для этого дела это - `/system history`
- Можно юзать `/undo` `/redo` 

- *Отменяется последнее redoable правило*
- *А восстанавливается последнее отмененное правило, все по-дефолту*

### Configuration Export and Import

> The Export command does not export system user passwords, installed certificates, SSH keys, Dude, or a User-manager database.
> [Installed certificates](https://help.mikrotik.com/docs/display/ROS/Certificates#Certificates-ExportCertificate), [Dude](https://wiki.mikrotik.com/Manual:The_Dude_v6/DB_import_export), and [User-manager](https://help.mikrotik.com/docs/display/ROS/User+Manager#UserManager-Database) databases must be manually exported and imported into a new device.
> System user passwords and user SSH keys can not be exported.

*Ну и понятно что микротики просят что бы версия была одинаковая у роутерОС, что бы не было конфликтов команд*

#### Export
`export`

*Экспортит только юзеровые модификации. Не будет экспортить дефолтные.*

> Note:
> The * flag, indicates that the entry is system default and cannot be removed manually.

Лист со списком, где могут быть дефолтные штуки:
https://help.mikrotik.com/docs/spaces/ROS/pages/328155/Configuration+Management#ConfigurationManagement-ConfigurationExport

*Начиная с RouterOS 7.13 можно экспортить специфические куски, пример:*
```bash
ip firewall address-list export where list=mylist
```

Параметры экспорта:

|                                                                                                                                                          |                                                                                                                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **compact**                                                                                                                                              | Так понимаю то шо он считает по дефолту имеет какие-то значения то не будет экспортить.                                                                                |
| **file**                                                                                                                                                 | Понятно, файл                                                                                                                                                          |
| **show-sensitive** _(yes\|no; Default: no)._ **RouterOS version 7 only**<br><br>**hide-sensitive** _(yes\|no; Default: no_). **RouterOS version 6 only** | Show sensitive information, like passwords, keys, etc.<br><br>Hide sensitive information, like passwords, keys, etc.                                                   |
| **terse**                                                                                                                                                | With this parameter, the export command will output only configuration parameters, without defaults. (хотя как я понял то он каждой команде абсолютный путь указывает) |
| **verbose**                                                                                                                                              | Ну тут тупо все будет вытягивать, вместе с параметрами со звездочкой                                                                                                   |

#### Import

|               |                                                                                                                                                     |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **from-line** | Start executing the script from the specified line number. This option is only available in verbose mode.                                           |
| **file-name** | Name of the script (.rsc) file to be executed.                                                                                                      |
| **verbose**   | Reads each line from the file and executes individually, allowing to debug syntax or other errors more easily.                                      |
| **dry-run**   | Simulates the import without making any configuration changes. This helps in catching syntax errors. This option is only available in verbose mode. |
*Ну и надо если заливать импорт то нужно конечно почистить конфигурацию до этого*

##### [Import troubleshooting](https://help.mikrotik.com/docs/spaces/ROS/pages/328155/Configuration+Management#ConfigurationManagement-Importtroubleshooting)

### Reset configuration
Ну понятно шо юзер будет или админ без пасса или то шо на железяке написано.

[Список дефолтных конфигураций](https://help.mikrotik.com/docs/spaces/ROS/pages/167706788/Default+configurations)

Ну все параметры очевидны, только вот:
`run-after-reset`  - по идее указываем файл конфигурации. *Если файл будет выполняться более 2х минут то будет фейл.*



