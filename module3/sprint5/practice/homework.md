# Практическая работа

Вот мы и изучили тему "Построение сетей". В ней мы постарались вам дать достаточно практики, но в уроках вам предлагалось повторить в симуляторе за преподавателем с небольшими изменениями. В этой практике мы предложим вам 3 задания, которые вам нужно решить самостоятельно.

Скачайте файл, прикреплённый к этой практике, и откройте его в программе Cisco Packet Tracer. Вы увидите следующую картину:


![p5 1](https://github.com/lexche/Testyp/assets/95694325/2ecf9f1a-2c36-40eb-8e7e-b3826ab3f371)


Давайте не будем пугаться, а в начале разберём экспозицию: практическое задание состоит из 3х частей, каждое задание помечено отдельным цветом и подписано. 


### Задание 1.

В офисе работают 2 организации: организация 1 и организация 2. Обе организации арендуют часть офисного помещения. У организации 1 на компьютерах прописаны адреса из сети 172.16.10.0/24: 172.16.10.10-12. У организации 2 на компьютерах прописаны адреса из сети 172.16.20.0/24: 172.16.10.10-11. И менять адресацию на компьютерах они не хотят. Оборудование на обе организации одно, предоставленное арендодателем, требование обеих организаций: компьютеры не должны видеть друг друга.

Системный алминистратор, который начал настраивать сеть, но не успел довести работу до конца, так как его "перебросили" на другой объект, оставил такую информацию :

Все компьютеры подключены в 1 коммутатор. Какой компьютер в какой порт - неизвестно. Порт коммутатора GigabitEthernet0/1 подключен к порту роутера FastEthernet1\0. 

На роутере были выполнены следующие команды:

```

Router>enable
Router#
Router#configure terminal
Router(config)#int FastEthernet 1/0.100
Router(config-subif)#encapsulation dot1Q 10
Router(config-subif)#ip address 172.16.10.1 255.255.255.0
Router(config-subif)#ex
Router(config)#int FastEthernet 1/0.200
Router(config-subif)#encapsulation dot1Q 20
Router(config-subif)#ip add 172.16.20.1 255.255.255.0
Router(config-subif)#ex
Router(config)#  access-list 101 deny ip 172.16.10.0 0.0.0.255 172.16.20.0 0.0.0.255
Router(config)#access-list 101 permit ip any any
Router(config)#  access-list 102 deny ip 172.16.20.0 0.0.0.255 172.16.10.0 0.0.0.255
Router(config)#access-list 102 permit ip any any
Router(config)#interface FastEthernet 1/0.100
Router(config-subif)#  ip access-group 101 in
Router(config-subif)#  ip access-group 102 out
Router(config-subif)#ex
Router(config)#interface FastEthernet 1/0.200
Router(config-subif)#ip access-group 101 out
Router(config-subif)#ip access-group 102 in
Router(config-subif)#ex
Router(config)#ex
Router#wr
Building configuration...
[OK]

```


