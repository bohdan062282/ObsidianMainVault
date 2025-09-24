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
сравнивает **два текста (файла или вывода)** и показывает **различия между ними**.

---
### Basic syntax

- `-w` - игнорировать пробелы
- `-r` - рекурсивно (сравнивает деревья каталогов)


Выводит различия построчно в формате:

```bash
<n строки>c<n строки>
< строки из file1
---
> строки из file2

- `c` → change (изменено)
- `a` → add (добавлено)
- `d` → delete (удалено)
```

#### Unified format (удобнее читать)
`diff -u file1.txt file2.txt`

Вывод выглядит как патч:

```bash
@@ -1,3 +1,3 @@
-старый текст
+новый текст
```

#### Side-by-side
`diff -y file1.txt file2.txt`

---
### Examples


---

