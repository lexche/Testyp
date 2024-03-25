## Урок 5. Соединить маршрутизаторы


В этом уроке мы покажем как настраивать сеть , когда наша сеть состоит из нескольких маршрутизаторов и подсетей. Маршрутизаторы должны знать друг о друге и о подсетях, которые находятся за маршрутизаторами, и давать возможность устройствам из разных подстей взаимодействовать друг с другом, если это необходимо.

В предыдущих уроках мы уже затрагивали виды маршрутизации: статическая и динамическая , но перед практикой обновим этим знания.

Статическая маршрутизация - это метод определения маршрутов на сетевом устройстве (маршрутизаторе) вручную, без использования динамических протоколов маршрутизации. Это означает, что администратор самостоятельно настраивает таблицу маршрутизации на устройстве, указывая, куда отправлять пакеты для доставки к заданному назначению.

Преимущества статической маршрутизации:

1. Простота и прозрачность: Статические маршруты легко понимать и настраивать, поскольку администратор точно знает, какие маршруты используются.
   
2. Предсказуемость: Поскольку маршруты устанавливаются вручную, они остаются неизменными, пока администратор не внесет изменения.
   
3. Меньшая нагрузка на процессор маршрутизатора: Поскольку нет необходимости в обмене информацией о маршрутах с другими маршрутизаторами, статическая маршрутизация оказывает меньшую нагрузку на процессор устройства.

Недостатки статической маршрутизации:

1. Несколько маршрутов: В средних и крупных сетях настройка и обновление статических маршрутов может быть сложной задачей, особенно если сеть имеет множество маршрутов и подсетей.
   
2. Отсутствие динамической адаптации: Статические маршруты не могут адаптироваться к изменениям в сети, таким как отказы узлов или изменения в топологии сети.

3. Масштабируемость: В крупных сетях использование статической маршрутизации может быть неэффективным и неудобным из-за необходимости ручного управления.

Статическая маршрутизация все еще широко используется в малых сетях, в виртуальных сетях, а также для конкретных специальных случаев или для настройки базовой доступности до других сетей.


Динамическая маршрутизация - это процесс автоматического обмена информацией о сети между маршрутизаторами с целью определения оптимальных маршрутов для передачи данных. Здесь не нужно вручную настраивать маршруты, так как маршрутизаторы сами обмениваются информацией о сетях, что облегчает процесс управления сетью.

Несколько протоколов динамической маршрутизации:

1. OSPF (Open Shortest Path First):
   OSPF - это протокол маршрутизации, который определяет оптимальные маршруты на основе стоимости связей (bandwidth). OSPF является протоколом класса link-state и используется для средних и крупных сетей. Для настройки OSPF в Cisco IOS используется команда router ospf. 

2. RIP (Routing Information Protocol):
   RIP - один из самых простых протоколов маршрутизации. RIP работает на основе расстояния (hop count) до целевой сети. Хотя он не обладает такой масштабируемостью, как OSPF, RIP легко настраивается и подходит для небольших сетей. 

3. BGP (Border Gateway Protocol):
   BGP - это протокол межсетевой маршрутизации, используемый провайдерами интернет-услуг и крупными корпоративными сетями. BGP принимает решения о пути на основе различных атрибутов, таких как AS-путь. Настройка BGP требует более глубоких знаний и обычно используется для соединения различных автономных систем.


Преимущества:

1. Адаптивность: Маршруты могут быстро реагировать на изменения в сети.
2. Масштабируемость: Эффективно для крупных сетей, где динамический поиск оптимальных маршрутов является важным.
3. Удобство обслуживания: Позволяет управлять большим количеством маршрутов более эффективно.

Недостатки:

1. Нагрузка: Может создавать дополнительную нагрузку на сеть из-за обмена информацией между маршрутизаторами.
2. Конфигурационная сложность: Требует знаний для правильной настройки протоколов маршрутизации.

Статическая маршрутизация предпочтительна в небольших сетях, где управление небольшим числом маршрутов важнее автоматизации и быстрой адаптации. Динамическая маршрутизация лучше подходит для крупных распределенных сетей, где эффективное управление маршрутами и быстрая реакция на изменения необходимы. 

В этом уроке, в его практической, мы будем использовать статическую маршрутизацию.

Давайте соберём тестовый стенд. Откроем Cisco Packer tracer. 

Добавим в рабочую зону 2 маршрутизатора и 2 устройства(например, компьютер и ноутбук):


![5 2 5 1](https://github.com/lexche/Testyp/assets/95694325/65bdd351-78e8-404a-8b14-22dfff54377b)

Соединим маршрутизатора между собой через интерфейсы FastEthernet0/0(далее 0/0), а интерфейсы FastEthernet0/1(далее 0/1) подключим к конечным устройствам.

![5 2 5 2](https://github.com/lexche/Testyp/assets/95694325/34c82d4c-c210-42e5-81f0-3e691059e885)

Красные треугольники показывают, что никто никого не видит. Давайте исправим это.

Начнём с описания того, что проговорим какие подсети будем использовать. У нулевого маршрутизатора интерфейс 0/1 будет иметь адрес 192.168.0.1 255.255.255.0 интерфейс 0/0 10.10.10.1 255.255.255.252 (Вопрос со звёздочкой: какую разрядность имеет подсеть с маской 255.255.255.252 и сколько адресов для хостов будет в этой сети?). У первого маршрутизатора интерфейс 0/1 будет иметь адрес 192.168.1.1 255.255.255.0 интерфейс 0/0 10.10.10.2 255.255.255.252 (Вопрос со звёздочкой: какую разрядность имеет подсеть с маской 255.255.255.252 и сколько адресов для хостов будет в этой сети?). 

Назначим IP-адреса на конечных устройствах: компютере (192.168.0.10) и ноутбуке (192.168.1.10).

Далее перейдём к настройкам маршрутизаторов. Пропишем на интерфейсах адреса, как описано выше.

Попробуем пропинговатьс компьютера (192.168.0.10) роутер 1(192.168.1.1):

```
C:\>ping 192.168.1.1

Pinging 192.168.1.1 with 32 bytes of data:

Reply from 192.168.0.1: Destination host unreachable.
Reply from 192.168.0.1: Destination host unreachable.
Reply from 192.168.0.1: Destination host unreachable.
Reply from 192.168.0.1: Destination host unreachable.

Ping statistics for 192.168.1.1:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss)

```

Результат ожидаем - ответа нет. Давайте пропишем маршруты.

На роутере 0 заходим в терминал и вводим:

```
Router>enable 
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#ip route 192.168.1.0 255.255.255.0 10.10.10.2
Router(config)#exit
Router#
%SYS-5-CONFIG_I: Configured from console by console

Router#wr

```

Аналогично добавляем маршрут на 1м роутере.

После этого мы наблюдаем, что ноутбук и компьютер "видят" друг друга.

![5 2 5 3](https://github.com/lexche/Testyp/assets/95694325/aa3c4e7b-c846-48f9-b454-46fb80af4c28)


### Практическое задание.

Мы умышлено не стали детально описывать часть настроек, так как они были в предыдущих уроках.

Например, мы не упоминули команду no shutdown на роутерах, так как по умолчанию интерфейсы на маршрутизаторах "выключены".

Соберите самостоятельно аналогичный стэнд и сделайте "доступными" друг для друга конечные устройства.

---

