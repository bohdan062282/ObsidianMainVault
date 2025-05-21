### Saving a backup
**Sub-menu:** `/system backup save`
- **dont-encrypt** (_yes | no_; Default: **no**)
- **encryption** (_aes-sha256 | rc4_; Default: **aes-sha256**) - нормально будет чисто шоб совместимость со старыми версиями была
- **name** (_string_; Default: **[identity]-[date]-[time].backup**)
- **password** (_string_; Default: )

*Если версия начиная с v6.43 и донтЭнкрипт не выбран то будет зашифрован пароль текущего юзера.*

### Loading backup
Без пароля:
```bash
`system/backup/load name=auto-before-reset.backup password=""`
```

*А может можно и без пассворд, но когда с паролем то можно и без, надо пробовать*


