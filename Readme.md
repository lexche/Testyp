### Урок 1. Постановка задачи

В этой теме речь пойдёт о проектировании сети. В этом уроке рассмотрим общие аспекты, на которые стоит обратить внимание при планировании построения локальной сети компании.

Сразу обращу внимания, что при планировании сети нет "готовых" решений, так как сеть для каждой компании уникальна, эта уникальность зависит от: локации, архитектурных особенностей здания (зданий), бюджета, статуса объекта (например, требования ГОСТов к локальной сети в офисных и складских помещениях будут отличаться). 
В этом уроке мы рассмотрим усреднённый пример, чтобы охватить основные моменты, на которые стоит обратить внимание.

![5 2 1 1](https://github.com/lexche/Testyp/assets/95694325/39ea3141-59f5-43a4-98d1-2a35645e0140)

Представим, что в нашей компании есть главный офис - семиэтажное здание с цокольным и чердачным этажами длина и ширина здания: 40х50 метров, высота этажей 3 метра; филиал, который находится в другом городе - крыло верхнего этажа в офисном здании 30х40 метров, высотапотолка 3 метра; склад филиала, находится в двух километрах от филиала в промышленной зоне, но в прямой видимости - складское помещение с отапливаемой офисной частью 20х10 и складом 200х150 метров. 

Наша задача - создать единую сеть на всех трёх площадках. 

Давайте добавим контекста, так будет легче: представим, что компания, для которой мы будем проектировать сеть, не висит в воздухе, а вполне себе функционирует, купили\арендовали себе новые здания, и готовятся туда въехать,
поэтому мы не рассматриваем серверное оборудование, оно уже есть, когда всё будет готово, его переместят в новую локацию. 

Наша задача спроектировать сеть в которую входит внутренняя инфраструктура фирмы: рабочие места, периферия, IP-телефония, IP-видеонаблюдение (да такое ~~иногда~~ чаще всего случается), СКУД (система контроля и управление доступом aka пропускная система)и пр. Последние 2 системы как будто не относятся к системному администрированию, но мы сделаем допущение, что организацию сети под эти системы поручили нам. 

В этой локации проблем с провайдерами нет. В здание заходит оптика от двух провайдеров. С электричеством тоже всё окэй.

С чего бы вы начали?

Всё верно с изучения чертежей здания и посещения объекта. Пример чертежа:

![5 2 2 2](https://github.com/lexche/Testyp/assets/95694325/df739bce-e097-4600-99b4-53cda19f4f14)

После знакомства с объектом вы начали согласовывать расположение серверной\главного комутационного узла.

Как по вашему мнениию где лучше расположить серверную и почему? Речь идёт о расположении внутри здания, на ГОСТы для телекоммуникационных помещений внимание, в этом вопросе, не обращаем, но они есть, знать полезно, в этом уроке мы говорим о построении сети. Шутки за 300 отставить:

![5 2 2 3](https://github.com/lexche/Testyp/assets/95694325/9edc6335-4c38-4ac3-926b-b19533e63acf)

Если рассматривать этот вопрос со стороны коммутации, то это центр здания, хотя бы потому, что кабельные шахты будут равномерно загружены и мы сможем обойтись меньшим количеством дополнительных коммутационных шкафов. В нашем случае мы поставим дополнительные шкафы на техническом этаже и цоколе, для того чтобы в случае необходимости использовать технологию PoE для различных сетевых устройств: IP-видеокамеры, Wi-Fi точки доступа, IP-телефоны.  

Power over Ethernet (PoE) представляет собой стандартную технологию, которая позволяет передавать электрическое питание и данные по одному кабелю Ethernet. Это удобно и позволяет устройствам, подключенным к сети Ethernet, получать питание напрямую через сетевой кабель, обеспечивая более гибкую и простую установку. 

В нашем случае эта технология полезна тем, что избавляет нас от необходимости в электрических розетках в труднодоступных местах, например, для Wi-Fi точки доступа на потолке. При использовании технологии PoE необходимо внимательно подбирать оборудование, так как стандарт PoE имеет различные версии, такие как IEEE 802.3af, 802.3at (PoE+), 802.3bt (PoE++), каждая из которых предоставляет разные уровни мощности и поддерживает разные устройства.

Для нашего небольшого здания мы обойдёмся витой парой Cat5e, так как расстояния у нас небольшие, кстати, сможете посчитать примерную длинну максимальной трассы? Пусть трассы у нас прямые, заложите 10 метров от трассы до конечного пользователя и столько же в комутационной комнате.

Итак, давайте считать вместе: : комутационная  в центре семиэтажного здания это вверх или вниз 10 метров, + 25, так как здание 40 на 50, +20 запас с двух сторон, итого около: 55 метров, витой паре данной категории это по плечу. 

Несколько моментов касательно витой пары: обращайте внимание на маркировку в одном из предыдущих уроков мы об этом говорили, читайте ГОСТы. 

Используйте для каждого типа устройств свой цвет оплётки кабеля, например: рабочие места - серые, камеры - жёлтые или чёрные, если расположены вне здания., Wi-Fi - точки зелёные, и т.д. так их проще идентифицировать.

Маркируйте кабели с двух сторон (на всякий случай уточнил).

Если прокладку кабеля поручили подрядной организации, разбейте данный вид работ на этапы, для каждого этапа пропишите сроки, принимайте работы поэтапно.

С проводами разобрались, перейдём к оборудованию.

Помним, что помимо главного здания у нас ещё склад и филиал, туда мы уже тоже съездили\посчитались и имеем представление, какого оборудования и сколько нам понадобиться на всех объектах. Старайтесь избегать "зоопарка" и использовать, по возможности, одинаковое оборудование на всех площадках.

Старайтесь донести до руководства, что лучше закупать оборудования много и с запасом 15-20%, таким образом велика вероятность скидки, + обращения от такого покупателя диллеры и поставщики будут обрабатывать в первую очередь. 

Для нашей "основной" локальной сети придерживаемся иерархической модели сети  — это подход к дизайну и организации компьютерных сетей, который предусматривает разделение сети на уровни с определенными функциональными обязанностями и характеристиками. Этот подход позволяет упростить управление сетью, улучшить безопасность, повысить производительность и масштабируемость сети. Иерархическая модель сети которая в себя включает:

- ядро сети (Core layer: высокопроизводительные устройства, главное назначение — быстрый транспорт) - высокопроизводительный слой, который обеспечивает быструю передачу данных между различными частями сети

- уровень распространения (Distribution layer: обеспечивает применение политик безопасности, QoS, агрегацию и маршрутизацию в VLAN, определяет широковещательные домены). Этот слой обеспечивает эффективное управление трафиком внутри сети

- уровень доступа (Access-layer: как правило, L2 свичи, назначение: подключение конечных устройств, маркирование трафика для QoS, защита от колец в сети (STP) и широковещательных штормов, опционально обеспечение питания для PoE устройств).  Здесь обычно располагаются L2 коммутаторы, которые обеспечивают подключение конечных устройств к сети.

![5 2 2 5](https://github.com/lexche/Testyp/assets/95694325/1e454fa8-f332-4e67-b48c-2d40d314288e)


Мы запланировали приобрести: коммутаторы нескольких видов: управляемые и неуправляемые, с поддержкой PoE и без, будем считать, что в коммутаторах все порты имеют пропускную способность 1 Гбит/сек, коммутаторы "ядра сети" - 10 Гбит/сек, кроме PoE свитчи под видеонаблюдение - 100мбит/сек, маршрутизаторы с портами 1 Гбит/сек, пара радио мостов, видеорегистраторы. Часть из этого сразу отправится на склад и филиал. 

Для того, чтобы глаза не полезли на лоб, разобъём эту задачу на подзадачи:

1. Разделим 3 сети: локальную, СКУД, видеонаблюдение на физическом уровне. То есть у каждой из этих сетей будет независимый контур со своей адресацией, линиями связи, коммутаторами, взаимодействие между контурами осуществляется с помощью "пограничных" устройств, например, видеорегистраторы, сервер для обслуживания пропускной системы.

2. Раздедим локальную сеть на сегменты: рабочие места, wi-fi точки, ВКС и пр.

3. Распределим место в коммутационной, чтобы каждый сегмент сети был отдельно. Контуры, которые решили вести отдельно, лучше коммутировать в отдельные стойки с замком. Ключи отдать отделу, который будет ответственным за это оборудование, например, служба безопасности, а решением со звёздочкой будет убедить службу безопасности, разместить это оборудование в своих помещениях (например, центральный пульт охраны):

![5 2 2 4](https://github.com/lexche/Testyp/assets/95694325/39f93ffb-fae5-46a5-9912-b19a6b4324e4)

4. Установим в комутационные шкафы, куда "заходит" витая пара, коммутаторы, которые будут относится к уровню доступа, не забывайте маркировать и подписывать всё, что попадается под руку, потом скажете себе "Спасибо". Так же не игнорируйте маркировку устройств, подключённых к розетке, разными цветами патчкордов, колпачков.

5. Далее в центральной стойке установим коммутаторы уровня распространения. Уровень распределения является посредником между уровнями доступа и ядра сети. Он обеспечивает агрегацию трафика от множества уровней доступа перед направлением его в ядро сети.

6. Создание "ядра сети". Ядро сети - это часть компьютерной сети, где происходит передача данных с высокой скоростью между различными узлами (компьютерами, серверами, устройствами) внутри сети. Ядро сети обычно представляет собой высокоскоростной канал связи, который обеспечивает быструю и эффективную передачу данных по сравнению с другими частями сети. Ядро сети один из важнейших элементов локальной сети, поэтому пора задуматься о резервировании оборудовании, например с помощью протокола VRRP. Кроме того ядро сети может выполнять функции маршрутизации и сегментации трафика.

VRRP (Virtual Router Redundancy Protocol) - это протокол, предназначенный для обеспечения отказоустойчивости и избыточности маршрутизаторов в локальной сети. VRRP позволяет объединить несколько маршрутизаторов в виртуальную группу, чтобы обеспечить непрерывную работу сети в случае отказа основного маршрутизатора. Вот некоторые ключевые особенности и принципы работы VRRP:

#### Принцип работы VRRP:

- Виртуальный IP-адрес: В рамках группы VRRP создается виртуальный IP-адрес, который является шлюзом по умолчанию для устройств в локальной сети.

- Мастер и запасной маршрутизаторы: В группе VRRP один из маршрутизаторов выбирается как мастер (master), который обрабатывает трафик для виртуального IP-адреса, в то время как остальные маршрутизаторы находятся в режиме запасного (backup).

- Обнаружение отказа: В случае отказа мастер-маршрутизатора, маршрутизаторы-запасные используют протокол VRRP для выбора нового мастера, который продолжит обработку трафика для виртуального IP-адреса.

- Преимущества:

   - Обеспечение отказоустойчивости и непрерывной работы сети.
   - Уменьшение времени простоя в случае отказа маршрутизатора.
   - Повышение надежности шлюза по умолчанию для устройств в сети.

 
 7. Установка и настройка роутера. В общепринятом понимании роутер — это сетевое устройство, которое принимает пакеты данных из сети, анализирует их адреса и принимает решения о том, к какому узлу или сегменту сети отправить эти пакеты. Роутер используется для маршрутизации данных в компьютерных сетях, обеспечивая передачу информации между различными сегментами или сетями.

  Так же как и ядро сети, роутер может быть зарезервирован с помощью протокола VRRP:

  ![6 2 2 7](https://github.com/lexche/Testyp/assets/95694325/21191e73-8d44-469a-8301-ebe13dae5a32)

  В понимании обывателя роутер помимо своих основных функций:

1. Маршрутизация пакетов:
   - Роутер принимает пакеты данных из сети и передает их по дороге к месту назначения, используя оптимальные маршруты и принимая решения на основе информации в таблице маршрутизации.

2. Обеспечение сегментации сети:
   - Роутер позволяет разделять сеть на логические сегменты для улучшения безопасности и управления трафиком, разделяя сеть на виртуальные локальные сети (VLAN) или подсети.

3. Фильтрация пакетов:
   - Маршрутизаторы могут фильтровать пакеты данных на основе установленных правил и настроек, обеспечивая безопасность и контроль трафика в корпоративной сети.

4. Поддержка протоколов маршрутизации:
   - Роутер выполняет обмен информацией о сети с соседними маршрутизаторами, используя протоколы маршрутизации, такие как OSPF, EIGRP, BGP, для определения оптимального маршрута для пересылки пакетов.

5. Управление трафиком (Traffic Management):
   - Роутер может выполнять функции управления трафиком, включая Quality of Service (QoS) для приоритизации и обеспечения качества обслуживания для определенных типов трафика.

6. Трансляция адресов (NAT):
   - Роутеры могут выполнять функции Network Address Translation (NAT), преобразуя локальные IP-адреса устройств в частных сетях в публичные IP-адреса для внешнего интернета, обеспечивая безопасность и конфиденциальность данных.

Выполняет ещё функции:

1. VPN-шлюз (Virtual Private Network):
   - Развертывание VPN-шлюза, позволяющего сотрудникам подключаться к корпоративной сети из удаленных мест и обеспечивать защищенное соединение через интернет.

2. Фильтрация трафика и безопасность:
   - Роутер обеспечивает фильтрацию пакетов данных в соответствии с определенными правилами безопасности, контролирует доступ и обеспечивает защиту сети от внешних угроз.

3. Балансировка нагрузки:
   - Оптимизация сетевой производительности путем распределения трафика между несколькими линиями передачи данных, что позволяет повысить производительность и отказоустойчивость.

4. Обнаружение сетевых атак:
   - Мониторинг сети и обнаружение потенциальных сетевых атак для обеспечения безопасности и защиты корпоративной сети.

Номинально современный роутер может выполнять этот функционал. В крупных компаниях, которые серъёзно относятся к информационной безопасности и качеству связи, предпочитают не делать "комбайн" на одном устройстве, а разнести функционал по разным устройствам, хотя бы в локации, где сосредоточены главные ресурсы.

Например, связка Маршрутизатор-Фаервол(OgnennayaStena)-VPN-шлюз(концентратор), как показано на рисунке:

![5 2 1 8](https://github.com/lexche/Testyp/assets/95694325/9b0a76c0-9c2a-4181-814a-bcdd700ddcb7)

Подобный подход даёт возможность более гибкой настройки каждого элемента сети: для фаервола - это правила безопасности, для роутера - протоколы маршрутизации и всё о чём мы говорили выше, а VPN-шлюз - методы шифрования удалённых подключений.

Прежде чем использовать тот или иной метод шифрования для VPN туннелей, ознакомьтесь с соответствующей документацией, например, согласно Постановлению Правительства РФ от 16 апреля 2012 г. N 313 использовать  алгоритмы шифрования, которые не сертифицированы по ГОСТ возможно с длинной ключа не более 56 бит, но это зависит от статуса организации и других моментов, поэтому это не обязательно может относится к вашей организации, но знать такие моменты необходимо.

Мы установили нашу связку, Роутер-Брэндмауэр-VPN шлюз, с помощью VRRP зарезервировали роутер и VPN шлюз.

### Практическое задание.

Мы представили руководству план локальной сети в нашем здании: центральный узел в центре здания, вспомогательные ящики на техэтаже и в подвале, в коммутационной отдельные стойки под видеонаблюдение и СКУД, стойки с коммутацией рабочих мест, Wi-Fi точек и прочего нетипичного оборудования. Стойка с коммутаторами уровня распространения, ядром сети, и маршрутизацией. В шкафах наверхи и внизу проведены несколько линков под каждый сегмент сети и установлено по коммутатору. 

При первой "защите" проекта вам удалось убедить руководство в использовании проводов нужного класса, и даже оставить около 10% запасных линий связи, на случай увеличения сотрудников. Про отделение сети видеонаблюдения и СКУД от основной локальной сети получили положительный отклик и, несмотря на возражения службы безопасности, шкафы с их оборудованием из серверной решено было перенести на пульт охраны, чтобы не предоставлять доступ в серверную сторонним сотрудникам для обслужиания этих систем. Но увидев итоговый ценник, попросили удешевить проект. Как бы вы это сделали?

Ответ: 

1. Режем запас, по большому счёту, он для этого и нужен, оставить в резерв по паре штук каждой модели, остальной резерв перекинуть на следующий год. Устройства новые, вероятность выхода из строя невелика, замените на резервные, вышедшее из строя поменяете по гарантии.

2. Устанавливаем дополнительные шкафы сверху, снизу, тянем в них трассы, но оборудование в них пока не покупаем.

3. Этого оказалось недостаточно, тогда отказываемся от PoE свитчей, закупаем обычные и отправляем службу безопасности договариваться с электриком, о том, чтобы он подводил электричество к камерам.

4. И этого мало. Отказываемся от сегментации сети путём физического разделения по типам устройств. То есть сокращаем количество закупаемых свитчей и используем VLAN'ы для 100 % заполняемости портов на коммутаторах.

5. Отказываемся от VRRP для роутера и VPN-шлюза.

6. Объеденяем роутер и VPN шлюз.


Наша сеть сильно поменялась, после того как нам дали возможность оптимизировать бюджет:

Сеть, которую ты планировал             |  Сеть, на которую тебе хватило бюджета
:-------------------------:|:-------------------------:
<img src="https://github.com/lexche/Testyp/assets/95694325/4a0bbe02-e6b1-40a7-aff5-8a012afc6ec8" width="500" height="500"> | <img src="https://github.com/lexche/Testyp/assets/95694325/2f3254dc-5679-4b73-9b54-9453bca7dcbc" width="500" height="500">

Вторая часть урока будет про филиал и склад. Освежим в голове диспозицию: филиал 30х40 метров, высотапотолка 3 метра, находится на 4 этаже. В филиале подключили интернет. Договоры аренды позволяет в филиале\ устанавливать на фасад здания дополнительное оборудование, например кронштейн или радио-мачта. 

В филиале работает около 20-25 человек (22 рабочих места) + 4 МФУ, планируется установить 3 камеры , 1 Wi-Fi точка доступа. Оборудование смонтировано в отдельно стоящем шкафу. 

Склад филиала, находится в двух километрах от филиала в промышленной зоне, но в прямой видимости - складское помещение с отапливаемой офисной частью 20х10 и складом 200х150 метров. На складе не смогли подключить интернет, так как на территории промзоны провайдеров нет и мобильная сеть ловит через раз. Но как и в филиале договор аренды позволяет в филиале\ устанавливать на фасад здания дополнительное оборудование, например кронштейн или радио-мачта. 

![5 2 1 11](https://github.com/lexche/Testyp/assets/95694325/4d3f4a5f-988e-4176-a43b-6b11aa8cb114)

На складе есть металлические стеллажи с товарами, руководство хочет просматривать, что находится между стеллажами и опробовать беспроводные терминалы для сборки заказов(для них необходимо WI-Fi соединение), поэтому наша задача спроектировать локальную сеть для видеонаблюдения и wi-fi сети. На территории склада есть 2 коммутационных ящика, соединённых оптическим кабелем, . 

На складе в офисной части 10 рабочих мест 2 МФУ, планируется установить 14 камер и 10 Wi-Fi точек доступа.

Из офиса после оптимизации бюджета пришло: 1 роутер\брандмауэр, 4 коммутатора с 48 портами со скоростью 1 Гбит\сек на каждом порту, 24 порта из 48 поддерживают технологию PoE необходимого стандарта для камер и точек доступа и 4 оптическими портами, 2 комплекта радио моста - 2 направленнык антены со встроенным програмируемым оборудованием и радио-модулем в каждой, 3 Sfp-модуля для подключения оптического кабеля.

### Практическое задание.

Объясните как обеспечить связью склад и филиала?

У вас есть 3 ящика: 1 в филиале 2 на складе. определите какое оборудование для какого ящика предназначено, чтобы функционировало всё оборудование и появилась связь с центральным офисом. Про настройки мы не говорим, допустим из главного офиса оборудование уже пришло настроенным.


### Ответ.

Филиал

В комутационный ящик устанавливаем роутер, 1 свитч. от свитча, конкретно от порта с PoE, ведём линию связи из здания. В уроке говорилось, что договор аренды допускает установку на фасад здания кронштейна или радио-мачты, устанавливаем на кронштейн одну из антенн, подключаем её с помощью кабеля cat 5e (если укажите, что использовали кабель для уличной прокладки кабеля, то это отдельный плюсик, это было в прошлых уроках).

Склад 

В 1й комутационный шкаф устанавливаем свитч, к нему подключаем оптический кабель в оптический порт, используем Sfp-модуль, так же из этого ящика от PoE порта коммутатора выводим линию связи (cat5e для уличной прокладки кабеля) на улицу к кронштейну, на который устанавливаем вторую антенну, направляем её в сторону филиала. Во 2й комутационный шкаф устанавливаем свитч, к нему подключаем оптический кабель в оптический порт, используем Sfp-модуль.

Оставшееся оборудования убираем в запас, на случай выхода оборудования из строя.


В этом уроке мы рассмотрели на какие аспекты стоит обратить внимание при проектировании сети: нормативные документы, архитектурные особенности, бюджет. Рассмотрели на примере из чего состоит сеть, какое устройсвто за что отвечает. Узнали такие понятия как Иерархическая модель сети и из чего она состоит. Познакомились с протоколом VRRP, узнали для чего он нужен. Смоделировали проектирование и реализацию сети в новом здании компании, рассмотрели с какими трудностями мы можем столкнуться и как их решать, основное  - это дефицит бюджета и модернизация сети. Вы сами попробовали спроектировать и распределить оборудование в отдельной локации в практическом задании.

В следующем уроке детально поговорим про провода и радиоволны.
