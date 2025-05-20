`netsh` (Network Shell) — это встроенная утилита Windows, позволяющая настраивать и управлять сетевыми параметрами системы: интерфейсами, IP, DNS, маршрутизацией, брандмауэром и т.д.

#### Просмотр интерфейсов
`netsh interface show interface`

#### Отключение-включение интерфейса
`netsh interface set interface name="Имя" admin=disabled(enabled)`

### Настройка айпи
#### Статика
```sh
netsh interface ip set address name="Ethernet" static 192.168.1.100 255.255.255.0 192.168.1.1

netsh interface ip set dns name="Ethernet" static 8.8.8.8
netsh interface ip add dns name="Ethernet" 8.8.4.4 index=2
```

#### DHCP
```sh
netsh interface ip set address name="Ethernet" source=dhcp

netsh interface ip set dns name="Ethernet" source=dhcp
```

*По идее можно это дело комбинировать.*

### Firewall
#### Отключить включить
```sh
netsh advfirewall set allprofiles state off
netsh advfirewall set allprofiles state on
```
#### Разрешить порт 8080
```sh
netsh advfirewall firewall add rule name="Open Port 8080" dir=in action=allow protocol=TCP localport=8080
```

### Resets
`netsh int ip reset`
✅ Удаляет все пользовательские настройки TCP/IP  
✅ Сбрасывает ключи реестра, связанные с IP  
✅ Удаляет статические маршруты  
✅ Может помочь при:
- Потере доступа к интернету
- Ошибках типа "Сетевой протокол отсутствует"
- Проблемах с DNS
- Не работает DHCP
- Ошибках после вирусов или кривых VPN/файрволов

`netsh winsock reset`
**Winsock** — это интерфейс, через который программы получают доступ к сетевым функциям Windows.
Команда **удаляет повреждённые или изменённые записи Winsock из реестра** и восстанавливает его к заводским настройкам.
✅ После вирусов, троянов, рекламных программ  
✅ После криво удалённых VPN, файрволов или антивирусов  
✅ Проблемах с DNS или прокси, которые "застревают" в системе

```sh
netsh winsock reset
netsh int ip reset
ipconfig /flushdns
ipconfig /release
ipconfig /renew
```

### Полезные команды
```sh
netsh interface ip show config

netsh int ip reset

netsh interface ip show config name="Ethernet"
```