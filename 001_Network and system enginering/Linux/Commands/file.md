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
Показывает, что за файл, независимо от его расширения. Проверяет «магическую подпись» содержимого, а не только имя.

---
### Basic syntax
**Полезные опции:**
- `-b` — вывод без имени файла.
- `-i` — вывод в виде MIME-типа (`text/plain`, `image/png` и т.п.).
- `-z` — пытаться анализировать сжатые файлы.
- `-f` — читать список файлов из указанного файла.

---
### Examples
```bash
file photo.jpg
# Вывод: photo.jpg: JPEG image data, Exif standard

file -b script.sh
# Вывод: Bourne-Again shell script, ASCII text executable

file -i document.pdf
# Вывод: document.pdf: application/pdf; charset=binary

file -z archive.gz
# Анализировать даже если файл сжат
```

---

