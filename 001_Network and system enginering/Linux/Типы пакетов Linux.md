---
Category: Information
tags:
  - information
  - open
  - linux
---

###### External links
- 
---
## Description


---
## Типы пакетов Linux
#### 1. **DEB** (.deb)
- **Что это**: Пакетный формат для систем, основанных на **Debian**.
- **Установка**: `dpkg`, `apt`, `gdebi`, или через графический установщик.
- **Где используется**:
    - Debian
    - Ubuntu
    - Linux Mint
    - Pop!_OS
    - Elementary OS
    - Zorin OS
- **Совместимость**: Пакеты DEB можно использовать на любом производном от Debian дистрибутиве, но иногда бывает конфликт версий библиотек.

---
#### 2. **RPM** (.rpm)
- **Что это**: Формат пакетов для дистрибутивов **Red Hat**-семейства.
- **Установка**: `rpm`, `dnf`, `yum`, или через графический установщик.
- **Где используется**:
    - Red Hat Enterprise Linux (RHEL)
    - Fedora
    - CentOS (до версии 8)
    - AlmaLinux
    - Rocky Linux
    - openSUSE (с поддержкой RPM)
- **Совместимость**: Пакеты RPM иногда можно адаптировать под разные RPM-системы, но тоже есть риски несовместимости библиотек.

---

#### 3. **TAR.GZ** (.tar.gz / .tgz / .tar.bz2 / .tar.xz)
- **Что это**: Просто архив исходников или бинарников (не сам по себе пакетный формат).
- **Установка**: Обычно надо вручную распаковать, затем `./configure`, `make`, `make install` или просто запустить бинарник.
- **Где используется**: Подходит для **любой Linux-системы**, но требует ручной установки.
- **Совместимость**: Высокая (если нет зависимости от конкретных библиотек).

---

#### 4. **AppImage** (.AppImage)
- **Что это**: Самодостаточный бинарный образ. Не требует установки.
- **Установка**: Дать права на исполнение (`chmod +x`), запустить.
- **Где используется**: Любой современный Linux.
- **Совместимость**: Отличная. Работает почти везде, если ядро и библиотеки достаточно новые.

---

#### 5. **Snap** (snap-пакеты)
- **Что это**: Контейнеризованный формат от Canonical (создателей Ubuntu).
- **Установка**: Через `snapd` (`snap install пакет`).
- **Где используется**:
    - Ubuntu (встроено)
    - Linux Mint (ограниченно)
    - Fedora
    - Arch (через установку `snapd`)
- **Совместимость**: Нужен установленный `snapd`. Иногда конфликты с политиками безопасности (например, в Fedora нужно дополнительно включать поддержку).

---

#### 6. **Flatpak** (flatpak-пакеты)
- **Что это**: Альтернативный контейнерный формат для приложений, более независимый от Canonical.
- **Установка**: Через `flatpak` (`flatpak install репозиторий приложение`).
- **Где используется**:
    - Fedora (по умолчанию)
    - Ubuntu (можно установить)
    - Linux Mint
    - Elementary OS
- **Совместимость**: Отличная. Главное — установить `flatpak` и подключить репозитории (например, Flathub).

---

#### 7. **Source Code** (исходники)
- **Что это**: Программа в виде исходного кода.
- **Установка**:
    - `git clone` / скачать архив
    - `./configure && make && sudo make install`
- **Где используется**: Везде.
- **Совместимость**: Требует правильной сборки. Нужно вручную решать зависимости.  
    (Удобно, но требует навыков).

### Сводная таблица совместимости

|Формат|Подходит для|Требует установку менеджера|Совместимость|
|---|---|---|---|
|`.deb`|Debian, Ubuntu и производные|Нет|Высокая|
|`.rpm`|RHEL, Fedora, openSUSE|Нет|Высокая|
|`.tar.gz`|Все дистрибутивы|Нет|Очень высокая|
|`.AppImage`|Все дистрибутивы|Нет|Очень высокая|
|`Snap`|Ubuntu, Fedora, Arch и др.|Да (`snapd`)|Средняя/высокая|
|`Flatpak`|Fedora, Ubuntu, Mint и др.|Да (`flatpak`)|Очень высокая|
|Исходники|Все системы|Нет|Зависит от сборки|

### Дополнительно
- **Pacman пакеты (.pkg.tar.zst)**: используются в **Arch Linux** и производных (Manjaro, EndeavourOS).  
    Установка через `pacman -S пакет`.
- **Portage**: система сборки и управления пакетами для **Gentoo Linux** (работает через исходники).
- **Nix**/**Guix**: отдельные современные менеджеры пакетов (NixOS, GuixSD) с собственным форматом.

---
## Notes
### Вывод
- Для **Ubuntu** удобнее `.deb`, `Snap`, `Flatpak`.
- Для **Fedora** удобнее `.rpm`, `Flatpak`.
- Для **Arch** — `pacman`, `AUR` (из исходников).
- Для **максимальной совместимости** — `AppImage` или `Flatpak`.

---

