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


