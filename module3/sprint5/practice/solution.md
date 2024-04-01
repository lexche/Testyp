### Задание 1.

1. Настраиваем порт коммутатора, который подключён к маршрутизатору: переводим его в режим trunk:

```
Switch#conf t
Switch(config)#interface GigabitEthernet0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)#ex
Switch(config)#ex
Switch#
Switch#wr

```

2. Мы не знаем какой компьютер куда подключен, скорее всего они подключены хаотично. Мы любим порядок, информации, что появится ещё одна организация, у нас нет, поэтому отталкиваемся от того, что их 2. Портов в коммутаторе 24, на гигабитные не смотрим:
один задействован на транк, второй держим в резерве, если 1й выйдет из строя, поэтому для 1й организации возьмём порты с 1го по 12, для 2й с 12 по 24. Удаляем существующие связи, подключаем согласно новой концепции.

3. Разделяем коммутатор на 2 Vlan'а:

```
Switch>en
Switch#conf t
Switch(config)#interface range FastEthernet 0/1 -12
Switch(config-if-range)#switchport mode access 
Switch(config-if-range)#switchport access vlan 100
Switch(config-if-range)#ex
Switch(config)#interface range FastEthernet 0/13 -24
Switch(config-if-range)#switchport mode access 
Switch(config-if-range)#switchport access vlan 200
Switch(config-if-range)#ex
Switch#wr

```

![p5 2](https://github.com/lexche/Testyp/assets/95694325/ae203e5f-bda3-4a1a-97b1-185a1cbc9706)

После этого пингуем шлюзы по умолчанию, они доступны. Едем дальше.

### Задание 2.

1. Изолируем подсети 192.168.10.0/24 и 192.168.20.0/24. Для этого на маршрутизаторе R1 выполним следующие команды:

```
Router(config)#access-list 110 deny ip 192.168.10.0 0.0.0.255 192.168.20.0 0.0.0.255
Router(config)#access-list 110 permit ip any any
Router(config)#access-list 120 deny ip 192.168.20.0 0.0.0.255 192.168.10.0 0.0.0.255
Router(config)#access-list 120 permit ip any any
Router(config)#int
Router(config)#interface F
Router(config)#interface FastEthernet 1/0.10
Router(config-subif)#ip access-group 110 in
Router(config-subif)#ip access-group 120 out
Router(config-subif)#ex
Router(config)#interface FastEthernet 1/0.20
Router(config-subif)#ip access-group 120 in
Router(config-subif)#ip access-group 110 out
Router(config-subif)#ex
Router(config)#ex
Router#wr

```

В первом уроке есть подсказка с пояснением как это делать, нужно только поменять подсети и номера ACL'ов.

2. Настраиваем интерфейсы FastEthernet0/0 на маршрутизаторах R0 и R1:

На R0 вводим:

```

Router>en
Router#conf t
Router(config)#interface FastEthernet0/0
Router(config-if)#ip address 10.10.10.1 255.255.255.252
Router(config-if)#ex
Router(config)#ex
Router#wr

```

На R1 вводим:

```

Router>en
Router#conf t
Router(config)#interface FastEthernet0/0
Router(config-if)#ip address 10.10.10.2 255.255.255.252
Router(config-if)#ex
Router(config)#ex
Router#wr

```

3. Настроим маршрутизацию.


```

На R0 вводим:

Router#conf t
Router(config)#ip route 192.168.10.0 255.255.255.0 10.10.10.2
Router(config)#ip route 192.168.20.0 255.255.255.0 10.10.10.2

На R1 вводим:

Router#conf t
Router(config)#ip route 172.16.10.0 255.255.255.0 10.10.10.1
Router(config)#ip route 172.16.20.0 255.255.255.0 10.10.10.1

```
После этого подсети двух площадок видят друг друга, но не соседей по площадке. 

4. Донастройка ACL'ов для достижения 100% кошерности.


R0:

```

Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#access-list 111 deny ip 172.16.10.0 0.0.0.255 192.168.20.0 0.0.0.255
Router(config)#access-list 111 permit ip any any
Router(config)#access-list 112 deny ip 192.168.20.0 0.0.0.255 172.16.10.0 0.0.0.255
Router(config)#access-list 112 permit ip any any
Router(config)#access-list 121 deny ip 172.16.20.0 0.0.0.255 192.168.10.0 0.0.0.255
Router(config)#access-list 121 permit ip any any
Router(config)#access-list 122 deny ip 192.168.10.0 0.0.0.255 172.16.20.0 0.0.0.255
Router(config)#access-list 122 permit ip any any
Router(config)#interface FastEthernet 1/0.100
Router(config-subif)#ip access-group 111 in
Router(config-subif)#ip access-group 112 out
Router(config-subif)#ex
Router(config)#interface FastEthernet 1/0.200
Router(config-subif)#ip access-group 121 in
Router(config-subif)#ip access-group 122 out
Router(config-subif)#ex

```

R1:

```

Router#conf t
Router(config)#access-list 111 deny ip 192.168.10.0 0.0.0.255 172.16.20.0 0.0.0.255
Router(config)#access-list 111 permit ip any any
Router(config)#access-list 121 deny ip 192.168.20.0 0.0.0.255 172.16.10.0 0.0.0.255
Router(config)#access-list 121 permit ip any any
Router(config)#access-list 112 deny ip 172.16.20.0 0.0.0.255 192.168.10.0 0.0.0.255
Router(config)#access-list 112 permit ip any any
Router(config)#access-list 122 deny ip 172.16.10.0 0.0.0.255 192.168.20.0 0.0.0.255
Router(config)#access-list 122 permit ip any any
Router(config)#interface FastEthernet 1/0.10
Router(config-subif)#ip access-group 111 in
Router(config-subif)#ip access-group 112 out
Router(config-subif)#ex
Router(config)#interface FastEthernet 1/0.20
Router(config-subif)#ip access-group 121 in
Router(config-subif)#ip access-group 122 out
Router(config-subif)#ex

```


Готово. Что надо видно, что не надо не видно. 


### Задание 3.


Начнём со второй площадки, так как интерфейс у нас там настроен и "подключен" к "интернету".

Для подсети 192.168.10.0/24:

```
Router#conf t
Router(config)#interface FastEthernet1/0.10
Router(config-subif)#ip nat inside 
Router(config-subif)#ex
Router(config)#interface FastEthernet0/1
Router(config-if)#ip nat outside
Router(config-if)#ex
Router(config)#ip nat inside source list 1 interface FastEthernet0/1 overload
Router(config)#access-list 1 permit 192.168.10.0 0.0.0.255

```


Для подсети 192.168.20.0/24:

```
Router#conf t
Router(config)#interface FastEthernet1/0.20
Router(config-subif)#ip nat inside 
Router(config-subif)#ex
Router(config)#interface FastEthernet0/1
Router(config-if)#ip nat outside
Router(config-if)#ex
Router(config)#ip nat inside source list 2 interface FastEthernet0/1 overload
Router(config)#access-list 2 permit 192.168.20.0 0.0.0.255

```

Объясним только одну последовательность команд, так как они практически идентичны:

1. Router#conf t: Это команда перехода в режим конфигурации.

2. Router(config)#interface FastEthernet1/0.20: Эта команда переводит нас в режим настройки подинтерфейса FastEthernet1/0.20. Мы настраиваем подинтерфейс с идентификатором VLAN 20 для NAT внутренней части сети.

3. Router(config-subif)#ip nat inside: Эта команда указывает, что данный интерфейс является внутренним для NAT. Подинтерфейс FastEthernet1/0.20 помечается как внутренний для NAT, что означает, что IP-адреса в этой сети будут транслироваться.

4. Router(config-subif)#ex: Выходим из режима настройки подинтерфейса.

5. Router(config)#interface FastEthernet0/1: Переход к настройке физического интерфейса FastEthernet0/1. Мы настраиваем указанный интерфейс как внешний для NAT, к которому подключены устройства вне внутренней сети.

6. Router(config-if)#ip nat outside: Указываем, что данный интерфейс является внешним для NAT. Интерфейс FastEthernet0/1 помечается как внешний для NAT, указывая, что IP-трафик, проходящий через этот интерфейс, должен быть переведен.

7. Router(config-if)#ex: Выходим из режима настройки интерфейса FastEthernet0/1.

8. Router(config)#ip nat inside source list 2 interface FastEthernet0/1 overload: Конфигурируем источник NAT с использованием списка ACL и перегрузкой исходных IP-адресов. Указывается, что IP-адреса из списка ACL 2 должны быть переведены при прохождении через интерфейс FastEthernet0/1 с использованием NAT overload.

9. Router(config)#access-list 2 permit 192.168.20.0 0.0.0.255: Создаем ACL для разрешения трансляции адресов. В ACL с номером 2 разрешено транслировать IP-адреса из диапазона 192.168.20.0/24. Эти адреса будут подвергаться NAT при выходе на интерфейс FastEthernet0/1.
   
Далее подключаем свободный интерфейс маршрутизатора R0 к глобальной паутине (сетевому хабу). Назначаем на интерфейсе ip-адрес210.0.11.20 255.255.255.0, и проделываем тоже самое, только меняем подсети:

Для подсети 192.168.10.0/24:

```
Router#conf t
Router(config)#interface FastEthernet1/0.10
Router(config-subif)#ip nat inside 
Router(config-subif)#ex
Router(config)#interface FastEthernet0/1
Router(config-if)#ip nat outside
Router(config-if)#ex
Router(config)#ip nat inside source list 1 interface FastEthernet0/1 overload
Router(config)#access-list 1 permit 172.16.10.0 0.0.0.255

```


Для подсети 192.168.20.0/24:

```
Router#conf t
Router(config)#interface FastEthernet1/0.20
Router(config-subif)#ip nat inside 
Router(config-subif)#ex
Router(config)#interface FastEthernet0/1
Router(config-if)#ip nat outside
Router(config-if)#ex
Router(config)#ip nat inside source list 2 interface FastEthernet0/1 overload
Router(config)#access-list 2 permit 172.16.20.0 0.0.0.255

```

Немного ждём, с первого раза может пинг не пройти, но со второго раза должны увидеть:

```

C:\>ping 210.0.11.50

Pinging 210.0.11.50 with 32 bytes of data:

Reply from 210.0.11.50: bytes=32 time<1ms TTL=127
Reply from 210.0.11.50: bytes=32 time<1ms TTL=127
Reply from 210.0.11.50: bytes=32 time<1ms TTL=127
Reply from 210.0.11.50: bytes=32 time<1ms TTL=127

Ping statistics for 210.0.11.50:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

```
