---
Category: Information
tags:
  - information
  - open
---
---
###### External links
- 
---
## Description

---
## Packages
### System packages

|                                |                                                          |
| ------------------------------ | -------------------------------------------------------- |
| **routeros-arm** (_arm_)       | system package for arm devices                           |
| **routeros-arm** _(arm64)_     | system package for arm64 devices                         |
| **routeros-mipsbe** (_mipsbe_) | system package for mipsbe devices                        |
| **routeros-mmips** (_mmips_)   | system package for mmips devices                         |
| **routeros-smips** (_smips_)   | system package for smips devices                         |
| **routeros-tile** (_tile_)     | system package for tile devices                          |
| **routeros-ppc** (_ppc_)       | system package for ppc devices                           |
| **routeros** (_x86, CHR_)      | system package for x86 installations and CHR environment |

### Extra packages

|                                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| -------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **calea** (_arm, arm64, mipsbe, mmips, tile, ppc, x86, CHR_)               | Data gathering tool for specific use due to "Communications Assistance for Law Enforcement Act" in the USA                                                                                                                                                                                                                                                                                                                                                                                                          |
| **container** _(arm, arm64, x86, CHR)_                                     | [Container](https://help.mikrotik.com/docs/display/ROS/Container) implementation of Linux containers, allows users to run containerized environments within RouterOS                                                                                                                                                                                                                                                                                                                                                |
| **dude** (_arm, arm64, mmips, tile, x86, CHR_)                             | [Dude](https://wiki.mikrotik.com/wiki/Manual:The_Dude) tool that allows monitoring of network environment                                                                                                                                                                                                                                                                                                                                                                                                           |
| **extra-nic** (arm64)                                                      | arm64 CPU architecture, Network Interface Card(NIC) support, recommended for UEFI installation on non MikroTik boards                                                                                                                                                                                                                                                                                                                                                                                               |
| **gps** (_arm, arm64, mipsbe, mmips, tile, ppc, x86, CHR_)                 | [Global Positioning System](https://help.mikrotik.com/docs/display/ROS/GPS) devices support                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **iot** (_arm, arm64, mipsbe, mmips, tile, ppc, x86, CHR_)                 | Enables:<br><br>- [MQTT](https://help.mikrotik.com/docs/display/ROS/MQTT)<br>- [LoRa](https://help.mikrotik.com/docs/display/ROS/General+Properties) (for devices with LR8/9/2 miniPCie cards)<br>- [Bluetooth](https://help.mikrotik.com/docs/display/ROS/Bluetooth) (for devices with Bluetooth chip)<br>- [GPIO](https://help.mikrotik.com/docs/display/ROS/GPIO) (for devices with GPIO pins)<br>- [Modbus](https://help.mikrotik.com/docs/pages/viewpage.action?pageId=61046813) (for devices with RS485 port) |
| **iot-bt-extra** (arm, arm64)                                              | A package for ARM, ARM64 devices which enables the use of USB Bluetooth adapters (must support LE 4.0+).<br><br>_**note**:_ Not all adapters were tested. We can not guarantee beforehand that a specific adapter will work.                                                                                                                                                                                                                                                                                        |
| **lora** _(arm, arm64, mipsbe, mmips, tile, ppc, x86, CHR)_                | Dummy package for [Lora](https://help.mikrotik.com/docs/display/ROS/General+Properties) support. LoRa package is not obligatory anymore and is left only for compatibility reasons. LoRa functionality is moved into iot package.                                                                                                                                                                                                                                                                                   |
| **lte** _(mipsbe)_                                                         | Required package only for SXT LTE (RBSXTLTE3-7), which contains drivers for the built-in LTE interface.                                                                                                                                                                                                                                                                                                                                                                                                             |
| **rose-storage** (_arm, arm64, tile, x86, CHR_)                            | Additional [enterprise data center functionality](https://help.mikrotik.com/docs/display/ROS/ROSE-storage) in RouterOS, support disk monitoring, improved formatting, RAIDs, rsync, iSCSI , NVMe over TCP, NFS, and improved SMB                                                                                                                                                                                                                                                                                    |
| **tr069-client** (_arm, arm64, mipsbe, mmips, smips, tile, ppc, x86, CHR_) | [TR069 Client](https://help.mikrotik.com/docs/display/ROS/TR-069) package                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **ups** (_arm, arm64, mipsbe, mmips, tile, ppc, x86, CHR_)                 | [APC ups management](https://help.mikrotik.com/docs/display/ROS/UPS) interface                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **user-manager** (_arm, arm64, mipsbe, mmips, tile, ppc, x86, CHR_)        | [MikroTik User Manager](https://help.mikrotik.com/docs/display/ROS/User+Manager) server for controlling Hotspot and other service users.                                                                                                                                                                                                                                                                                                                                                                            |
| **wifi-qcom** (_arm, arm64_)                                               | Mandatory driver package for 802.11ax interfaces. Introduced in 7.13.  [Wifi CAPsMAN](https://help.mikrotik.com/docs/display/ROS/WiFi#WiFi-WiFiCAPsMAN) support comes with the system package.                                                                                                                                                                                                                                                                                                                      |
| **wifi-qcom-ac** (_arm_)                                                   | Optional [Wifi](https://help.mikrotik.com/docs/display/ROS/WiFi) driver package for compatible 802.11ac interfaces. Introduced in 7.13.                                                                                                                                                                                                                                                                                                                                                                             |
| **wireless** (_arm, arm64, mipsbe, mmips, tile, ppc, x86, CHR_)            | Utilities and drivers for managing WiFi (up to 802.11ac) and 60GHz wireless interfaces.  <br>This package is bundled into RouterOS for versions up to 7.12. Starting with 7.13, it is a separate package.  <br><br>The **wireless** package conflicts with **wifi-qcom** and **wifi-qcom-ac** packages - they cannot be active at the same time.                                                                                                                                                                    |
| **zerotier** _(arm, arm64)_                                                | Enables [ZeroTier](https://help.mikrotik.com/docs/display/ROS/ZeroTier) functionality                                                                                                                                                                                                                                                                                                                                                                                                                               |

### Working with packages

**Menu:** _/system package_

Commands executed in this menu will take place only on restart of the router. Until then, the user can freely schedule or revert set actions.

|                   |                                                                                                                                                                                   |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **disable**       | schedule the package to be disabled after the next reboot. No features provided by the package will be accessible                                                                 |
| **downgrade**     | will prompt for the reboot. During the reboot process will try to downgrade the RouterOS to the oldest version possible by checking the packages that are uploaded to the router. |
| **enable**        | schedule package to be enabled after the next reboot                                                                                                                              |
| **uninstall**     | schedule package to be removed from the router. That will take place during the reboot.                                                                                           |
| **unschedule**    | remove scheduled task for the package.                                                                                                                                            |
| **print**         | outputs information about the packages, like: version, package state, planned state changes, etc.                                                                                 |
| **update**        | manages the _"check-for-updates"_ channel and performs RouterOS upgrades                                                                                                          |
| **apply-changes** | apply scheduled changes and reboot device                                                                                                                                         |

**Menu:** _/system/check-installation_

The "Check installation" function ensures the integrity of the RouterOS system by verifying the readability and correct placement of files. Its primary purpose is to confirm the health and status of your NAND/Flash storage.

**Menu:** _/system/package/update install ignore-missing_ command allows upgrading only the RouterOS main package, while omitting packages that are either missing or not uploaded during a manual upgrade process.

---
## Notes
- *По дефолту лочше проверять логи после ребута, потому что какие-то пакеты могут требовать совместимость или зависимости.*
- *Если зааплоадить файл с названием ".auto.npk" то по идее будет афтоапдейт но возможно если закинуть по фпт или сфтп.*

---

