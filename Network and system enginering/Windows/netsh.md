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

### Полезные команды
```sh
netsh interface ip show config

netsh int ip reset

netsh interface ip show config name="Ethernet"
```