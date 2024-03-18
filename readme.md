### Урок 3. Настроить коммутацию.

В этом уроке речь пойдёт про коммутацию, а точнее про коммутаторы, а ещё точнее про настройку коммутаторов в локальной сети компании.

Но прежде чем начать практиковаться в 

Коммутатор (англ. switch) — это устройство компьютерной сети, используемое для соединения устройств в локальной сети (LAN) и обеспечения коммуникации между ними.
Коммутатор работает на канальном и физических уровнях сетевой модели OSI и способен принимать, анализировать и пересылать данные к целевому устройству в сети.

Коммутаторы помогают решать такие задачи, как: 

1. Управление трафиком. Коммутаторы управляют потоком данных в локальной сети (LAN), обеспечивая передачу информации только тем устройствам, для которых данные предназначены. Это позволяет избежать перегрузок сети и обеспечить эффективное использование ресурсов.

2. Формирование сети. Коммутаторы помогают формировать сеть путем соединения различных устройств, таких как компьютеры, принтеры, серверы, IP-телефоны и другие сетевые устройства. Они обеспечивают взаимодействие между устройствами внутри сети.

3. Предоставление безопасности. Коммутаторы могут создавать виртуальные сегменты сети (VLAN), разделяя сеть на отдельные группы для повышения безопасности. Они также могут применять функции безопасности, такие как контроль доступа к сети (NAC) и обнаружение вторжений (IDS), для защиты сети от угроз.

4. Обеспечение скорости и пропускной способности. Коммутаторы позволяют передавать данные с высокой скоростью в сети, что обеспечивает быстрый обмен информацией между устройствами. Они поддерживают различные стандарты передачи данных, такие как Fast Ethernet, Gigabit Ethernet и 10 Gigabit Ethernet.


Перечислим основные типы коммутаторов:

1. Неуправляемый коммутатор (Unmanaged Switch): Простой в использовании, не имеет функций настройки. Подходит для небольших сетей, где нет потребности в расширенных возможностях управления. Пример: TP-Link TL-SG108.

2. Управляемый коммутатор (Managed Switch):Позволяет администратору управлять и настраивать сеть, обладает расширенными функциями, такими как VLAN, QoS, безопасность и др. Пример: Cisco Catalyst 2960.

3. Коммутатор 2 уровня OSI (Layer 2 Switch): Работает на канальном уровне OSI, коммутирует пакеты на основе MAC-адресов. Обеспечивает быструю передачу данных внутри локальной сети. Пример: NETGEAR GS308.

4. Коммутатор 3 уровня OSI (Layer 3 Switch): Обладает функциями маршрутизации, способен работать на сетевом уровне OSI. Позволяет маршрутизировать пакеты между сегментами сети. Пример: Cisco SG350.

5. Коммутатор с поддержкой PoE (PoE Switch): Поддерживает технологию Power over Ethernet, позволяя передавать электропитание по сетевому кабелю Ethernet. Используется для питания устройств, таких как IP-камеры, телефоны и другие. Пример: D-Link DGS-1100.

6. Стекируемые коммутаторы (Switch Stack): Несколько коммутаторов объединяются в стек, что позволяет управлять ими как единым устройством. Упрощает управление сетью и повышает отказоустойчивость. Пример: HP Aruba 2930M.

7. Коммутатор с агрегацией линков (Link Aggregation Switch): Поддерживает агрегацию линков, объединяя несколько портов для увеличения пропускной способности и создания избыточных соединений. Пример: NETGEAR GS116LP.

8. Гигабитный коммутатор (Gigabit Switch): Обеспечивает передачу данных на скорости 1 Гбит/с на каждом порту, что делает его идеальным для быстрой передачи данных в малых и средних сетях. Пример: NETGEAR GS308P.

9. 10-гигабитный коммутатор (10-Gigabit Switch): Предоставляет более высокую пропускную способность до 10 Гбит/с на порт, что особенно полезно для средних и крупных предприятий с высокими требованиями к скорости передачи данных. Пример: Cisco SG350X.
  
10. С модульным дизайном (Modular Switch): Модульные коммутаторы позволяют гибко расширять сеть, добавляя новые модули для увеличения количества портов, поддержки новых технологий или других возможностей в зависимости от потребностей сети.Пример:  Juniper Networks EX9200.

11. Оптоволоконный коммутатор (Fiber Optic Switch): Используется для подключения устройств по оптоволоконным кабелям для передачи данных на большие расстояния с высокой скоростью и надежностью. Они особенно полезны при построении сетей с высокими требованиями к скорости и пропускной способности. Пример:  Cisco Catalyst 9300L.

С типами разобоались, давайте заглянем внутрь.

Мы уже упоминали ASIC-микросхемы в коммутаторах в одной из первых тем, самое время погрузиться в них более детально.

ASIC-микросхема — это специализированная интегральная микросхема, разработанная для конкретного приложения или задачи. В контексте сетевых устройств, таких как коммутаторы, 
ASIC-микросхема используется для выполнения специфических функций, связанных с обработкой и коммутацией сетевых данных на высокой скорости.

![5 2 3 1](https://github.com/lexche/Testyp/assets/95694325/b2bf7252-e01b-4594-9b9c-34733d333a54)

Вот несколько ключевых особенностей и назначений ASIC-чипов:

1. Специализация: ASIC-микросхема проектируется для конкретного функционала или приложения.
В сетевых устройствах, ASIC-микросхемы могут быть специально разработаны для обработки сетевых данных, коммутации пакетов и обеспечения высокой производительности передачи.

2. Высокая производительность: Благодаря специализированной архитектуре и оптимизации под конкретные задачи, ASIC-микросхемы обеспечивают быструю и эффективную обработку данных,
что особенно важно для современных сетей с высокими скоростями передачи.

3. Энергоэффективность: ASIC-микросхемы могут быть оптимизированы для энергоэффективной работы, что актуально для сетевых устройств, где важны не только высокая производительность,
но и экономия энергии.

4. Поддержка специфических протоколов: ASIC-микросхемы могут быть разработаны с учетом требований сетевых протоколов, обеспечивая выполнение конкретных сетевых функций и коммутацию
на определенных уровнях сетевой модели OSI.

5. Интеграция с другими компонентами: ASIC-микросхемы могут интегрироваться с другими компонентами сетевого оборудования, такими как процессоры, память и интерфейсы,
 для создания комплексных сетевых решений.

Кроме ASIC, важную роль в коммутаторах занимает такой вид памяти как CAM(Content-Addressable Memory) - это специальный вид памяти в коммутаторах, используемый для быстрого поиска MAC-адресов устройств в локальной сети. 

Давайте рассмотрим основные особенности CAM:

1. Цель CAM в коммутаторах: CAM используется для хранения содержащихся данных, вроде MAC-адресов устройств и соответствующих им портов коммутатора. CAM в коммутаторах помогает определять, на какой порт нужно отправить сетевой пакет на основе его MAC-адреса.

2. Быстрый доступ к данным: Основное преимущество CAM заключается в возможности быстро и эффективно находить данные. Когда коммутатор получает сетевой кадр, CAM позволяет ему моментально определить, куда отправить пакет, обращаясь к содержащимся данным без необходимости последовательного поиска.

3. Оптимизация коммутации: CAM таблицы в коммутаторах способствуют оптимизации процесса коммутации данных в локальной сети. Благодаря возможности быстрого нахождения соответствия между MAC-адресами устройств и их портами, коммутаторы могут эффективно управлять трафиком и обеспечить быструю передачу данных.

4. Динамическое обновление: CAM таблицы обновляются динамически при изменении конфигурации сети: когда новое устройство посылает пакет, его MAC-адрес и порт добавляются в CAM таблицу. Это позволяет коммутатору постоянно обновлять информацию о расположении устройств в сети.

5. Решение проблем с коллизиями MAC-адресов: CAM помогает избежать проблем с коллизиями MAC-адресов, предотвращая отправку пакетов неправильно настроенным устройствам, так как позволяет точно определить местоположение источника и назначения пакетов.

---

Перейдём к практике. Давайте установим симуляторот компании Cisco. Скачайте установочный файл по ссылке:

https://sysadmin.education-services.ru/downloads/Packet_Tracer821_64bit_setup_signed.exe

Запустите скачанный файл:

![5 2 3 2](https://github.com/lexche/Testyp/assets/95694325/f37f4f77-d6af-4fad-8530-b25d4fc34d06)

![5 2 3 3](https://github.com/lexche/Testyp/assets/95694325/918d028b-8f55-40be-9935-67453b9795f3)

Далее пройдите через стандартную процедуру установки : Далее-далее-готово, если у вас нет необходимости установить приложение не в "Program Files": 

![5 2 3 4](https://github.com/lexche/Testyp/assets/95694325/e060cd01-766d-47e1-8ae3-cfcf90fc1c79)

![5 2 3 5](https://github.com/lexche/Testyp/assets/95694325/d483d6cb-4307-4f9d-a116-d23fdb1a37fc)

![5 2 3 6](https://github.com/lexche/Testyp/assets/95694325/c8044030-0e0f-4e6d-80fa-b6e40ad78d63)

![5 2 3 7](https://github.com/lexche/Testyp/assets/95694325/d5a9d0d2-b6ef-4659-9d5d-65fe585c196f)

После установки у вас появится ярлык приложения на "Рабочем столе" или в меню "Пуск":

![5 2 3 8](https://github.com/lexche/Testyp/assets/95694325/481c01d2-e337-448f-8dcc-4bcc843692a0)

Далее, прежде чем запускать пиложение, отключите сеть (проводную и беспроводную) на вашем устройстве, иначе программа попросит авторизоваться, а нам это не нужно.

После того как приложение запустилось, сеть можно обратно подключить.

![5 2 3 9](https://github.com/lexche/Testyp/assets/95694325/2f243865-8756-4205-a8ed-eb5188247dac)

В открывшнмся окне обратите внимание на левый нижний угол. Выбираем Network Devices->Switches. 

![5 2 3 10](https://github.com/lexche/Testyp/assets/95694325/43e22105-392a-4412-831d-831574c8e09a)

Возьмём коммутатор 2960 и перетащите его на основное поле.

![5 2 3 11](https://github.com/lexche/Testyp/assets/95694325/a60c3e41-7f24-45fa-90aa-a71759bb1584)


Кликните на появившийся коммутатор и перейдите во вкладку CLI (Comand Line interface).

![5 2 3 12](https://github.com/lexche/Testyp/assets/95694325/c870ef13-9d75-423f-81c5-1e320295c836)
![5 2 3 13](https://github.com/lexche/Testyp/assets/95694325/571e8f61-6140-4486-8391-e7f13ec38779)

Нажмите Enter, чтобы начать сессию на этом коммутаторе. Сделаем первоначальную настройку: дадим имя этому коммутатору, установим пароли и сообщим об этом в начальном сообщении.

Для начала введите команды enable и configure terminal (можно сократить до conf t), чтобы перейти в режим конфигурирования коммутатора, после этого вводим команду: hostname "новое имя коммутатора"(возьмём yp_switch_01), после этого вводим exit, 
чтобы выйти из режима конфигурирования. Вводим команду write memory (или write, или wr), эта команда сохраняет в энергонезависимой памяти все изменения, сделанные в конфигурации, так же можно использовать команду: copy running-config startup-config, иначе после перезагрузки сделанные настройки не сохраняться.

![5 2 3 14](https://github.com/lexche/Testyp/assets/95694325/25ab4011-979c-4dab-9baf-170533df8872)

Отлично. Имя есть, теперь сделаем пароль для того, чтобы начинать работу с коммутатором и переходить в режим конфигурирования.

Запаролим вход в коммутатор:

```

yp_switch_01>enable
yp_switch_01#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
yp_switch_01(config)#line con 0
yp_switch_01(config-line)#password superpassword3000!
yp_switch_01(config-line)#login
yp_switch_01(config-line)#exit
yp_switch_01(config)#exit
yp_switch_01#wr
Building configuration...
[OK]
yp_switch_01#

```
При следующей попытке поддключения коммутатор запросит пароль. Теперь установим пароль на вход в режим конфигурации:

```

yp_switch_01>enable
yp_switch_01#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
yp_switch_01(config)#enable secret superpassword3001!
yp_switch_01(config)#exit
yp_switch_01#
%SYS-5-CONFIG_I: Configured from console by console

yp_switch_01#wr
Building configuration...
[OK]
yp_switch_01#exit

```

Ну вот, теперь кто попало лазить не будет, давайте сделаем "приветственное" сообщение:

```

yp_switch_01>enable
yp_switch_01#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
yp_switch_01(config)#banner motd $
Enter TEXT message.  End with the character '$'.
You need super password!!!


$

yp_switch_01(config)#exit
yp_switch_01#
%SYS-5-CONFIG_I: Configured from console by console

yp_switch_01#wr
Building configuration...
[OK]
yp_switch_01#exit

```

При следующем входе видим:

![5 2 3 15](https://github.com/lexche/Testyp/assets/95694325/8f43343e-b905-49a0-9946-6bda32c63b1a)

С первоначальной настройкой мы закончили.

#### Квиз.

Вопрос:
Какая функция лучше всего характеризует ASIC в коммутаторах?

A) Маршрутизация пакетов в сети
B) Хранение информации о VLAN
C) Ускоренная обработка сетевых данных
D) Фильтрация сетевого трафика

Правильный ответ: C) Ускоренная обработка сетевых данных  
Объяснение: ASIC в коммутаторах отличается высокой производительностью и специализированной обработкой данных для быстрой коммутации.

Вопрос:
Какую информацию хранит CAM таблица в коммутаторе?

A) IP-адреса устройств в сети
B) Телефонные номера подключенных устройств
C) MAC-адреса и соответствующие порты подключения
D) Содержимое передаваемых пакетов данных

Правильный ответ: C) MAC-адреса и соответствующие порты подключения  
Объяснение: CAM таблица хранит соответствие между MAC-адресами устройств и портами коммутатора для эффективной коммутации пакетов.

Вопрос:
Какую роль играет ASIC в работе коммутатора?

A) Определение IP-адресов устройств в сети\
B) Ускоренная обработка сетевых пакетов\
C) Хранение информации о VLAN в сети\
D) Распределение широковещательных пакетов

Правильный ответ: B) Ускоренная обработка сетевых пакетов  
Объяснение: ASIC в коммутаторе способствует быстрой и эффективной обработке и коммутации сетевых пакетов для повышения производительности.

Вопрос:
Какую роль играют CAM таблицы в коммутаторах?

A) Маршрутизация сетевых пакетов
B) Хранение информации о сегментах VLAN
C) Определение принадлежности IP-адресов устройств
D) Ассоциация MAC-адресов с портами коммутатора

Правильный ответ: D) Ассоциация MAC-адресов с портами коммутатора  
Объяснение: CAM таблицы используются для хранения MAC-адресов и соответствующих портов для эффективной коммутации сетевых пакетов.

Вопрос:
Что представляет собой ASIC в контексте коммутаторов?

A) Интегральная микросхема общего назначения\
B) Специализированная интегральная микросхема для определенных задач\
C) Программируемый контроллер для сетевой безопасности\
D) Программно-аппаратный комплекс для телефонных систем

Правильный ответ: B) Специализированная интегральная микросхема для определенных задач  
Объяснение: ASIC в коммутаторах представляет собой специализированную микросхему, разработанную для конкретных сетевых функций.

---

В 1м уроке мы использовали аббревиатуру VLAN, давайте её рассшифруем и узнаем почему VLAN так важен в коммутации.

VLAN (Virtual Local Area Network) - это технология локальных сетей, которая позволяет создавать виртуальные сегменты в пределах одной физической сети. Каждый VLAN представляет собой логическую группу устройств, которая может обмениваться данными как отдельная сеть, хотя физически они могут быть подключены к одному коммутатору или маршрутизатору.

Давайте зайдём через аналогию, чтобы стало яснее. Представьте, что коммутатор - это многоквартирный дом, где  все квартиры подключены к общей инфраструктуре (вода, газ, электричество) - это и есть физическая сеть.

Каждый этаж дома принадлежит разным структурам ( VLAN), где живут разные группы людей.

Каждая квартира на своем этаже (VLAN) изолирована от других. Жильцы могут чувствовать себя более безопасно и спокойно, так как доступ к их квартире ограничен. 

Администратор дома (администратор сети) может управлять распределением квартир по этажам, разрешать или запрещать доступ в определенные квартиры (VLAN).

Разделение дома на квартиры позволяет эффективнее использовать ресурсы. Например, если на одном этаже (VLAN) сломается водопровод, другие этажи останутся незатронутыми.

Внутри "дома" всё звучит логично, но какие преимущества даёт VLAN в коммутации и нужен(нужна) ли он(а)? Нужен(нужна), потому что решает следующиезадачи:

1. Изоляция трафика: VLAN позволяют разделять сеть на логические группы, что помогает изолировать трафик между этими группами. Например, можно создать отдельные VLAN для разных отделов компании, чтобы обеспечить безопасность и конфиденциальность данных.

2. Управление трафиком: VLAN помогают управлять потоком данных, определяя, какие устройства могут общаться друг с другом. Это позволяет оптимизировать сетевой трафик и улучшить производительность сети.

3. Повышение безопасности: С помощью VLAN можно создавать сегментированные сети, что ограничивает доступ к определенным участкам сети. Это снижает риск несанкционированного доступа к данным.

От теории перейдём к практике, настроим в коммутаторе несколько виртуальных частных сетей. Создадим VLAN на нашем виртуальном коммутаторе:

```
yp_switch_01>en
Password: 
yp_switch_01#	
yp_switch_01#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
yp_switch_01(config)#vlan 10
yp_switch_01(config-vlan)#name First_VLAN
yp_switch_01(config-vlan)#exit
yp_switch_01(config)#exit
yp_switch_01#
%SYS-5-CONFIG_I: Configured from console by console
yp_switch_01#wr
Building configuration...
[OK]

```
Объясним каждую строчку:

1. **yp_switch_01#conf t**:
   - Эта команда переключает коммутатор в режим глобальной конфигурации. Пользователь видит приставку yp_switch_01#, что обозначает имя устройства и указывает, что коммутатор готов к вводу команд настройки.

2. **yp_switch_01(config)#vlan 10**:
   - Здесь мы создаем новый VLAN с идентификатором 10. После ввода этой команды коммутатор переходит в режим настройки VLAN с номером 10.

3. **yp_switch_01(config-vlan)#name First_VLAN**:
   - В этой строке мы называем созданный VLAN как "First_VLAN". Команда name используется для присвоения понятного имени VLAN, которое облегчает идентификацию и управление VLAN.

4. **yp_switch_01(config-vlan)#exit**:
   - Команда exit используется для выхода из режима конфигурации VLAN. После этой команды коммутатор переключается обратно в глобальный режим конфигурации.

5. **yp_switch_01(config)#exit**:
   - Эта команда также используется для выхода из текущего режима конфигурации. После этой команды коммутатор переключается в режим просмотра конфигурации.

6. **yp_switch_01#wr**:
   - Команда wr (или write) сохраняет текущую конфигурацию в постоянной памяти коммутатора. Это важно, чтобы сохранить внесенные изменения и избежать их потери при перезагрузке коммутатора.

А теперь добавим первые пять портов к созданному vlan 10:

```
yp_switch_01#conf t
yp_switch_01(config)#interface  range  fastEthernet 0/1 - 5
yp_switch_01(config-if-range)#switchport mode access 
yp_switch_01(config-if-range)#switchport access vlan 10
yp_switch_01(config-if-range)#end
yp_switch_01#
yp_switch_01#wr
Building configuration...
[OK]
yp_switch_01#

```
Объясним каждую строчку:

1. **yp_switch_01#conf t**:
   - Эта команда вводится для перехода в режим глобальной конфигурации (configure terminal), где вы можете вносить изменения в настройки коммутатора.

2. **yp_switch_01(config)#interface range fastEthernet 0/1 - 5**:
   - Здесь мы выбираем диапазон портов FastEthernet с 1 по 5 для конфигурации. Используется ключевое слово range, чтобы указать диапазон портов.

3. **yp_switch_01(config-if-range)#switchport mode access**:
   - Данная строка устанавливает режим порта в режим доступа (access mode), что означает, что порт принадлежит только одному VLAN.

4. **yp_switch_01(config-if-range)#switchport access vlan 10**:
   - Эта команда привязывает выбранные порты (FastEthernet 0/1-5) к VLAN 10 в режиме доступа. Происходит присвоение портам определенного VLAN.

5. **yp_switch_01(config-if-range)#end**:
   - Команда end используется для завершения конфигурации диапазона портов и перехода в общий режим конфигурации.

6. **yp_switch_01#wr**:
   - Эта команда сохраняет текущую конфигурацию в постоянной памяти коммутатора. Она гарантирует, что все внесенные изменения будут сохранены даже после перезагрузки устройства.


#### Практическое задание.

Отработайте в тренажёре то, что мы сейчас разобрали.



