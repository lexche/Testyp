### Урок 1. Постановка задачи

В этой теме речь пойдёт о проектировании сети. В этом уроке рассмотрим общие аспекты, на которые стоит обратить внимание при планировании построения локальной сети компании.

Сразу обращу внимания, что при планировании сети нет "готовых" решений, так как сеть для каждой компании уникальна, эта уникальность зависит от: локации, архитектурных особенностей здания (зданий), бюджета, статуса организации (например, требования ГОСТов к локальной сети в офисных и складских помещениях будут отличаться). 
В этом уроке мы рассмотрим усреднённый пример, чтобы охватить основные моменты, на которые стоит обратить внимание.

![5 2 1 1](https://github.com/lexche/Testyp/assets/95694325/39ea3141-59f5-43a4-98d1-2a35645e0140)

Представим, что в нашей компании есть главный офис - семиэтажное здание с цокольным и чердачным этажами длина и ширина здания: 40х50 метров; филиал, который находится в другом городе - крыло верхнего этажа в офисном здании 30х40 метров; склад филиала, находится в двух километрах от офиса в промышленной зоне, но в прямой видимости - складское помещение с отапливаемой офисной частью 20х10 и складом 150х170 метров. 

Наша задача - создать единую сеть на всех трёх площадках. 

Давайте дадим контекста, так будет легче: представим, что компания, для которой мы будем проектировать сеть, не висит в воздухе, а вполне себе функционирует, купили\арендовали себе новые здания, и готовятся туда въехать,
поэтому мы не рассматриваем серверное оборудование, оно уже есть, когда всё будет готово, его переместят в новую локацию. 

Наша задача спроектировать сеть в которую входит внутренняя инфраструктура фирмы: рабочие места, периферия, IP-телефония, IP-видеонаблюдение (да такое ~~иногда~~ чаще всего случается), СКУД (система контроля и управление доступом aka пропускная система)и пр. Последние 2 системы как будто не относятся к системному администрированию, но мы сделаем допущение, что сеть под эти системы поручили нам. В этой локации проблем с провайдерами нет. В здание заходит оптика от двух провайдеров. С электричеством тоже всё окэй.

С чего бы вы начали?

Всё верно с изучения чертежей здания и посещения объекта. Пример чертежа:

![5 2 2 2](https://github.com/lexche/Testyp/assets/95694325/df739bce-e097-4600-99b4-53cda19f4f14)

После знакомства с объектом вы начали согласовывать расположение серверной\комутационного узла.

Как по вашему мнениию где лучше расположить серверную и почему? Речь идёт о расположении внутри здания, на ГОСТы для телекоммуникационных помещений внимание, в этом вопросе, не обращаем, но они есть, знать полезно, в этом уроке мы говорим о построении сети. Шутки за 300 отставить:

![5 2 2 3](https://github.com/lexche/Testyp/assets/95694325/9edc6335-4c38-4ac3-926b-b19533e63acf)

Если рассматривать этот вопрос со стороны коммутации, то это центр здания, хотя бы потому что кабельные шахты будут равномерны загружены и мы сможем обойтись меньшим количеством дополнительных коммутационных шкафов. В нашем случае мы поставим дополнительные шкафы на техническом этаже и цоколе, для того чтобы в случае необходимости использовать технологию PoE для различных сетевых устройств: IP-видеокамеры, Wi-Fi точки доступа, IP-телефоны.  

Power over Ethernet (PoE) представляет собой стандартную технологию, которая позволяет передавать электрическое питание и данные по одному кабелю Ethernet. Это удобно и позволяет устройствам, подключенным к сети Ethernet, получать питание напрямую через сетевой кабель, обеспечивая более гибкую и простую установку. 

В нашем случае эта технология полезна тем, что избавляет нас от необходимости в электрических розетках в труднодоступных местах, например, для Wi-Fi точки доступа на потолке. При использовании технологии PoE необходимо внимательно подбирать оборудование, так как стандарт PoE имеет различные версии, такие как IEEE 802.3af, 802.3at (PoE+), 802.3bt (PoE++), каждая из которых предоставляет разные уровни мощности и поддерживает разные устройства.

Для нашего небольшого здания мы обойдёмся витой парой Cat5e, так как расстояния у нас небольшие, кстати, сможете посчитать примерную длинну максимальной трассы? Пусть трассы у нас прямые, заложите 10 метров от трассы до конечного пользователя и столько же в комутационной комнате.

Итак, давайте считать вместе: : комутационная  в центре семиэтажного здания это вверх или вниз 10 метров, + 25, так как здание 40 на 50, +20 запас с двух сторон, итого около: 55 метров. 

Несколько моментов касательно витой пары: обращайте внимание на маркировку в одном из предыдущих уроков мы об этом говорили, читайте ГОСТы. 

Используйте для каждого типа устройств свой цвет оплётки кабеля, например: рабочие места - серые, камеры - жёлтые или чёрные, если расположены вне здания., Wi-Fi - точки зелёные, и т.д. так их проще идентифицировать.

Маркируйте кабели с двух сторон (на всякий случай уточнил).

С проводами разобрались, перейдём к оборудованию.

Помним, что помимо главного здания у нас ещё склад и филиал, туда мы уже тоже съездили\посчитались и имеем представление, какого оборудования и сколько нам понадобиться на всех объектах.

Старайтесь донести до руководства, что лучше закупать оборудования много и запас 15-20%, таким образом велика вероятность скидки, + обращения от такого покупателя диллеры и поставщики будут обрабатывать в первую очередь.

