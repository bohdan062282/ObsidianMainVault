### Versions
- **Long term**: Released rarely, and includes only the most critical fixes, upgrades within one number branch do not contain new features. When a **Stable** release has been out for a while and seems to be stable enough, it gets promoted into the long-term branch, replacing an older release, which is then moved to the archive. This consecutively adds new features.
- **Stable**: Released every few months, including all tested new features and fixes.
- **Testing**: Released every few weeks, only undergoes basic internal testing, and should not be used in production.
- **Development**: Released when necessary. Includes raw changes and is available for software enthusiasts for testing new features.

### Standart update
System → Packages menu. The _Check For Updates_ window will open with the current or the latest changelog (if a newer version exists). If newer version exists, buttons _Download_ and _Download&Install_ will appear. By cicking the _Download_ button a newest version will be downloaded (manual device reboot is required), by clicking _Download&Install_, download will start, and after a successful download will reboot a device to install the downloaded packages.

Не всегда в каналах есть последняя версия, часто нужно сначала обновиться до промежуточной а потом будут и новее светиться.

***It is strongly recommended to upgrade the bootloader after RouterOS update. To upgrade the bootloader, execute command "/system routerboard upgrade" in CLI, followed by a reboot. Alternatively, navigate to the GUI System → RouterBOARD menu and click the "Upgrade" button, then reboot the device.***

##### Апдейт скрипт (потом разобрать)
You can **automate** the upgrade process by running a script in the system scheduler. This script queries the MikroTik upgrade servers for new versions, if the response received says "New version is available", the script then issues the upgrade command below. Important note, this will not work, if you are running it for the first time on a release that is older. It might not see latest versions as available, if you are running v6.x, you would first have to manually select the "Upgrade" channel to do a major release upgrade to v7.12.1 intermediate version, and only afterwards newer v7 releases will be visible in the upgrade channels. 
```bash
/system package update check-for-updates once
:delay 3s;
:if ( [get status] = "New version is available") do={ install }`
```

### Manual upgrade
- WinBox – drag and drop files to the Files menu
- WebFig - upload files from the Files menu
- FTP - upload files to the root directory

- *Ну через винбокс по-дефолту закидываем файлик и он хавает его*
- *Через фпт тоже просто закинуть файлик*

`/system reboot`
`Reboot, yes? [y/N]: y`
after the reboot, your router will be up to date, you can check it in this menu:
`/system package print`
if your router did not upgrade correctly, make sure you check the **log**
`/log print without-paging`

### RouterOS local upgrade
*Feature is available from **7.17beta3** version in (system > packages local update) and will replace (system > auto update) feature.*

На сервачке должны быть просто файлы прошивки.
Можно сделать железяку мирор-сервером и в настройках сослаться на основной. (Минимальный интервал может быть 07:12). По идее он подключается по порту винбокса.
Ну на клиенте просто добавляем сервак и обновляем файлы и качаем..

### RouterOS upgrade using Dude
https://help.mikrotik.com/docs/spaces/ROS/pages/328142/Upgrading+and+installation#Upgradingandinstallation-RouterOSupgradeusingDude

### [[Netinstall]]
Netinstall is a widely-used installation tool for RouterOS. It runs on Windows systems or via a command-line tool, netinstall-cli, on Linux, or through Wine (with superuser permissions required).

The NetInstall utilities can be downloaded from the [MikroTik download section](https://www.mikrotik.com/download).

Netinstall is also used to re-install RouterOS in cases where a previous installation has failed, been damaged, or where access passwords have been lost.

To use NetInstall, your device must support booting from Ethernet, with a direct Ethernet connection between the NetInstall computer and the target device. All RouterBOARDs support PXE network booting, which can be enabled in the RouterOS "routerboard" menu (if RouterOS is accessible) or in the bootloader settings using a serial console cable.

***Note:** For RouterBOARD devices without a serial port or RouterOS access, you can activate PXE booting using the resetButton.*

NetInstall can also directly install RouterOS onto a disk (USB/CF/IDE/SATA) connected to the NetInstall Windows machine. Once installed, simply transfer the disk to the Router machine and boot from it.

#### [[Packages]]
