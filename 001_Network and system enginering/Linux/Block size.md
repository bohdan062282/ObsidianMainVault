---
Category: Information
tags:
  - information
  - open
  - linux
---
---
###### External links
- 
---
## Description
`bs=` определяет **размер блока данных**, который читается и записывается за одну операцию `dd`.

---
## Block size
Примеры:
- `bs=512` — читается и пишется по 512 байт (обычный размер сектора у жёстких дисков);
- `bs=1M` — читается и пишется по 1 мегабайту;
- `bs=4M` — по 4 мегабайта, часто используется при копировании ISO-образов.

*В тупую - меньше блок - больше системных вызовов. То есть больше нагрузка на проц но меньше хавает оперы. В момент времени оперы хавает просто размер блока, потому что вгружает его туда и выгружает, все просто*

*Считается что лучше с поврежденными секторами минимальным блоком работать*


### Примеры производительности

| `bs`      | Примерная скорость (на HDD/SSD)                                 |
| --------- | --------------------------------------------------------------- |
| `bs=512`  | Очень медленно, много операций                                  |
| `bs=4K`   | Чуть быстрее, но всё ещё медленно                               |
| `bs=1M`   | Хороший компромисс                                              |
| `bs=4M`   | Обычно оптимально                                               |
| `bs=64M`+ | Иногда быстрее, но не всегда оправдано — может занять много RAM |
- *По-дефолту лучше всего использовать 1 или 4 и все.*
- *Для записи на флешку, например, Большой блок → быстрее запись - ставим 4м.*
- *Для считывания задамаженого диска (Маленький блок позволяет точно обнаружить и обойти плохие сектора) ставим 512 байт - размер сектора.*


### Пример тестирования скорости 
```bash
dd if=/dev/zero of=testfile bs=1G count=1 oflag=direct
```
Создаёт файл в 1 ГБ, чтобы проверить скорость диска. Тут bs=1G — единичная операция, максимум скорости (но требует много RAM).


### Тип носителя и оптимальный `bs`

|Тип носителя|Рекомендуемый `bs`|Максимальный `bs`, разумный|
|---|---|---|
|HDD (механика)|`bs=512K – 4M`|до `64M`|
|SATA SSD|`bs=1M – 16M`|до `128M`|
|NVMe SSD|`bs=4M – 64M`|до `1G` (если много RAM)|
|USB 2.0/3.0|`bs=1M – 4M`|до `32M`|
*Универсальный, можно сказать, это - 1м*


### Узнать размер блока устройства
```bash
cat /sys/block/sdX/queue/logical_block_size
cat /sys/block/sdX/queue/physical_block_size
```
1. С которым минимальным работает система
2. Физ размер сектора устройства

---
## Notes


---












